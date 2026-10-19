---
layout: post
title: "Autonomous Human-Following Robot"
description: A differential-drive autonomous mobile robot that tracks and follows a human using HC-SR04 ultrasonic distance ranging and dual infrared sensors, with L298N motor driver kinematics for smooth pursuit behaviour.
skills:
  - Arduino
  - C++
  - Ultrasonic Sensing
  - IR Tracking
  - Differential Drive
  - L298N Motor Driver
  - Autonomous Navigation

main-image: /cover.jpg
order: 5
---

## Overview

An **autonomous mobile robot** that identifies and follows a human target using a combination of ultrasonic distance measurement and infrared proximity tracking. The robot maintains a safe follow distance while adapting its speed and steering in real time.

---

## Sensor Fusion Strategy

### Ultrasonic Ranging (HC-SR04)
- Measures distance to the target human (effective range: 2 cm – 400 cm)
- Provides the **follow distance** signal: too far → speed up, too close → slow down / stop

### Dual IR Sensors (Left + Right)
- Detect the lateral position of the human relative to the robot
- Drive **differential steering** decisions: both detect → go straight, left only → turn left, right only → turn right, neither → stop/search

---

## Control Logic

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
              │  (Speed Control)   │
              └─────────┬──────────┘
                        │
              ┌─────────┴──────────┐
              │  L298N Motor Drive │
              │  (PWM to motors)   │
              └────────────────────┘
```

---

## Hardware Bill of Materials

| Component | Purpose |
|-----------|---------|
| Arduino Uno | Main controller |
| HC-SR04 | Distance measurement |
| 2× IR Sensors | Human tracking (left/right) |
| L298N Dual H-Bridge | Motor driver |
| 2× DC Gear Motors | Differential drive |
| 4× Wheels + Chassis | Mobile platform |

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/arduino-human-following-robot)
