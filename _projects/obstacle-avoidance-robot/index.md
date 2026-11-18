---
layout: post
title: "Autonomous Obstacle Avoidance Robot"
description: An autonomous 4WD mobile robot featuring an HC-SR04 ultrasonic rangefinder mounted on an SG90 micro-servo pan scanner, executing spatial environment scanning and differential tank turns via an L298N motor driver.
skills:
  - Arduino
  - C++
  - Ultrasonic Ranging
  - Servo Radar Scanning
  - L298N Motor Driver
  - Differential Steering
  - Autonomous Mobile Robots

main-image: /cover.jpg
order: 10
---

## Overview

An **autonomous mobile robot** engineered to navigate unfamiliar, cluttered indoor environments without physical collisions. The robot combines an **HC-SR04 ultrasonic rangefinder** with a **TowerPro SG90 micro-servo** to form an active $180^\circ$ spatial radar scanner. When an obstacle is detected in its forward trajectory, the robot halts, sweeps both flanks to evaluate spatial clearance, and executes differential tank turns toward the widest open path.

---

## 📸 Hardware Assembly & Physical Showcase

| 4WD Chassis & Underside Motor Mounts | Fully Assembled Robot & Sensor Testing |
| :---: | :---: |
| <img src="{{ '/assets/images/projects/obstacle-avoidance-robot/chassis_assembly_underside.jpg' | relative_url }}" width="420" alt="4WD Chassis Underside Assembly" style="border-radius: 8px; margin: 8px 0;"> | <img src="{{ '/assets/images/projects/obstacle-avoidance-robot/robot_assembled_testing.jpg' | relative_url }}" width="420" alt="Fully Assembled Robot and Ultrasonic Sensor Testing" style="border-radius: 8px; margin: 8px 0;"> |
| *Bottom view showing 4× TT yellow DC gear motors and wheels mounted to the laser-cut acrylic chassis with the SG90 micro-servo ready for pan assembly.* | *Top view of the completed 4WD autonomous robot with Arduino Uno, L298N driver, dual 18650 battery pack, and HC-SR04 ultrasonic rangefinder obstacle detection.* |

---

## 🧠 Radar Decision & Navigation Algorithm

```
                  ┌──────────────────────┐
                  │ Drive Forward (Safe) │
                  └──────────┬───────────┘
                             │
                  ┌──────────▼───────────┐
                  │  HC-SR04 Echo Check  │
                  └──────────┬───────────┘
                             │
                      [Distance < 20cm?]
                         /         \
                    (No)/           \(Yes)
                       /             \
                      ▼               ▼
           ┌──────────────────┐    ┌─────────────────────────┐
           │ Continue Cruise  │    │ 1. Emergency Halt       │
           └──────────────────┘    │ 2. Pan Servo Left (180°)│
                                   │ 3. Pan Servo Right (0°) │
                                   │ 4. Compare Clearances   │
                                   │ 5. Tank Turn Open Side  │
                                   └─────────────────────────┘
```

1. **Forward Cruising**: The robot moves forward while continuously pinging the front sector.
2. **Obstacle Detection**: If an object enters the danger threshold ($< 20\text{ cm}$), the microcontroller halts both motor channels.
3. **Flank Radar Sweeping**: The SG90 servo sweeps the ultrasonic transducer $90^\circ \rightarrow 180^\circ$ (left flank scan) and then $90^\circ \rightarrow 0^\circ$ (right flank scan).
4. **Differential Pivot**: The control algorithm compares the left and right clearance buffers, executing a pivot-turn toward the direction with maximum free space before resuming forward navigation.

---

## Hardware Bill of Materials (BOM)

| Component | Specification | Quantity | Role |
|-----------|---------------|----------|------|
| **Arduino Uno R3** | ATmega328P (16 MHz) | 1 | Master embedded logic controller |
| **HC-SR04** | Ultrasonic transducer (2–400 cm) | 1 | Non-contact spatial distance measurement |
| **SG90 Micro Servo** | 9g servo motor, 180° sweep | 1 | Transducer pan actuation mechanism |
| **L298N Dual H-Bridge** | 2A peak per bridge | 1 | High-current DC gear motor drive |
| **TT DC Gear Motors** | 3V–6V DC, 1:48 reduction | 4 | 4WD chassis propulsion |
| **Smart Car Chassis** | Laser-cut acrylic dual-plate frame | 1 | Mechanical structural frame & wheel mounts |
| **Battery Power** | 2× 18650 Li-ion cells (7.4V nominal) | 1 pack | Logic & motor power supply |

---

## Source Code & Documentation

🔗 [View on GitHub: youniquestar/obstacle-avoidance-robot](https://github.com/youniquestar/obstacle-avoidance-robot)
