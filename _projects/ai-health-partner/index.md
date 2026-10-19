---
layout: post
title: "AI Health Partner — Clinical Triage Engine"
description: An intelligent conversational AI backend that automates clinical triage, parses unstructured patient language into validated clinical data, and maintains empathetic daily follow-ups — built during a high-stakes hackathon.
skills:
  - Python
  - NLP
  - State Machine Design
  - Conversational AI
  - REST API
  - Healthcare Tech
  - Backend Architecture

main-image: /cover.jpg
order: 3
---

## Overview

Developed during a high-stakes hackathon, **AI Health Partner** is an intelligent conversational engine designed to bridge the gap between overstrained healthcare systems and patient care. The backend service automates the clinical triage process and maintains empathetic daily follow-ups to ensure treatment adherence.

---

## My Role: AI Backend Developer

I architected a **modular state-machine logic** that parses unstructured patient natural language into validated clinical data — without the unpredictability of raw LLM outputs.

---

## Key Features

- **Automated Clinical Triage**: Symptom intake through natural conversation, severity classification, and appropriate care-level routing
- **State Machine Architecture**: Deterministic conversation flow ensuring every patient interaction follows validated clinical pathways
- **NLP Parsing**: Extracts structured medical data (symptoms, duration, severity) from free-text patient input
- **Follow-Up Engine**: Scheduled check-ins to monitor treatment adherence and recovery progress
- **Empathetic Responses**: Tone-aware response generation that maintains clinical accuracy while being supportive

---

## Technical Design

```
Patient Input → NLP Parser → State Machine Router
                                    ↓
                    ┌───────────────┼───────────────┐
                    ↓               ↓               ↓
              Triage Flow    Checkup Flow    Follow-Up Flow
                    ↓               ↓               ↓
              Severity Score   Vitals Log    Adherence Check
                    ↓               ↓               ↓
                    └───────────────┼───────────────┘
                                    ↓
                          Structured JSON Response
```

---

## Source Code

🔗 [View on GitHub](https://github.com/youniquestar/ai_health_partner)
