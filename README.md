# AeroJudge PCB Redesign - Board Consolidation Project

**Goal:** Merge two existing boards plus three sub-modules into a single Raspberry Pi 4 HAT for streamlined production.

This project consolidates a multi-board assembly into one functional HAT PCB suitable for commercial manufacturing (JLCPCB-A or similar).

## Project Overview

Currently, the AeroJudge system consists of:
- Main board (primary interface and controls)
- Power board with three mounted sub-modules
- Multiple interconnecting cables

**Target:** Single PCB design with all functionality integrated, ready for automated assembly.

## Files Included

- `Main_Board.kicad_pcb` / `Main_Board.kicad_sch` - Primary interface board
- `Power_Board.kicad_pcb` / `Power_Board.kicad_sch` - Power management board
- `Pololu_2810_Circuit.pdf` - Circuit diagram for power switch implementation
- Sub-board reference links and datasheets (see below)

## Main Board Changes

**Components to Remove:**
- ENC 1 (keep ENC2 only)
- GPIO16, GPIO12, GPIO23, GPIO18
- All I2C connectors except I2C-1 (which will be integrated on-board)
- Backside pads for poweroff select and shutdown select (replace with direct traces to GPIO24 and GPIO25)

## Power Board Integration

The power board currently uses three separate sub-modules that must be integrated directly onto the main PCB:

### 1. INA226 Current/Voltage Sensor
- Reference module: https://www.aliexpress.us/item/3256806274363321.html
- Function: Battery monitoring
- Designer should integrate equivalent circuit based on INA226 datasheet

### 2. Pololu 2810 Power Switch
- Circuit diagram provided: `Pololu_2810_Circuit.pdf`
- Use this circuit diagram to integrate switch functionality onto main board
- No pre-made module needed

### 3. Voltage Regulator (Requires Redesign)
- Current setup uses manual voltage adjustment (not optimal)
- **Requirements:** 5.1V DC output, 3+ Amp capability for Raspberry Pi 4
- **Options:**
  - Clone Pololu 4892 circuit (5V, 3.4A Step-Down Voltage Regulator D30V30F)
  - Design equivalent buck converter circuit
  - Designer should recommend specific components/circuit

**Power Input:**
- Replace current battery solder pads with appropriate DC power connector/plug
- Specify connector type in design

**Connectors Being Eliminated:**
All external connectors between boards become internal traces:
- I2C connectors
- Power/shutoff connectors  
- 5V battery connector

## Additional Requirements

### LED Connector
- Duplicate existing LED connector
- Add second connector for 3.3V LED operation
- Designer should specify connector types

### Physical Constraints
- Base on Raspberry Pi 4 HAT form factor (can be larger if needed - provide size recommendations)
- **Connector height limit:** Approximately 5mm (90-degree connectors required for case clearance)
- Components can be on both sides of board
- **Avoid placing connectors on bottom side** (HAT clearance requirements)
- Existing case can be redesigned if necessary, but prefer to work within current constraints

### Board Markings
- Front: AeroJudge logo, website link, "Board Rev 3.0"
- Rear: IMAC logo (if space permits, not critical)

## Deliverables Expected

1. Complete KiCad project files (schematics + PCB layout)
2. Manufacturing-ready Gerber files
3. Bill of Materials (BOM) with specific part numbers
4. Assembly drawing/notes
5. Board size recommendations based on component layout

## Design Notes

- Target manufacturer: JLCPCB-A or similar automated assembly service
- All sub-assemblies must be eliminated - single PCB only
- Maintain all existing functionality from current two-board system
- Designer should flag any potential issues with integration approach

## Questions for Designer

Before starting, please confirm:
1. Are the provided sub-board references sufficient, or do you need additional datasheets?
2. What board dimensions do you recommend based on component density?
3. Any concerns about the voltage regulator redesign requirements?
4. Estimated component cost impact vs. current design?

## Contact

For questions or clarifications during design process, please open an issue in this repository.
