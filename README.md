# Pico W PIO 4-Digit 7-Segment Example

Documentation-first repository for a Raspberry Pi Pico W / RP2040 project that drives a 4-digit 7-segment display using PIO-based multiplexing.

## Features
- RP2040 PIO-assisted 7-segment multiplexing
- 4-digit decimal counter display (incrementing)
- UART serial banner output on startup
- Wiring and architecture docs included

## Repository Layout

- `src/main.cpp` — original firmware logic (preserved)
- `include/segment.pio.h` — placeholder contract for PIO-generated header
- `docs/wiring.md` — wiring map, components, GPIO usage
- `docs/architecture.md` — code/module breakdown and data flow
- `CMakeLists.txt` — minimal documentation-oriented CMake scaffold

## Hardware Components
- Raspberry Pi Pico / Pico W (RP2040)
- 4-digit 7-segment display (A, B, C, D, E, F, G, DP, DIG1..DIG4)
- Jumper wires
- (Recommended for real hardware) current-limiting resistors

## Pin Mapping (Pico)

| Signal | GPIO |
|---|---|
| A..DP | GP2..GP9 |
| DIG1..DIG4 | GP10..GP13 |
| UART TX | GP0 |
| UART RX | GP1 |

## Run in Wokwi
1. Create/import a Raspberry Pi Pico project in Wokwi using Arduino community core.
2. Place `src/main.cpp` logic as the sketch source.
3. Use the provided `diagram.json` wiring (or mirror `docs/wiring.md`).
4. Start simulation and open Serial Monitor.
5. Expect startup message and incrementing 4-digit output.

## Run on Real Hardware
1. Open project with Arduino IDE / Arduino CLI using an RP2040 Arduino core.
2. Ensure your PIO helper/header (`segment.pio.h`) is present exactly as expected by the code.
3. Select board: **Raspberry Pi Pico W**.
4. Build and flash.
5. Connect display per `docs/wiring.md` and verify counting output.

## Wi-Fi Notes
- This firmware does **not** use Wi-Fi.
- If you add Wi-Fi later, keep credentials outside source control (e.g., local config header or build-time defines).

## Behavior Constraints
This repository intentionally preserves the provided main firmware behavior and focuses on structure + documentation.
