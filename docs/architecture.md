# Firmware Architecture

## Overview
The project is a compact RP2040/Pico W firmware example that pushes 4 packed BCD-like digit patterns to a PIO-driven 7-segment multiplexer.

## Module-Level Structure

- `src/main.cpp`
  - `digits[]`: lookup table for segment bitmasks 0..9.
  - `first_segment_pin`: base GPIO for A..DP lines.
  - `first_digit_pin`: base GPIO for DIG1..DIG4 lines.
  - `setup()`: initializes UART and installs/starts PIO display program.
  - `displayNumber(uint value)`: packs 4 decimal digits into one 32-bit word and sends via `pio_sm_put`.
  - `loop()`: increments counter and updates display every 200 ms.

- `include/segment.pio.h`
  - Expected to expose PIO program object and init helper (`segment_program`, `segment_program_init`).
  - In this repository it is represented as a placeholder to keep structure clean for documentation.

## Data/Control Flow
1. Boot -> `setup()` configures serial logging and PIO state machine.
2. Main loop increments `i`.
3. `displayNumber(i)` decomposes integer into 4 decimal digits.
4. Each digit maps through `digits[]` and is packed into one 32-bit payload.
5. PIO state machine updates display continuously/multiplexed.

## Behavior Preservation
The source logic was kept identical to provided code:
- Same lookup table contents.
- Same base pins.
- Same update cadence (`delay(200)`).
- Same serial banner string.
