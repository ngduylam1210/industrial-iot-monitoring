# Project State

## Project Status

Planning & System Design

## Current Phase

Phase 1 — Engineering Definition

## Completed

- Project repository created
- Git initialized
- GitHub repository connected
- Project specification defined
- Project scope defined
- Initial system requirements defined
- Initial system architecture defined
- Initial engineering decisions documented

## Current Task

Finalize the hardware BOM and begin implementation from the electrical
subsystem, following the project execution roadmap below.

## Next Task

Validate the 12V power path, DRV8871 motor driver, motor, and STM32
connections before starting firmware integration.

## Current Execution Roadmap

The project will be implemented incrementally. Each step must be wired,
implemented, and tested before moving to the next dependent step.

### Electrical Subsystem

1. **12V power supply**
	- Define the protection and DC-DC conversion path.
	- Verify output voltage, polarity, grounding, and current capacity.

2. **DRV8871 and motor**
	- Connect the motor power path through the DRV8871.
	- Verify motor direction, PWM response, driver temperature, and fault behavior.

3. **Encoder**
	- Connect encoder channels A/B to STM32 timer inputs.
	- Verify pulse counting, direction detection, and RPM calculation.

### Firmware and Controller Integration

4. **Complete STM32 controller**
	- Integrate the motor driver and encoder interfaces.
	- Establish the STM32 firmware baseline, including the required timers,
	  GPIO, ADC, I2C, UART, and FreeRTOS tasks.
	- Verify closed-loop motor control and basic fault handling.

5. **NTC temperature sensor**
	- Connect the NTC voltage divider to an STM32 ADC input.
	- Calibrate the temperature conversion and verify motor temperature readings.

6. **INA219 electrical monitoring**
	- Connect INA219 through I2C in the motor supply path.
	- Verify bus voltage, current, and power measurements under changing load.

7. **RS485 communication**
	- Connect the STM32 UART to the RS485 transceiver.
	- Implement and test the Modbus RTU register map and communication fault handling.

### Gateway and Data Platform

8. **ESP32 gateway**
	- Connect the ESP32 to the RS485 bus.
	- Read STM32 Modbus data and verify gateway reconnection behavior.

9. **MQTT and backend**
	- Publish telemetry from ESP32 through Wi-Fi and MQTT.
	- Receive, validate, store, and expose the data in the backend.

10. **Machine learning**
	 - Build a dataset from verified telemetry.
	 - Engineer features from RPM, current, voltage, power, and temperature.
	 - Train and evaluate anomaly or condition classification models.

### Step Completion Rule

For every step, record the wiring or software change, the test result, and
any unresolved issue before starting the next dependent step. The roadmap
does not imply that a step is complete unless it is verified in the project.

## Current Architecture

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

## Implementation Dependency Flow

12V Power
↓
DRV8871 + Motor
↓
Encoder ↔ STM32 PWM / Encoder Firmware
↓
STM32 Complete Controller
├── NTC
├── INA219
└── RS485 / Modbus RTU
	↓
ESP32
↓
MQTT / Backend
↓
Machine Learning

## Current Hardware

- STM32
- ESP32

## Additional Hardware

Not purchased yet.

## Known Issues

None.

## Important Notes

- Requirements are still subject to refinement.
- Architecture is currently a draft.
- Hardware selection has not been finalized.
- No hardware purchases should be made until the BOM is defined.