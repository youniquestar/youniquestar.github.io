---
layout: post
title: "Smart Assistive Walking Stick"
description: An assistive smart mobility cane for visually impaired individuals featuring ultrasonic spatial obstacle detection with dual-frequency acoustic beeps and haptic vibration feedback for safe, independent navigation.
skills:
  - Arduino
  - C++
  - Assistive Technology
  - Ultrasonic Sensing
  - Haptic Feedback
  - Accessibility Engineering
  - Embedded Systems

main-image: /cover.jpg
order: 8
---

## Overview

A **smart walking cane** designed to help visually impaired individuals navigate their environment safely and independently. The cane uses an HC-SR04 ultrasonic sensor to detect obstacles ahead, then provides **dual-mode feedback** — audio tones and haptic vibration — that intensify as obstacles get closer.

---

## How It Works

### Detection
- HC-SR04 ultrasonic sensor mounted at cane height (~waist level)
- Continuous distance sampling at ~20 Hz
- Effective detection range: 4 cm to 200 cm

### Feedback Zones

| Zone | Distance | Audio | Vibration |
|------|----------|-------|-----------|
| **Safe** | > 100 cm | Silent | None |
| **Caution** | 50–100 cm | Slow beep (1 Hz) | Light pulse |
| **Warning** | 20–50 cm | Fast beep (4 Hz) | Medium pulse |
| **Danger** | < 20 cm | Continuous tone | Continuous vibration |

### Design Philosophy
- **Dual-channel feedback** ensures the user receives warnings even in noisy environments (vibration) or when wearing gloves (audio)
- **Progressive intensity** gives the user spatial awareness — not just "obstacle present" but "obstacle getting closer"
- **Low power**: Runs on 9V battery with efficient sleep-wake cycling

---

## Social Impact

This project addresses a real accessibility need. Over 2.2 billion people worldwide have a vision impairment. While commercial smart canes exist at premium price points, this open-source design can be built for under $15 in components, making it accessible to communities that need it most.

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/arduino-smart-walking-stick)
