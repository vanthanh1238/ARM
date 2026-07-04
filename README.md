# ARM - STM32F4 Autonomous Delivery Robot Project

Embedded systems project combining firmware development and PCB hardware design for an autonomous delivery robot platform based on STM32F407VGTx.

## Project Structure

### [Code_F4/](Code_F4/) - Firmware & Software
- **DELI_ROBOT**: Complete embedded firmware for autonomous delivery robot
  - Motor control, encoder feedback, IMU sensor fusion
  - CAN bus communication, UART debugging
  - Watchdog timer, RTC, real-time control loops
  - Built with STM32 Standard Library, compilable in Keil MDK

### [Expansion_Board_F4/](Expansion_Board_F4/) - Hardware Design
- Custom PCB expansion board for STM32F4 ecosystem
  - Designed in Altium Designer
  - Multiple design iterations (v1, v2, v3)
  - Gerber files and manufacturing documentation included
  - Interfaces: motors, sensors, CAN, UART, power distribution

## Quick Start

### Firmware Development
```
1. Open Code_F4/Final_Version/DELI_ROBOT/DELI_ROBOT/template.uvprojx in Keil MDK
2. Select target: STM32F407VGTx
3. Build and flash to hardware
```

### PCB Design & Manufacturing
```
1. Open Expansion_Board_F4/STM32F4 version1.PrjPcb in Altium Designer
2. Review/edit schematics and layouts (v1, v2, v3)
3. Export Gerber files from Project Outputs folder
4. Submit to PCB manufacturer (JLCPCB, PCBWay, etc.)
```

## Key Features

**Firmware:**
- Motor PWM control with encoder odometry
- 6/9-DOF IMU with quaternion-based orientation estimation
- CAN vehicle-to-vehicle communication
- Watchdog timer for system reliability
- Interrupt-driven architecture with DMA transfers

**Hardware:**
- Multi-layer PCB with optimized power distribution
- Extended I/O and communication interfaces
- Protection circuitry and filtering
- Manufacturing-ready Gerber files

## Technologies

- **Microcontroller**: STM32F407VGTx (ARM Cortex-M4, 168 MHz, 1MB Flash)
- **IDE**: Keil MDK uVision
- **PCB Design**: Altium Designer
- **Sensors**: MPU6050, HMC5883L encoders, ultrasonic
- **Communication**: CAN bus, UART, I2C, SPI

## File Organization

```
ARM/
├── Code_F4/
│   └── Final_Version/
│       ├── DELI_ROBOT/          # Firmware source & project
│       └── readme.txt           # Original notes
│
├── Expansion_Board_F4/          # PCB design & manufacturing files
│   ├── *.SchDoc                 # Altium schematics
│   ├── *.PcbDoc                 # PCB layouts (v1, v2, v3)
│   ├── Project Outputs/         # Gerber, drill, DRC files
│   └── History/                 # Previous versions
│
├── README.md                    # This file
└── .git/                        # Version control
```

## Documentation

- **[DELI_ROBOT](Code_F4/Final_Version/DELI_ROBOT/README.md)** - Complete firmware documentation
- **[Expansion_Board_F4](Expansion_Board_F4/README.md)** - PCB design and manufacturing guide

## Development Status

- ✅ Firmware v3.0 (with watchdog timer integration)
- ✅ PCB design v1 with layout iterations (v2, v3)
- ✅ Design rule checks passed
- ✅ Manufacturing files ready

## Contact & Attribution

**Author**: Nguyen Minh Chuong & Tran Huy Hoang Anh & Le Van Thanh

---

*Last Updated: July 2026*
