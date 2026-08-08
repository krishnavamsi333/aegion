# Aegion — Requirements v1.0

## 1. Purpose

Aegion is an industrial I/O controller designed for machine
automation, industrial equipment, and robotics infrastructure.

The controller provides protected 24 V field I/O, analog signal
acquisition, industrial communication, diagnostics, and real-time
control.

## 2. Target Applications

- Industrial machinery
- Automation equipment
- Distributed I/O systems
- Robotics infrastructure
- Embedded machine controllers

## 3. Power

- Nominal supply: 24 V DC
- Operating range: 9–32 V DC
- Reverse-polarity protection
- Input transient protection
- Protected field-power domain
- Separate logic and field-power domains
- Power architecture shall support the defined worst-case I/O load

## 4. Digital Inputs

- 8 × 24 V digital inputs
- Field-side protection
- Defined ON/OFF thresholds
- Input diagnostics
- Protection against common field wiring faults

## 5. Digital Outputs

- 8 × high-side/source outputs
- 24 V field-side operation
- 0.5 A continuous target per channel
- Target capability: 8 channels operating simultaneously at 0.5 A,
  subject to thermal validation
- Individual short-circuit protection
- Current/thermal protection
- Output fault diagnostics
- Defined safe state during MCU reset and watchdog failure

## 6. Analog Inputs

- 4 × analog input channels
- Each channel shall support:
  - 0–10 V input
  - 4–20 mA input
- 16-bit measurement path
- Input protection
- Input filtering
- Defined measurement accuracy
- Per-channel configuration between voltage and current modes

## 7. CAN-FD

- 1 × CAN-FD interface
- Backward compatibility with Classic CAN
- Galvanic isolation from the logic domain
- Field-side ESD/transient protection
- Serviceable field connector
- Configurable node identification

## 8. RS-485

- 1 × half-duplex RS-485 interface
- Galvanic isolation from the logic domain
- Field-side ESD/transient protection
- 120 ohm termination selectable
- Bus biasing selectable
- Serviceable field connector

## 9. Processing

- STM32G4-family microcontroller
- Integrated FDCAN peripheral
- Real-time I/O processing
- Hardware watchdog
- Non-volatile configuration storage
- Fault detection and diagnostics

## 10. Isolation

The design shall provide galvanic isolation between the logic domain
and external communication/field domains where practical.

The final isolation boundaries shall be defined during system
architecture.

## 11. Diagnostics

The controller shall provide diagnostics for:

- Input power status
- Logic power status
- Digital input state
- Digital output state
- Output faults
- Analog input status
- CAN communication
- RS-485 communication
- MCU reset/watchdog faults

## 12. Connectors

- Pluggable terminal blocks
- Initial target pitch: 3.5 mm or 5.08 mm
- Connector selection shall consider current rating, wiring space,
  serviceability, and PCB area

## 13. PCB

- Designed using KiCad
- Initial target size: approximately 100 × 80 mm
- 2- or 4-layer PCB
- Clear separation between field and logic circuitry
- Accessible test points
- Design for automated assembly
- Design for manufacturing and inspection

## 14. EMC and Protection

The design shall use industrial-oriented protection including:

- Reverse-polarity protection
- TVS/transient protection
- ESD protection
- EFT-oriented protection
- Surge-oriented protection where applicable
- Appropriate filtering and grounding strategy

Protection requirements shall be refined during the electrical
architecture and PCB layout phases.

## 15. Environmental Target

Initial design target:

- Industrial equipment environment
- Operating temperature: -20 °C to +70 °C
- No conformal coating assumed
- Final environmental requirements to be defined

## 16. Safety and Fault Behavior

The design shall define a deterministic safe state for:

- MCU reset
- Watchdog timeout
- Loss of logic power
- Communication failure
- Digital-output fault
- Field-power fault

## 17. Manufacturing

The design shall support:

- Standard PCB fabrication
- Automated assembly
- Test-point access
- Component availability
- Design-for-manufacturing review
- Electrical test and functional test

## 18. Validation

The prototype shall be validated for:

- Power input behavior
- Reverse-polarity protection
- Transient protection
- Digital input thresholds
- Digital output operation
- Output current capability
- Output fault behavior
- Analog input accuracy
- 0–10 V measurement
- 4–20 mA measurement
- CAN-FD communication
- Classic CAN communication
- RS-485 communication
- Isolation integrity
- MCU reset/watchdog behavior
- Thermal behavior

## 19. Status

Requirements: v1.0 Draft

Architecture: Not started

Schematic: Not started

PCB: Not started

Prototype: Not started

Validation: Not started
