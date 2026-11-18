---
layout: post
title: "RFID Barrier Gate Access Control"
description: An industrial-grade access control barrier gate driven by an Arduino Nano, MFRC522 13.56MHz RFID reader, 12V 5840-31ZY high-torque DC worm gear motor, BTS7960 43A H-bridge driver, dual position limit switches, and an LM2596 buck converter.
skills:
  - Arduino Nano
  - C++
  - RFID (MFRC522)
  - SPI Protocol
  - BTS7960 Motor Driver
  - Worm Gear Motor
  - Access Control
  - Hardware Position Tracking

main-image: /cover.jpg
order: 7
---

## Overview

A robust physical **RFID-based access control barrier gate** engineered for parking facilities, private compounds, and automated checkpoints. Built on the **Arduino Nano**, the system reads 13.56 MHz MIFARE RFID cards and keyfobs via SPI, validates credentials against an internal whitelist, and drives a high-torque **12V DC worm gear motor (5840-31ZY)** through an industrial **BTS7960 43A H-bridge driver**.

Physical gate geometry is tracked deterministically using dual micro limit switches for full open ($90^\circ$) and closed ($0^\circ$) positions, providing fail-safe motor shut-off and eliminating mechanical over-travel.

---

## System Components & Hardware Architecture

| Component | Specification | Role |
|-----------|--------------|------|
| **Arduino Nano** | ATmega328P (16 MHz) | Central logic controller |
| **MFRC522** | 13.56 MHz RFID module | Contactless card/fob authentication (3.3V logic via SPI) |
| **Worm Gear Motor** | 12V DC 5840-31ZY | High-torque non-backdrivable barrier boom drive |
| **BTS7960 Driver** | 43A High-Power H-Bridge | Industrial motor drive handling stall currents without overheating |
| **Limit Switches** | 2× Roller lever micro switches | Hardware position detection: $0^\circ$ (Closed) & $90^\circ$ (Open) |
| **LM2596 Buck Converter** | DC-DC step-down (12V $\rightarrow$ 5.0V) | Deterministic, thermally safe 5V power for Nano & logic |
| **12V 7Ah SLA Battery** | Sealed lead-acid accumulator | Heavy-duty power source for motor & logic |
| **Barrier Arm** | 100cm ACP hollow boom (fixed at 20cm mark) | Lightweight, durable physical gate barrier |

---

## Power Distribution & Wiring Architecture

- **12V Main Bus**: 12V battery power feeds directly to the BTS7960 driver ($B+/B-$) and the LM2596 buck converter input ($IN+/IN-$).
- **Regulated 5V Rail**: Buck converter outputs a stabilized 5.0V to the Arduino Nano $5V$ and $GND$ pins.
- **Motor Control**: BTS7960 $LPWM$ and $RPWM$ connect to Nano Digital Pins 5 and 6, while enable lines ($L\_EN$, $R\_EN$) tie to 5V.
- **Position Tracking**: Dual micro limit switches utilize internal pull-up resistors (`INPUT_PULLUP`):
  - Open Limit ($90^\circ$): Nano Pin D2 $\rightarrow$ NO, COM $\rightarrow$ GND
  - Closed Limit ($0^\circ$): Nano Pin D3 $\rightarrow$ NO, COM $\rightarrow$ GND
- **Access Control (SPI)**: MFRC522 powered strictly at 3.3V with SPI lines on Pins 9 (RST), 10 (SDA), 11 (MOSI), 12 (MISO), and 13 (SCK).

---

## Access Control Flow

1. **Idle Closed State**: Barrier rests at closed position ($0^\circ$), Closed Limit Switch engaged, motor stopped.
2. **Card Scan**: MFRC522 reads tag UID via hardware SPI.
3. **Whitelist Validation**: Firmware verifies UID against stored authorized database.
4. **Authorized Gate Raise**:
   - BTS7960 powers motor forward to lift the 100cm barrier.
   - Motor automatically shuts off the instant the $90^\circ$ Open Limit Switch triggers.
   - System holds gate open for a programmable clearance dwell period (e.g., 5 seconds).
5. **Deterministic Closure**: Motor reverses until the $0^\circ$ Closed Limit Switch triggers, locking the worm gear in place.
6. **Denied Access**: Unauthorized tags trigger an audio alert, maintaining the barrier securely closed.

---

## Source Code & Documentation

🔗 [View on GitHub: youniquestar/rfid-barrier-gate](https://github.com/youniquestar/rfid-barrier-gate)
