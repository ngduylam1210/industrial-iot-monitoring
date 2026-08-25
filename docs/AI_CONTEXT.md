# AI Context

## 1. Project Identity

Project:
Industrial IoT Monitoring & Predictive Maintenance System

Purpose:
Build an engineering portfolio project demonstrating skills in
Embedded Systems, Industrial IoT, and Automation.

---

## 2. Target Skills

Primary:

- Embedded C
- STM32
- FreeRTOS
- UART / I2C / SPI
- RS485
- Modbus RTU
- ESP32
- Wi-Fi
- MQTT
- Backend development
- Database
- Machine Learning
- Git / GitHub

Secondary:

- PLC
- HMI / SCADA
- CAN
- Additional industrial protocols

---

## 3. Current Architecture

STM32
↓
RS485 / Modbus RTU
↓
ESP32
↓
Wi-Fi / MQTT
↓
Backend
↓
Database
↓
Dashboard
↓
Machine Learning

---

## 4. Component Responsibilities

### STM32

Responsible for:

- Real-time sensor acquisition
- Data processing
- Equipment monitoring
- Equipment control
- Fault detection
- Modbus RTU
- FreeRTOS

### ESP32

Responsible for:

- IoT Gateway
- RS485 communication
- Wi-Fi
- MQTT
- Network communication

### Backend

Responsible for:

- Data reception
- Data processing
- Database
- API
- Alarm management
- Machine Learning integration

---

## 5. Engineering Rules

1. Do not change the architecture without discussing the reason first.

2. Do not introduce unnecessary hardware.

3. Prefer using existing hardware whenever possible.

4. Implement and test components incrementally.

5. Do not rewrite working code without a clear reason.

6. Keep hardware and software modular.

7. Explain important technical decisions.

8. Record important architecture decisions in DECISIONS.md.

9. Keep PROJECT_STATE.md updated after completing major tasks.

10. Do not assume a feature has been implemented unless it is
verified in the project.

---

## 6. AI Working Rules

Before starting a task:

1. Read PROJECT_SPEC.md.
2. Read REQUIREMENTS.md.
3. Read ARCHITECTURE.md.
4. Read DECISIONS.md.
5. Read PROJECT_STATE.md.
6. Identify the current task.

When completing a task:

1. Explain what was changed.
2. Identify files that were modified.
3. Provide testing instructions.
4. Identify remaining issues.
5. Update PROJECT_STATE.md when appropriate.

---

## 7. Multi-AI Continuity

This project may be developed using multiple AI assistants.

Possible assistants:

- ChatGPT
- Claude
- Gemini

All AI assistants must treat the Git repository and project
documentation as the primary source of project state.

The AI conversation itself is not the authoritative project state.

When joining an existing project session:

1. Read the project documentation.
2. Read PROJECT_STATE.md.
3. Inspect the relevant source code.
4. Continue from the current task.
5. Do not restart or redesign the project unnecessarily.

---

## 8. Current Project State

Current Phase:
Phase 1 — Engineering Definition

Current Task:
Establish AI-assisted development workflow.

Next Task:
Test the multi-AI handoff workflow.

---

## 9. User Preferences

- Work incrementally.
- Provide step-by-step instructions.
- Do not skip important setup steps.
- Explain terminal commands briefly.
- Avoid unnecessary complexity.
- Prioritize practical implementation over excessive theory.