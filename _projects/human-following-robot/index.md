---
layout: post
title: "Autonomous Human-Following Robot"
description: A differential-drive autonomous mobile robotic carriage that tracks and follows a human target using HC-SR04 ultrasonic distance ranging and dual infrared optical proximity sensors, with L298N motor driver kinematics for smooth real-time pursuit.
skills:
  - Arduino
  - C++
  - Ultrasonic Sensing
  - IR Tracking
  - Differential Drive
  - L298N Motor Driver
  - Autonomous Navigation
  - Sensor Fusion

main-image: /cover.jpg
order: 5
---

## Overview

An **autonomous mobile robotic carriage** designed and built to identify, track, and follow a human target in real time. The robot fuses sensory inputs from an **HC-SR04 ultrasonic rangefinder** (for dynamic distance monitoring and obstacle safety buffers) and **dual optical infrared (IR) proximity sensors** (for lateral angular tracking), dynamically modulating a 4-wheel differential-drive chassis powered by an **L298N dual H-Bridge motor driver**.

---

## 📸 Hardware Showcase & Working Demonstration

### 🎥 Live Video Demonstration
Watch the physical robotic cart actively tracking, steering, and maintaining follow distance in real-time:

{% include youtube-video.html id="VrDHZcq6VQA" %}

> 📺 **Watch on YouTube:** [Human Following Cart Robot](https://youtu.be/VrDHZcq6VQA?si=S0aPGt2VtVE8ypX7)

<br/>

### 🛠️ Physical Construction & Hardware Gallery

| Front Sensor Tracking Array | Internal Control Electronics & Carriage |
| :---: | :---: |
| <img src="{{ '/assets/images/projects/human-following-robot/front_sensor_array.jpg' | relative_url }}" width="420" alt="Front Sensor Tracking Array" style="border-radius: 8px; margin: 8px 0;"> | <img src="{{ '/assets/images/projects/human-following-robot/internal_electronics_and_carriage.jpg' | relative_url }}" width="420" alt="Internal Electronics and Carriage Lid" style="border-radius: 8px; margin: 8px 0;"> |
| *Front bumper assembly featuring central HC-SR04 ultrasonic sensor flanked by left and right optical IR tracking modules.* | *Interior chassis compartment housing Arduino Uno, L298N motor driver, battery pack, and removable carriage cover.* |

| Left Side Profile | Right Side Profile | Rear Power Interface |
| :---: | :---: | :---: |
| <img src="{{ '/assets/images/projects/human-following-robot/side_profile_left.jpg' | relative_url }}" width="280" alt="Left Side Profile" style="border-radius: 8px; margin: 8px 0;"> | <img src="{{ '/assets/images/projects/human-following-robot/side_profile_right.jpg' | relative_url }}" width="280" alt="Right Side Profile" style="border-radius: 8px; margin: 8px 0;"> | <img src="{{ '/assets/images/projects/human-following-robot/rear_power_switch.jpg' | relative_url }}" width="280" alt="Rear Power Switch" style="border-radius: 8px; margin: 8px 0;"> |
| *Side view showing 4WD wheel clearance and carriage body structure.* | *Side elevation showing TT gear motors and chassis ground clearance.* | *Rear panel integration showing the master rocker power switch.* |

---

## Sensor Fusion Strategy

### Ultrasonic Ranging (HC-SR04)
- Measures forward distance to the target human (effective range: 2 cm – 400 cm)
- Provides the **follow distance** signal:
  - **Distance > Upper Threshold (e.g., 25 cm)**: Target is moving away $\rightarrow$ accelerate forward.
  - **Distance in Safe Zone (15 cm – 25 cm)**: Maintain smooth pursuit.
  - **Distance < Lower Threshold (e.g., 15 cm)**: Target is too close $\rightarrow$ stop immediately to avoid collision.

### Dual Optical IR Sensors (Left + Right)
- Detect lateral angular displacement of the human relative to the robot's heading
- Drive **differential steering** decisions:
  - **Both Sensors Active**: Target is directly ahead $\rightarrow$ drive forward straight.
  - **Left Sensor Active Only**: Target stepped to the left $\rightarrow$ execute differential left turn.
  - **Right Sensor Active Only**: Target stepped to the right $\rightarrow$ execute differential right turn.
  - **Neither Sensor Active**: Target lost $\rightarrow$ enter idle search / hold position.

---

## Control Logic & System Flow

```
                  ┌─────────────┐
                  │  IR Sensors  │
                  │  L     R     │
                  └──┬───────┬──┘
                     │       │
              ┌──────┴───────┴──────┐
              │  Direction Decision │
              │  (Steer L/R/Fwd)   │
              └─────────┬──────────┘
                        │
              ┌─────────┴──────────┐
              │  HC-SR04 Distance  │
              │  (Speed / Safety)  │
              └─────────┬──────────┘
                        │
              ┌─────────┴──────────┐
              │  L298N Motor Drive │
              │  (PWM Kinematics)  │
              └────────────────────┘
```

---

## Hardware Bill of Materials (BOM)

| Component | Specification | Quantity | Purpose |
|-----------|---------------|----------|---------|
| **Arduino Uno R3** | ATmega328P (16 MHz) | 1 | Master logic controller |
| **HC-SR04** | Ultrasonic rangefinder (2–400 cm) | 1 | Distance ranging & safety buffer |
| **IR Proximity Sensors** | LM393 comparator optical modules | 2 | Left / right target tracking |
| **L298N Dual H-Bridge** | 2A continuous per bridge | 1 | DC gear motor driver |
| **TT DC Gear Motors** | 3V–6V DC, 1:48 reduction | 4 | 4WD chassis propulsion |
| **Wheels & Chassis** | Acrylic chassis + rubber tires | 1 | Mobile carriage platform |
| **Battery Pack** | 7.4V / 2S Li-ion battery pack | 1 | High-current power distribution |
| **Master Switch** | Heavy-duty rocker SPST switch | 1 | Primary power isolation |

---

## Source Code & Documentation

🔗 [View on GitHub: youniquestar/human-following-robot](https://github.com/youniquestar/human-following-robot)
