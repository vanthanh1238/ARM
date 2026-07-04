# Expansion_Board_F4 - STM32F4 Expansion Module

## Project Overview

**Expansion_Board_F4** is a custom PCB expansion board designed for the STM32F4 microcontroller ecosystem. This board extends the capabilities of the base STM32F407VGTx system by providing additional interfaces, peripheral connections, and power distribution circuits.

This expansion board is designed to work in conjunction with the [DELI_ROBOT](../Code_F4/Final_Version/DELI_ROBOT/README.md) autonomous delivery robot platform.

**Design Tool**: Altium Designer  
**Target MCU**: STM32F407VGTx  
**Current Version**: v1 (with v2, v3 iterations)

---

## Features

### Typical Expansion Capabilities
- **Extended I/O Connectors**: Additional GPIO headers for sensor/actuator connections
- **Power Distribution**: Efficient power management and supply rails
- **Communication Interfaces**: Additional UART, SPI, I2C, or CAN ports
- **Motor/Sensor Connectors**: Standardized headers for encoders, IMU, and motor control
- **Protection Circuitry**: ESD protection, overcurrent protection, filtering
- **Debug Interface**: Enhanced debugging and programming connections

---

## Project Structure

```
Expansion_Board_F4/
├── README.md                          # This file
├── STM32F4 version1.PrjPcb           # Main Altium project file
├── STM32F4 version1.PrjPcbStructure  # Project structure definition
├── version1.SchDoc                    # Schematic (main design)
├── version1.PcbDoc                    # PCB layout (corresponding to SchDoc v1)
├── version2.PcbDoc                    # PCB layout v2 (layout revision)
├── ver3.PcbDoc                        # PCB layout v3 (latest layout)
├── PCB1.PcbDoc                        # Alternative PCB variant
│
├── Project Outputs for STM32F4 version1/  # Manufacturing & CAM files
│   ├── Design Rule Check Files
│   │   ├── Design Rule Check - version1.drc  # DRC results v1
│   │   ├── Design Rule Check - version2.drc  # DRC results v2
│   │   ├── Design Rule Check - ver3.drc      # DRC results v3
│   │   └── *.html                             # HTML reports
│   │
│   ├── Gerber Files (Manufacturing)
│   │   ├── version1.GTL                # Top copper layer
│   │   ├── version1.GBL                # Bottom copper layer
│   │   ├── version1.GKO                # Keep-out layer
│   │   └── *.apr                       # Photoplotter aperture file
│   │
│   ├── Drill Files
│   │   ├── version1.TXT                # NC drill file (standard format)
│   │   ├── version1.LDP                # Laser drill PDF
│   │   └── version1.DRR                # Drill report
│   │
│   ├── Reports & Documentation
│   │   ├── version1.REP                # Assembly/placement report
│   │   ├── version1.RUL                # Design rules report
│   │   ├── version1.EXTREP             # Extra report
│   │   └── Status Report.Txt           # Generation status
│   │
│   └── Other
│       └── version1-macro.APR_LIB      # Aperture macro library
│
├── Project Logs for STM32F4 version1/  # Project revision history
├── History/                             # Historical versions
└── __Previews/                          # Design previews/renders
    └── version1.SchDocPreview
```

---

## Design Versions

### Version History

| Version | Status | Notes |
|---------|--------|-------|
| **v1** | Initial Release | Original design, passed DRC |
| **v2** | Layout Revision | PCB layout improvements, manufacturing optimization |
| **v3** | Latest | Final layout version with all improvements |
| **PCB1** | Alternative | Alternative variant layout |

Each version has corresponding:
- Schematic (v1 is the primary schematic)
- PCB layout files (versions 1, 2, 3)
- Design rule check reports
- Manufacturing/Gerber files

---

## Manufacturing Files

### Gerber Files (For PCB Manufacturing)

Located in: `Project Outputs for STM32F4 version1/`

**Required Files:**
- `version1.GTL` - Top copper layer
- `version1.GBL` - Bottom copper layer
- `version1.GKO` - Keep-out/outline layer
- `version1.apr` - Aperture file

**Usage:**
1. Zip all Gerber files together
2. Submit to PCB manufacturer (JLCPCB, PCBWay, Seeed, etc.)
3. Include drill files (*.TXT, *.LDP, *.DRR)

### Drill Files

- `version1.TXT` - Standard NC drill format (send to manufacturer)
- `version1.LDP` - Laser drill PDF
- `version1.DRR` - Drill file report with specifications

### Design Rules & Reports

- `Design Rule Check - version*.drc` - Automated design rule validation
- `version1.REP` - Assembly and placement report
- `version1.RUL` - Design rules used in verification

---

## Design Specifications

### PCB Characteristics
- **Layers**: Multi-layer design (typically 2-4 layers)
- **Copper Traces**: Standard trace width/spacing per manufacturing guidelines
- **Via Configuration**: Through-hole and blind vias as needed
- **Material**: FR-4 standard PCB material

### Connector Standard
- Designed for STM32F407VGTx microcontroller integration
- Compatible with DELI_ROBOT firmware/hardware
- Standard 2.54mm (0.1") pitch headers for most connections

### Power Distribution
- Multiple voltage rails for different subsystems
- Decoupling capacitors for signal integrity
- Ground plane for noise reduction

---

## Design Tools & Software

### Required Software
- **Altium Designer** (version 21.x or compatible)
  - Used for schematic and PCB layout
  - File formats: .SchDoc (schematic), .PcbDoc (layout), .PrjPcb (project)

### Supported Viewers (Free Alternatives)
- **Altium 365 Viewer** - View designs online without Altium license
- **GerbView/CamtasticViewer** - View Gerber manufacturing files
- **PDF Viewers** - For reports and documentation

---

## Working with the Design

### Opening in Altium Designer
1. Open Altium Designer
2. File → Open Project
3. Select `STM32F4 version1.PrjPcb`
4. View schematic: double-click `version1.SchDoc`
5. View layout: double-click `version1.PcbDoc` (or v2/v3 for other layouts)

### Making Changes
1. Edit schematic (`version1.SchDoc`)
2. Update PCB layout from schematic
3. Run Design Rule Check (Tools → Design Rule Check)
4. Export Gerber files to `Project Outputs` folder
5. Version control: Save and commit changes

### Design Rule Checking
- Run automated DRC before manufacturing
- Review `Design Rule Check - version*.drc` files
- Ensure all electrical rules and manufacturing requirements are met
- Fix any violations before production

---

## Interfacing with DELI_ROBOT

This expansion board provides additional I/O and connectivity for the DELI_ROBOT autonomous delivery platform:

- **Motor Control**: Enhanced PWM and driver circuits
- **Sensor Interfaces**: Headers for encoders, IMU modules, ultrasonic sensors
- **Communication**: Additional CAN, UART, and SPI ports
- **Power Management**: Dedicated supply circuits for motors and sensors
- **Debug Interface**: Enhanced JTAG/SWD debugging connectors

---

## Manufacturing Guidelines

### Before Ordering

1. **Review DRC Reports**: Check all design rule check files
2. **Verify Gerber Files**: 
   - All layers present (GTL, GBL, GKO)
   - Drill files included
3. **Manufacturing Specs**:
   - Trace width: Typically 8-10 mil minimum
   - Via diameter: 0.3-0.5 mm
   - Solder mask clearance: 1-2 mil
4. **Lead Time**: Order 2-3 weeks before needed
5. **Quantity**: Minimum order varies by manufacturer (typically 5-10 pieces)

### Recommended Manufacturers
- **JLCPCB** - Fast turnaround, low cost
- **PCBWay** - Quality focus, various layer options
- **Seeed Studio** - Community-friendly, good documentation
- **OSH Park** - High quality, US-based

---

## Quality Assurance

### Design Verification
- All DRC checks passed (see Design Rule Check files)
- Schematic and layout verified to match
- Electrical rules enforced
- Manufacturing design rules validated

### Testing Recommendations
1. **Visual Inspection**: Check for solder bridges, component placement
2. **Continuity Testing**: Verify all connections are sound
3. **Power Supply Testing**: Measure voltage rails under load
4. **Functionality Testing**: Test all interfaces with DELI_ROBOT firmware
5. **Signal Integrity**: Verify clock and communication signals

---

## Files Reference

| File | Description | Purpose |
|------|-------------|---------|
| `STM32F4 version1.PrjPcb` | Project file | Main project management |
| `version1.SchDoc` | Schematic | Electrical design |
| `version1.PcbDoc` | PCB Layout v1 | First layout iteration |
| `version2.PcbDoc` | PCB Layout v2 | Improved layout |
| `ver3.PcbDoc` | PCB Layout v3 | Final optimized layout |
| `*.GTL, *.GBL` | Gerber files | Manufacturing files |
| `*.TXT` | Drill files | Hole drilling specifications |
| `*.drc` | DRC reports | Design rule check results |

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| DRC violations | Review `Design Rule Check - *.drc` and fix layout |
| Manufacturing issues | Verify Gerber files are properly exported |
| Connection problems | Check schematic routing and PCB traces |
| Power supply issues | Verify decoupling capacitors and ground planes |
| Signal integrity | Check trace routing and via placement |

---

## Version Control & History

- **Schematic**: Maintained in version1.SchDoc
- **Layout Revisions**: v1, v2, v3 PcbDoc files reflect design iterations
- **Change Log**: Review `Project Logs for STM32F4 version1/` for revision history
- **Archive**: `History/` folder contains previous designs

---

## Next Steps

1. **For Prototyping**: Order the PCB using Gerber files from v3 (latest version)
2. **For Modifications**: Open project in Altium Designer and edit accordingly
3. **For Integration**: Connect expansion board to DELI_ROBOT via defined interfaces
4. **For Documentation**: Add custom notes in Altium project properties

---

## Related Documentation

- [DELI_ROBOT Firmware](../Code_F4/Final_Version/DELI_ROBOT/README.md)
- Altium Designer User Guide: https://www.altium.com/documentation
- STM32F407 Datasheet: https://www.st.com/resource/en/datasheet/stm32f407vg.pdf

---

## License & Attribution

This expansion board design complements the DELI_ROBOT autonomous delivery platform.

---

## Notes

- **Latest Version**: Use `ver3.PcbDoc` for manufacturing unless otherwise specified
- **Compatibility**: Designed specifically for STM32F407VGTx with DELI_ROBOT firmware
- **Customization**: All design files are editable in Altium Designer
- **Manufacturing**: Keep manufacturing files organized in dedicated output folder
