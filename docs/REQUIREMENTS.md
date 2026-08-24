# System Requirements

Status: Draft

## 1. Functional Requirements

### FR-001 — Sensor Data Acquisition

The system shall acquire data from sensors connected to the
STM32 controller.

### FR-002 — Motor Monitoring

The system shall monitor the operating condition of a motor.

### FR-003 — Motor Speed Measurement

The system shall measure motor rotational speed using an encoder.

### FR-004 — Temperature Measurement

The system shall measure equipment temperature.

### FR-005 — Electrical Parameter Measurement

The system shall measure at least one electrical parameter
related to the motor, such as current.

### FR-006 — Real-Time Processing

The STM32 shall process sensor data in real time.

### FR-007 — RTOS

The STM32 firmware shall use FreeRTOS for task management.

### FR-008 — Industrial Communication

The STM32 shall communicate with the IoT Gateway through
RS485 using Modbus RTU.

### FR-009 — IoT Gateway

The ESP32 shall act as an IoT Gateway between the embedded
controller and the network.

### FR-010 — MQTT Communication

The ESP32 shall publish monitoring data using MQTT.

### FR-011 — Backend

The system shall provide a backend service for receiving,
processing, and storing monitoring data.

### FR-012 — Database

The system shall store historical equipment data.

### FR-013 — Dashboard

The system shall provide a dashboard for monitoring equipment
status and sensor data.

### FR-014 — Alarm

The system shall generate an alarm when monitored parameters
exceed predefined limits.

### FR-015 — Anomaly Detection

The system shall provide a machine-learning-based mechanism
for detecting abnormal equipment conditions.

### FR-016 — Fault Handling

The system shall detect and report selected sensor,
communication, or equipment faults.

---

## 2. Non-Functional Requirements

### NFR-001 — Reliability

The system should continue operating when a non-critical
sensor or communication error occurs.

### NFR-002 — Modularity

Hardware and software components should be modular and
independently testable.

### NFR-003 — Maintainability

The source code shall be organized and documented.

### NFR-004 — Version Control

The project shall use Git and GitHub for version control.

### NFR-005 — Budget

Additional hardware should remain within approximately
1.5–2 million VND.

### NFR-006 — Documentation

Major architecture and engineering decisions shall be documented.

---

## 3. Hardware Requirements

### Existing Hardware

- STM32
- ESP32

### Additional Hardware

To be determined after architecture and hardware design.

---

## 4. Software Requirements

### Embedded

- C
- STM32 HAL
- FreeRTOS

### Gateway

- ESP32
- Wi-Fi
- MQTT

### Backend

- Python

### Machine Learning

- Python
- Machine Learning framework to be determined

---

## 5. Communication Requirements

- UART
- I2C
- SPI
- RS485
- Modbus RTU
- MQTT
- TCP/IP

---

## 6. Future / Optional Requirements

The following features may be added if time, budget, and
project requirements justify them:

- PLC integration
- HMI/SCADA
- CAN communication
- Additional industrial protocols
- Advanced predictive maintenance