# SPI Accelerometer Interface

This project demonstrates SPI communication using the STM32L4 Nucleo board to interface with the ADXL345 accelerometer. The system reads acceleration values on all three axes (X, Y, Z) and sends the results over UART to a PC terminal.

## Features
- SPI communication using SPI1 peripheral
- Initialization and configuration of ADXL345 accelerometer
- Reading real-time X, Y, Z axis acceleration
- Full-resolution mode (10-bit scale with fixed sensitivity)
- Output streamed to UART for monitoring

## Usage

1. Connect ADXL345 Accelerometer to STM32:

| Accelerometer Pin | STM32 Pin | Function        |
|-------------------|-----------|-----------------|
| CS                | PA4       | SPI1_NSS        |
| SCL               | PB3       | SPI1_SCK        |
| SDA               | PB5       | SPI1_MOSI       |
| SDO               | PB4       | SPI1_MISO       |
| VCC               | 3.3V      | Power           |
| GND               | GND       | Ground          |

2. Configuration Settings:
   - SPI Mode: CPOL = 1, CPHA = 1 (Mode 3)
   - Frame Format: 16-bit
   - Baud Prescaler: /16
   - Full-Duplex, MSB First
   - SysTick Timer: 1 ms interrupt for delay function

3. Accelerometer Setup:
   - Output Data Rate: 100 Hz
   - Full-Resolution Mode
   - Measurement Mode Enabled

4. Run the Program:
   - STM32 reads acceleration values from ADXL345 registers
   - Converts raw values to acceleration in g (using scale factor from datasheet)
   - Sends formatted output via UART to Termite or another terminal
