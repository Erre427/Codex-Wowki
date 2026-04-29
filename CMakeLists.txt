cmake_minimum_required(VERSION 3.13)

project(pico_w_7segment_pio C CXX ASM)

# This repository is documentation-focused and keeps original logic in src/main.cpp.
# The provided source uses Arduino-style setup()/loop() with RP2040 PIO APIs.
# Build with the Arduino Pico core in Wokwi or Arduino IDE for a runnable target.

add_custom_target(${PROJECT_NAME}_docs ALL
  COMMENT "Documentation-only CMake target; firmware build is handled by Arduino Pico toolchain"
)
