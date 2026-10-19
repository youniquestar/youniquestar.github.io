---
layout: post
title: "RFID Barrier Gate Access Control"
description: An Arduino Nano RFID access control system using MFRC522 reader, TowerPro MG90S metal-gear servo-actuated wooden barrier gate, with audio-visual feedback for authorised and denied access events.
skills:
  - Arduino Nano
  - C++
  - RFID (MFRC522)
  - SPI Protocol
  - Servo Control
  - Access Control
  - Security Systems

main-image: /cover.jpg
order: 7
---

## Overview

A physical **RFID-based access control system** that reads 13.56 MHz MIFARE cards/tags and raises or lowers a wooden barrier gate accordingly. Authorized UIDs are stored in firmware; unauthorized attempts trigger an alarm and visual denial feedback.

---

## System Components

| Component | Specification | Role |
|-----------|--------------|------|
| **Arduino Nano** | ATmega328P | Main controller |
| **MFRC522** | 13.56 MHz RFID | Card/tag reader (SPI) |
| **MG90S Servo** | Metal gear, 180° | Barrier arm actuation |
| **RGB LED** | Common cathode | Status indicator (green=open, red=denied) |
| **Buzzer** | Active piezo | Audio feedback |
| **Barrier Arm** | Wooden boom | Physical gate |

---

## Access Control Flow

1. **Idle State**: Red LED steady, barrier down
2. **Card Presented**: MFRC522 reads UID via SPI
3. **UID Lookup**: Compare against authorized UID whitelist in firmware
4. **Authorized**: Green LED, success tone, servo raises barrier → 3-second hold → barrier lowers
5. **Denied**: Red LED blink, alarm tone sequence, barrier stays down

---

## Engineering Details

- **SPI Communication**: Hardware SPI (pins 10–13) for high-speed RFID reads
- **Servo Soft Start**: Gradual PWM ramping to reduce mechanical stress on the wooden gate arm
- **Debounce Logic**: Prevents multiple reads of the same card within a cooldown window
- **Extensibility**: UID whitelist can be expanded; architecture supports future EEPROM storage or serial management

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/arduino-rfid-barrier-gate)
