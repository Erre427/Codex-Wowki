# Wiring (Raspberry Pi Pico W + 4-Digit 7-Segment Display)

## Components
Derived from `diagram.json`:

1. Raspberry Pi Pico (Wokwi part: `wokwi-pi-pico`, configured with `arduino-community` environment)
2. 4-digit 7-segment display (Wokwi part: `wokwi-7segment`, `digits=4`)
3. Serial monitor connection (virtual UART in Wokwi)

## GPIO Mapping

### UART (debug/monitor)
| Function | Pico pin | Notes |
|---|---|---|
| UART TX | GP0 | Connected to Wokwi Serial Monitor RX |
| UART RX | GP1 | Connected to Wokwi Serial Monitor TX |

### Segment lines
`first_segment_pin = GP2`, so contiguous segment mapping is used:

| 7-segment pin | Pico GPIO |
|---|---|
| A | GP2 |
| B | GP3 |
| C | GP4 |
| D | GP5 |
| E | GP6 |
| F | GP7 |
| G | GP8 |
| DP | GP9 |

### Digit select lines
`first_digit_pin = GP10`, so contiguous digit mapping is used:

| Digit select pin | Pico GPIO |
|---|---|
| DIG1 | GP10 |
| DIG2 | GP11 |
| DIG3 | GP12 |
| DIG4 | GP13 |

## Notes on Drive Method
- The design uses multiplexing (4 digits share segment lines).
- Refresh/output timing is offloaded to RP2040 PIO (via `segment_program`).
- No external display driver IC is used in this topology.

## Real Hardware Considerations
- Add current-limiting resistors for segment lines when moving from simulation to physical hardware.
- Verify display type/common pin polarity matches the bit patterns in firmware.
- Ensure 3.3V logic compatibility.
