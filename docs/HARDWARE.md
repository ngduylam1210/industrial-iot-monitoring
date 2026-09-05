# Hardware Specification

Status: Draft

## 1. System Hardware Architecture

### POWER SUPPLY 12V

12 DC POWER SUPPLY
      |     
     FUSE
      |----------------->  DC-DC 
      |                   12V -> 5V
      |                       |
      |                       |____ESP32
      |                       |____STM32*
    INA219
      |
   DRV8871
      |
    MOTOR

=> 5V - STM32

### GA25-370-1260-EN
Rated voltage = 12 V
Rated speed   ≈ 100 RPM
Rated current ≈ 0.3 A
Stall current ≈ 1.3 A
Encoder       = AB

### INA219
Voltage bus 0-26V, 12-bit, I2C/SMBus
Current
Power

### DRV8871
6.5–45V
~3.6A peak

## STM32 - DRV8871
                   STM32
              ┌─────────────┐
              │             │
        PWM ──┤             │
        DIR ──┤ GPIO        │
              │             │
              └──────┬──────┘
                     │
                     ▼
                ┌─────────┐
                │ DRV8871 │
                └────┬────┘
                     │
                 H-Bridge
                     │
                     ▼
                   MOTOR

=> PWM quyết định mức công suất trung bình -> tốc độ Motor

### Encoder Motor
AB Encoder
STM32 đọc xung A/B:
- tốc độ
- chiều quay
- vị trí tương đối
- số vòng quay
Encoder pulses
      ↓
  STM32 Timer
      ↓
     RPM

=> closed-loop control + condition monitoring
=> Khi đấu dây, Kiểm tra điện áp cấp và mức logic đầu ra encoder của đúng phiên bản GA25-370

## NTC
NTC 10K
1%
đầu dò inox
dây 1m

              3.3V
                │
              10kΩ
                │
                ├──────────── ADC STM32
                │
             NTC 10K
                │
               GND

### Khi nhiệt độ thay đổi: 

      Temperature
          ↓
 NTC resistance changes
          ↓
Voltage divider changes
          ↓
   ADC voltage changes
          ↓
STM32 calculates temperature

### Sau đó đặt đầu dò vào vỏ motor:
        MOTOR
   ┌───────────────┐
   │               │
   │       ●       │ ← NTC
   │               │
   └───────────────┘
           │
         1m cable
           │
           ▼
        STM32 ADC

- RPM
- Current
- Voltage
- Power
- Temperature

Tăng tải
   ↓
Motor phải tạo torque lớn hơn
   ↓
Current tăng
   ↓
RPM giảm
   ↓
Nhiệt tăng
=> Machine Learning

## Machine Learning
Physical system
      ↓
   Sensors
      ↓
Data acquisition
      ↓
   Dataset
      ↓
Feature engineering
      ↓
Machine Learning
      ↓
Condition classification

### Model học
      RPM
    Current
  Temperature
    Voltage
       │
       ▼
       ML
       │
       ▼
┌─────────────────┐
│ Normal          │
│ Overload        │
│ Abnormal        │
│ Stall           │
└─────────────────┘

## STM32
STM32 là edge controller / real-time controller.

             STM32
               │
      ┌────────┼────────┐
      │        │        │
      ▼        ▼        ▼
    PWM      Encoder   ADC
      │        │        │
      │        │        ├── NTC
      │        │        └── other sensors
      │        │
      ▼        ▼
   Motor     RPM
  Control

- STM32
- HAL
- Timer
- PWM
- Input Capture/Encoder
- ADC
- I²C
- UART
- FreeRTOS

## ESP32

STM32
 │
 │ sensor data
 ▼
RS485
 │
 ▼
ESP32
 │
 │ Wi-Fi
 ▼
MQTT / HTTP
 │
 ▼
Server

## RS485
             STM32
                │
             UART
                │
             MAX3485
                │
════════════════╪════════════════
             RS485
════════════════╪════════════════
                │
             MAX3485
                │
             UART
                │
             ESP32

### Sau này - Modbus RTU
STM32 đóng vai trò device/slave và ESP32 gateway/master

## WORK FLOW

                 ┌─────────────────┐
                 │    12V PSU      │
                 └────────┬────────┘
                          │
                        Fuse
                          │
                       INA219
                          │
                          ▼
                     ┌─────────┐
                     │ DRV8871 │
                     └────┬────┘
                          │
                         PWM
                          │
                          ▼
                    ┌───────────┐
                    │ GA25-370  │
                    │   MOTOR   │
                    └─────┬─────┘
                          │
                ┌─────────┴─────────┐
                │                   │
             Encoder              NTC
                │                   │
                ▼                   ▼
             ┌────────────────────────┐
             │         STM32          │
             │                        │
             │ PWM                    │
             │ Encoder → RPM          │
             │ ADC → Temperature      │
             │ I²C → INA219           │
             │ FreeRTOS               │
             └────────────┬───────────┘
                          │
                       RS485
                      Modbus RTU
                          │
                          ▼
                    ┌──────────┐
                    │  ESP32   │
                    │ IoT GW   │
                    └────┬─────┘
                         │
                       Wi-Fi
                         │
                         ▼
                    ┌──────────┐
                    │ Backend  │
                    └────┬─────┘
                         │
                ┌────────┴────────┐
                │                 │
            Dashboard             ML
                                  │
                                  ▼
                            Motor Condition