---
layout: post
title: "IoT-Based Smart Irrigation System"
description: An autonomous, cloud-connected precision agriculture and smart irrigation controller built on NodeMCU ESP8266 and Blynk IoT. Features soil moisture sensing, automated 5V relay pump actuation, and an SG90 oscillating servo sprinkler nozzle for uniform water dispersal with live telemetry.
skills:
  - NodeMCU ESP8266
  - Blynk IoT Cloud
  - C++
  - Soil Moisture Sensing
  - Relay & Pump Control
  - SG90 Servo Actuation
  - Cloud Telemetry
  - Smart Agriculture

main-image: /cover.jpg
order: 6
---

## Overview

An intelligent, cloud-connected precision agriculture and automated irrigation system engineered for nurseries, greenhouses, and seedling trays. Powered by a **NodeMCU ESP8266**, the system continuously samples soil volumetric moisture levels, performs closed-loop automated hysteresis control to regulate a **submersible DC water pump** via an optocoupled **5V relay**, and actively sweeps an **SG90 servo-driven oscillating sprinkler head** across the plant canopy for uniform water distribution.

Real-time telemetry is streamed to a remote **Blynk 2.0 IoT** dashboard (web, tablet, and mobile), delivering live gauge readouts, status indicators, and event notifications.

---

## 📸 Hardware Showcase & Cloud Dashboard

### 1. Physical Hardware & Live Cloud Telemetry

| Physical Circuit & Irrigation Bed | Live Remote Blynk IoT Dashboard |
| :---: | :---: |
| <img src="{{ '/assets/images/projects/smart-irrigation/hardware_setup.jpg' | relative_url }}" width="420" alt="Hardware Setup: Seedling Tray, NodeMCU, Relay & Servo Sprinkler" style="border-radius: 8px; margin: 8px 0;"> | <img src="{{ '/assets/images/projects/smart-irrigation/blynk_dashboard_live.jpg' | relative_url }}" width="420" alt="Live Blynk IoT Dashboard on Tablet" style="border-radius: 8px; margin: 8px 0;"> |
| *Multi-cell seedling tray, drip network, NodeMCU ESP8266, 5V relay, and SG90 servo sprinkler nozzle.* | *Blynk 2.0 cloud dashboard running on tablet displaying live moisture gauge & telemetry.* |

### 2. Live Automated Irrigation in Action

<p align="center">
  <img src="{{ '/assets/images/projects/smart-irrigation/system_demonstration.gif' | relative_url }}" width="380" alt="Smart Irrigation Live Demonstration" style="border-radius: 8px; margin: 8px 0;">
  <br>
  <em><b>Live Closed-Loop Response:</b> Removing the sensor probe from moist soil drops the reading below the 500 threshold, instantly engaging the pump relay, oscillating the SG90 sprinkler nozzle across the plant canopy (85°–150°), and broadcasting a <code>🔴 SOIL DRY</code> alert to the Blynk cloud dashboard.</em>
</p>

---

## System Architecture

```
┌─────────────────────────┐
│ Soil Moisture Sensor A0 │
└────────────┬────────────┘
             │ Analog Voltage (0-3.3V)
             ▼
┌─────────────────────────┐
│     NodeMCU ESP8266     │◄──────► Wi-Fi 2.4GHz / Blynk IoT Cloud
│ (Hysteresis Controller) │         (Live Gauges, Status, Alerts)
└──────┬────────────┬─────┘
       │ D1 (HIGH)  │ D2 (PWM)
       ▼            ▼
┌──────────────┐ ┌──────────────────────────┐
│ 5V Relay +   │ │ SG90 Servo Sprinkler     │
│ Water Pump   │ │ (Sweeps 85° - 150°)      │
└──────────────┘ └──────────────────────────┘
```

---

## Hardware Bill of Materials (BOM)

| Component | Specification | Role in System |
|-----------|---------------|----------------|
| **NodeMCU ESP8266** | Tensilica 32-bit, 2.4 GHz Wi-Fi | Edge microcontroller & IoT gateway |
| **Soil Moisture Sensor** | Analog probe with LM393 comparator | Volumetric soil moisture sensing (A0) |
| **Relay Module** | 1-channel 5V optocoupled relay | High-current isolation for water pump |
| **Mini Submersible Pump** | 5V / 12V DC water pump | Reservoir water extraction |
| **SG90 Micro Servo** | 9g servo motor, 180° range | Dynamic sprinkler head oscillation |
| **Tubing & Nozzle** | Flexible silicone hose & manifold | Drip & spray distribution network |
| **Power Supply** | 5V DC regulated power adapter | System power distribution |

---

## Control Logic & Cloud Integration

- **Sampling Interval**: Reads analog soil moisture every 2000 ms via non-blocking Blynk timer.
- **Hysteresis Thresholds**:
  - `Moisture < 500` (Dry): Relay energizes $\rightarrow$ Pump ON $\rightarrow$ SG90 oscillates ($85^\circ \text{--} 150^\circ$) $\rightarrow$ Blynk pushes `🔴 SOIL DRY` alert.
  - `Moisture > 600` (Wet): Relay de-energizes $\rightarrow$ Pump OFF $\rightarrow$ SG90 parks at $90^\circ$ $\rightarrow$ Blynk pushes `🟢 SOIL WET` status.
- **Remote Telemetry**: Virtual pin `V0` (radial moisture gauge), `V1` (status text), and `V2` (virtual status LED).

---

## Source Code & Documentation

🔗 [View on GitHub: youniquestar/IoT-Based-Smart-Irrigation-System](https://github.com/youniquestar/IoT-Based-Smart-Irrigation-System)
