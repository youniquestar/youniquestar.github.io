---
layout: post
title: "Astari Selah — 5-DOF Robotic Manipulator"
description: An open-source, production-grade 5-DOF articulated robotic arm uniting ESP32 bare-metal C++ firmware (FreeRTOS), ROS 2 Jazzy kinematics, and modular FreeCAD parametric solid assemblies. A full-stack robotics project from firmware to simulation.
skills:
  - ROS 2 Jazzy
  - ESP32 / FreeRTOS
  - C++
  - Python
  - Forward & Inverse Kinematics
  - FreeCAD CAD
  - URDF / Xacro
  - Gazebo Simulation
  - SPI / I2C

main-image: /cover.jpg
order: 1
---

## Overview

**Astari Selah** is a fully open-source, 5-degree-of-freedom articulated robotic manipulator designed from the ground up — spanning mechanical design, embedded firmware, and high-level robot control.

The project demonstrates end-to-end robotics engineering: from parametric CAD modelling in FreeCAD, to bare-metal ESP32 servo control under FreeRTOS, to ROS 2 kinematic planning and Gazebo simulation.

---

## Architecture

| Layer | Technology | Responsibility |
|-------|-----------|----------------|
| **Firmware** | ESP32 + FreeRTOS (C++) | Real-time joint servo control, SPI/I2C sensor reads |
| **Middleware** | ROS 2 Jazzy | Joint state publishing, trajectory planning, TF tree |
| **Kinematics** | Custom Python | DH-parameter FK/IK solvers, Jacobian computation |
| **Simulation** | Gazebo + RViz2 | Physics-based validation, visualization |
| **CAD** | FreeCAD PartDesign | Parametric link/joint assemblies, STL export |

---

## Key Engineering Decisions

- **ESP32 Core v3.0+ Compliance**: Firmware uses the updated callback API, ensuring forward compatibility with Espressif's evolving SDK
- **FreeRTOS Task Architecture**: Dedicated tasks for servo control, sensor polling, and serial communication with proper mutex guards
- **Modular URDF/Xacro**: Each link is a parameterized Xacro macro, allowing rapid design iteration without touching the control stack
- **Dual-Layer Control**: Low-level PID on the ESP32, high-level trajectory planning in ROS 2

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/astari-selah)
