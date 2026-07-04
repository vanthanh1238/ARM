# DELI_ROBOT - Autonomous Delivery Robot

## Project Overview

DELI_ROBOT is an embedded systems project for an autonomous delivery robot platform based on the **STM32F407VGTx** microcontroller. The firmware implements motor control, sensor integration, communication protocols, and real-time monitoring capabilities.

**Version**: 3.0  
**Author**: Nguyen Minh Chuong & Tran Huy Hoang Anh & Le Van Thanh
**Key Feature (v3)**: Integrated Watchdog Timer for system reliability

---

## Features

### Core Capabilities
- **Motor Control**: PWM-based motor control with variable speed
- **Odometry**: Encoder feedback for distance and position tracking
- **Inertial Measurement**: Multiple IMU implementations (MPU6050, HMC5883L)
- **Communication**: CAN bus networking for multi-device coordination
- **UART**: Serial communication for debugging and remote control
- **Timing**: Real-Time Clock (RTC) and timer management
- **Input Capture**: High-precision sensor data acquisition
- **System Monitoring**: Watchdog timer for fault detection and recovery

### Sensors & Modules
- **IMU (Inertial Measurement Unit)**: 6-DOF and 9-DOF implementations
- **Encoders (ENC)**: Wheel speed and distance measurement
- **RTC (Real-Time Clock)**: Time tracking and scheduling
- **CAN Bus**: Vehicle-to-vehicle communication
- **Ultrasonic (SR04)**: Distance sensing for obstacle detection

---

## Project Structure

```
DELI_ROBOT/
├── README.md                          # This file
└── DELI_ROBOT/
    ├── src/                           # Main source code
    │   ├── main.c                     # Application entry point
    │   ├── stm32f4xx_it.c/h           # Interrupt handlers
    │   ├── stm32f4xx_conf.h           # MCU configuration
    │   ├── system_stm32f4xx.c         # System initialization
    │   ├── utils.c/h                  # Utility functions
    │   └── Define.h                   # Type definitions
    │
    ├── fileTV/                        # Peripheral drivers & modules
    │   ├── CAN/                       # CAN bus communication
    │   ├── ENC/                       # Encoder driver
    │   ├── IMU/                       # IMU sensor driver (6-DOF)
    │   ├── IMU1/                      # Alternative IMU driver
    │   ├── IMU_RTxQ/                  # Quaternion-based IMU
    │   ├── INC/                       # Input capture module
    │   ├── INPP/                      # Input processing
    │   ├── PWM/                       # PWM motor control
    │   ├── RTC/                       # Real-Time Clock
    │   ├── Timer/                     # Timer management
    │   ├── UART/                      # Serial communication
    │   ├── Watchdog_timer/            # Watchdog timer (v3)
    │   ├── inputcapture/              # Input capture handlers
    │   └── delay_01ms.h               # Delay utilities
    │
    ├── Libraries/                     # STM32 peripherals & CMSIS
    │   ├── CMSIS/                     # ARM CMSIS headers
    │   └── STM32F4xx_StdPeriph_Driver/ # STM32F4 standard library
    │
    ├── DebugConfig/                   # Debug configurations for Keil
    ├── Objects/                       # Compiled object files
    ├── Listings/                      # Assembly listings
    └── template.uvprojx              # Keil MDK project file
```

---

## Hardware Requirements

- **Microcontroller**: STM32F407VGTx (ARM Cortex-M4, 168 MHz)
- **Memory**: 1 MB Flash, 192 KB RAM
- **Peripherals**: 
  - 2x Motor with encoders
  - IMU sensor(s)
  - CAN transceiver
  - UART for debugging
  - RTC backup power
  - Ultrasonic distance sensor

---

## Build & Setup

### Prerequisites
- **Keil MDK** (uVision 5.x or later)
- **STM32F4xx Device Pack**
- **Compiler**: ARM Compiler (included with Keil)

### Building the Project
1. Open `DELI_ROBOT/template.uvprojx` in Keil uVision
2. Select target: **STM32F407VGTx**
3. Build the project: **Project → Rebuild All**
4. Flash to device using ST-Link debugger

### Configuration Files
- **Hardware Setup**: Edit `src/Define.h` for system parameters
- **MCU Clock**: Configure in `src/system_stm32f4xx.c`
- **Peripheral Pins**: Modify respective driver files in `fileTV/`

---

## Key Modules

### Motor Control (PWM)
- Variable speed control via TIM2
- PWM channels CCR1, CCR2 for motor direction
- Configurable frequency and resolution

### Odometry (Encoders)
- Real-time distance calculation
- Input capture on timer channels
- High-precision speed measurement

### Communication
- **CAN Bus**: Multi-device coordination at 500 kbps
- **UART6**: Debug serial at 115200 baud
- **DMA**: Efficient data transfer for UART/CAN

### Sensor Fusion
- IMU data integration (accelerometer, gyroscope, magnetometer)
- Quaternion-based orientation estimation (IMU_RTxQ)
- Complementary filtering for stability

### System Monitoring
- **Watchdog Timer (v3)**: Independent hardware watchdog
- **RTC**: Time tracking across power cycles
- **LEDs**: Status indicators on GPIO pins D11-D15

---


## Version History

- **v3.0**: Integrated Watchdog Timer for improved reliability
- **v2.x**: Core motor and sensor control
- **v1.x**: Initial development base

---

## Debugging

### Debug Configurations Available
- `blink_14_STM32F407VGTx.dbgconf` - Basic LED blink test
- `DELI_ROBOT_STM32F407VGTx.dbgconf` - Full application debug
- `Target_1_STM32F407VGTx.dbgconf` - Generic target config
- `template_STM32F407VGTx.dbgconf` - Template configuration

### UART Output
- **Port**: UART6 (pins PG14 Rx, PG9 Tx)
- **Baud**: 115200
- **Purpose**: Debug messages and command interface

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Watchdog resets | Ensure watchdog is fed regularly in interrupts |
| Motor not responding | Check PWM timer configuration and GPIO pins |
| CAN communication failure | Verify CAN transceiver connection and termination |
| IMU data unstable | Calibrate sensor, check I2C/SPI communication |
| Encoder reading incorrect | Verify input capture timer setup and pin configuration |

---

## License & Attribution

**Author**: Nguyen Minh Chuong & Tran Huy Hoang Anh & Le Van Thanh

---

## Notes

- This firmware uses **interrupt-driven architecture** for real-time responsiveness
- DMA transfers reduce CPU overhead for serial/CAN communication
- Modular design allows easy sensor/hardware swapping
- Regular watchdog feeding required to prevent system resets
