# System Architecture

Status: Draft

## 1. System Overview

The system consists of five main layers:

1. Sensing & Actuation Layer
2. Embedded Control Layer
3. Industrial Communication Layer
4. IoT Gateway Layer
5. Backend & Application Layer

---

## 2. High-Level Architecture

# Main Components
## 1 STM32
Responsibilities:
•	Sensor acquisition 
•	Signal processing 
•	Real-time processing 
•	Equipment monitoring 
•	Equipment control 
•	Fault detection 
•	Modbus RTU communication 
•	FreeRTOS task management 

## 2 ESP32
Responsibilities:
•	IoT Gateway 
•	RS485 communication with STM32 
•	Wi-Fi connectivity 
•	MQTT communication 
•	Data forwarding 
•	Network reconnection handling 

## 3 Backend
Responsibilities:
•	Receive MQTT data 
•	Process telemetry 
•	Store historical data 
•	Provide API 
•	Manage alarms 
•	Provide data for dashboard 
•	Interface with machine learning module 

## 4 Machine Learning Module
Responsibilities:
•	Analyze equipment data 
•	Detect abnormal operating conditions 
•	Provide anomaly scores or classifications 

## 5 Dashboard
Responsibilities:
•	Display real-time measurements 
•	Display historical data 
•	Display equipment status 
•	Display alarms 
•	Display anomaly information

# Communication Architecture

## STM32 ↔ ESP32
Protocol:
Physical layer: RS485
Protocol: Modbus RTU

## ESP32 ↔ Backend
Protocol:
Transport: Wi-Fi / TCP/IP
Application: MQTT

## Backend ↔ Dashboard
Protocol:
REST API
WebSocket if required