# Aegion — Interface Definition v0.1

## 1. MCU

Target MCU family:

- STM32G4
- 3.3 V logic
- Integrated FDCAN
- Sufficient GPIO for all field I/O and diagnostics
- SWD programming/debug interface

The exact MCU part shall be selected after the complete I/O budget
is reviewed.

## 2. Digital Inputs

8 × 24 V digital inputs.

| Signal | MCU Resource | Direction |
|---|---|---|
| DI1 | GPIO | Input |
| DI2 | GPIO | Input |
| DI3 | GPIO | Input |
| DI4 | GPIO | Input |
| DI5 | GPIO | Input |
| DI6 | GPIO | Input |
| DI7 | GPIO | Input |
| DI8 | GPIO | Input |

Requirements:

- 24 V field-side conditioning
- Protected input
- Defined logic threshold
- Optional input filtering/debounce

## 3. Digital Outputs

8 × high-side 24 V outputs.

| Signal | MCU Resource | Direction |
|---|---|---|
| DO1 | GPIO | Output |
| DO2 | GPIO | Output |
| DO3 | GPIO | Output |
| DO4 | GPIO | Output |
| DO5 | GPIO | Output |
| DO6 | GPIO | Output |
| DO7 | GPIO | Output |
| DO8 | GPIO | Output |

The high-side driver shall provide the actual field-side switching.

Where supported, driver diagnostics shall return to the MCU.

## 4. Analog Inputs

4 × configurable analog channels.

| Signal | Function |
|---|---|
| AI1 | 0–10 V / 4–20 mA |
| AI2 | 0–10 V / 4–20 mA |
| AI3 | 0–10 V / 4–20 mA |
| AI4 | 0–10 V / 4–20 mA |

Target:

- 16-bit measurement path
- Protected input
- Filtering
- Calibration capability

The final ADC architecture may use the STM32G4 ADC or an external
precision ADC depending on accuracy, isolation, noise, and channel
requirements.

## 5. CAN-FD

One CAN-FD interface.

| Signal | Function |
|---|---|
| CAN_TX | MCU → transceiver |
| CAN_RX | transceiver → MCU |

The STM32G4 FDCAN peripheral shall be used.

The CAN physical layer shall be isolated and protected.

## 6. RS-485

One half-duplex RS-485 interface.

| Signal | Function |
|---|---|
| RS485_TX | MCU → transceiver |
| RS485_RX | transceiver → MCU |
| RS485_DE | Driver enable |
| RS485_RE | Receiver enable |

The final design may combine DE/RE where supported by the selected
transceiver.

The physical layer shall be isolated and protected.

## 7. Debug Interface

SWD shall be provided.

| Signal | Function |
|---|---|
| SWDIO | Programming/debug |
| SWCLK | Programming/debug |
| NRST | MCU reset |
| 3V3 | Reference |
| GND | Reference |

## 8. Status Indicators

Minimum:

- Power LED
- MCU status LED
- CAN status LED
- RS-485 status LED
- Fault LED

Additional channel indicators shall be evaluated against PCB area
and power consumption.

## 9. Monitoring

The MCU shall monitor important internal rails.

Target signals:

- VIN / field supply
- 5 V rail
- 3.3 V rail
- Output-driver fault signals
- Relevant temperature signals

## 10. Non-Volatile Storage

Provide non-volatile storage for:

- Device configuration
- Calibration constants
- Node identification
- Persistent fault information where useful

The exact memory device shall be selected during component selection.

## 11. Clock

The MCU clock architecture shall support:

- Accurate real-time operation
- CAN-FD timing requirements
- Reliable firmware execution

External crystal/oscillator requirements shall be determined from
the selected STM32G4 device and communication timing requirements.

## 12. Reset and Safety

The MCU shall have:

- Hardware reset
- Independent watchdog
- Brown-out/reset supervision
- Deterministic output state during reset

Digital outputs shall default to a safe OFF state during:

- MCU startup
- MCU reset
- Watchdog reset
- Loss of firmware control

## 13. Preliminary GPIO Budget

Minimum direct MCU signals:

```text
Digital inputs       8
Digital outputs      8
Analog inputs        4
CAN                  2
RS-485               3–4
SWD                  3
Status LEDs          4–5
Fault/monitoring     4+
--------------------------------
Minimum              ~36–38 signals
