---
layout: post
title: "Pulse AI — Predictive Maintenance Engine"
description: An end-to-end, production-grade machine learning pipeline and FastAPI backend that monitors industrial machinery health, detects anomalies in real-time sensor telemetry, and diagnoses root-cause failures before catastrophic breakdowns occur.
skills:
  - Python
  - Scikit-learn
  - Pandas / NumPy
  - FastAPI
  - Machine Learning
  - Data Engineering
  - REST API
  - Predictive Analytics

main-image: /cover.jpg
order: 2
---

## Overview

**Pulse AI** is a real-time predictive maintenance and root-cause diagnosis engine built around the AI4I 2020 Predictive Maintenance Dataset (10,000 milling machine records). It bridges the gap between raw time-series sensor telemetry and robust, deployable backend architecture.

---

## Technical Architecture

### Data Pipeline
- **Ingestion**: Raw CSV sensor data (air/process temperature, rotational speed, torque, tool wear)
- **Preprocessing**: Automated null handling, outlier detection, feature scaling with `StandardScaler`
- **Feature Engineering**: Derived features including temperature differential, power output, and tool wear bins

### ML Pipeline
- **Binary Classification**: Predicts whether a machine will fail (anomaly detection)
- **Multi-Class Diagnosis**: Identifies the specific failure mode — Heat Dissipation, Power, Overstrain, Tool Wear, or Random failure
- **Model Selection**: Evaluated Logistic Regression, Random Forest, Gradient Boosting, and SVM; selected based on F1-score and recall

### Backend API
- **FastAPI** REST endpoints for real-time health scoring
- Accepts live sensor readings and returns failure probability + root-cause diagnosis
- Structured JSON responses suitable for dashboard integration

---

## Key Results

| Metric | Value |
|--------|-------|
| Anomaly Detection Accuracy | ~97% |
| Root-Cause Diagnosis F1 | ~0.91 |
| API Response Time | < 50ms |

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/pulse-ai)
