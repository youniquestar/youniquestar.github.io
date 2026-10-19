---
layout: post
title: "ESP32 Wireless Robotics Controller"
description: Ultra-low-latency peer-to-peer ESP-NOW wireless telemetry and motion controller for multi-DOF robotic arms, achieving sub-5ms latency with ESP32 Core v3.0+ callback compliance.
skills:
  - ESP32
  - ESP-NOW Protocol
  - C++
  - FreeRTOS
  - Wireless Telemetry
  - PWM Servo Control
  - Real-Time Systems

main-image: /cover.jpg
order: 4
---

## Overview

A **peer-to-peer wireless control system** for multi-DOF robotic arms using Espressif's ESP-NOW protocol. The system achieves **sub-5ms communication latency** between a handheld joystick controller and a robotic arm receiver — no Wi-Fi router or internet required.

---

## System Architecture

### Transmitter (Controller)
- Dual analog joysticks for multi-axis control
- Tactile push-buttons for gripper and mode switching
- ESP32 running real-time ADC sampling at 100 Hz
- ESP-NOW broadcast with structured telemetry packets

### Receiver (Robot)
- ESP32 receiving motion commands via ESP-NOW callbacks
- PCA9685 16-channel PWM driver for servo orchestration
- Smooth servo interpolation with configurable acceleration curves
- Watchdog timer: auto-safe on signal loss

---

## Key Technical Highlights

| Feature | Specification |
|---------|--------------|
| Protocol | ESP-NOW (2.4 GHz, peer-to-peer) |
| Latency | < 5 ms end-to-end |
| Range | ~200 m line-of-sight |
| Core Compliance | ESP32 Arduino Core v3.0+ |
| Servo Channels | Up to 16 (PCA9685) |
| Safety | Watchdog timeout → neutral position |

---

## ESP32 Core v3.0+ Migration

This project was built with full compliance to the breaking API changes in ESP32 Arduino Core v3.0+, including:
- Updated `esp_now_register_recv_cb()` callback signatures
- New WiFi mode initialization sequences
- Revised MAC address handling

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/esp32-wireless-robotics-controller)
