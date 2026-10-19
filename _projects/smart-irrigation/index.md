---
layout: post
title: "Smart Irrigation System"
description: An environment-aware automated agricultural irrigation controller integrating soil moisture sensing, DHT11 microclimate telemetry, ambient light gating, water pump relay control, and a servo-swept sprinkler head for precision watering.
skills:
  - Arduino
  - C++
  - IoT / Smart Agriculture
  - Soil Moisture Sensing
  - DHT11 Temperature & Humidity
  - Relay & Pump Control
  - Servo Actuation

main-image: /cover.jpg
order: 6
---

## Overview

A **multi-sensor automated irrigation controller** that makes intelligent watering decisions based on real-time environmental conditions. The system monitors soil moisture, air temperature, humidity, and ambient light to determine when, and how much, to water crops — then actuates a water pump and servo-swept sprinkler head accordingly.

---

## Sensor Array

| Sensor | Measures | Role in Decision |
|--------|----------|-----------------|
| **Soil Moisture** | Volumetric water content | Primary trigger: irrigate when soil is dry |
| **DHT11** | Temperature + Humidity | Suppress irrigation in high humidity; increase in high heat |
| **LDR (Light Sensor)** | Ambient light level | Gate irrigation to avoid watering in direct sunlight (evaporation loss) |

---

## Actuation System

- **Relay Module → Water Pump**: Switches the 12V pump on/off based on the control algorithm
- **Servo Motor → Sprinkler Head**: Sweeps the sprinkler 180° for even water distribution across the planting bed

---

## Control Algorithm

```
IF soil_moisture < DRY_THRESHOLD
   AND humidity < HIGH_HUMIDITY
   AND light_level < DIRECT_SUN
THEN
   activate_pump()
   sweep_sprinkler(180°)
   WHILE soil_moisture < WET_THRESHOLD
      continue_watering()
   deactivate_pump()
ELSE
   sleep(CHECK_INTERVAL)
```

---

## Real-World Application

This system was designed for small-scale urban farming and greenhouse use, where manual watering is impractical. It reduces water waste by only irrigating when conditions are optimal and stops automatically when the soil reaches adequate moisture levels.

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/arduino-smart-irrigation-system)
