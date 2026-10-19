# ESP32 AI Smart Farm System

An automated agricultural monitoring and control system built with ESP32, FreeRTOS dual-core processing, Adafruit ST7735 TFT display, and Edge Impulse machine learning for crop disease prediction.

## Features
- **Telemetry Monitoring**: Real-time tracking of Temperature, Humidity, Soil Moisture, Ambient Light, and Digital pH.
- **Dual-Core Processing (FreeRTOS)**: Core 0 manages Wi-Fi & Telegram background communications; Core 1 handles sensor sampling, AI inference, and display rendering.
- **Embedded AI Inference**: Edge Impulse ML model running directly on the ESP32 to evaluate crop disease risks.
- **Remote Telegram Bot Control**: Query telemetry (`/status`) and toggle actuators (`/pump_on`, `/pump_off`, `/auto_on`, `/auto_off`).
- **Safety & Alerts**: On-screen visual warnings and automated Telegram notifications for High/Low pH, Extreme Temperatures, and AI Disease Alerts.

## Hardware Required
- ESP32 Development Board
- ST7735 1.8" SPI TFT Display (128x160)
- Analog Joystick Module (VRX, VRY, SW)
- DHT22 Temperature & Humidity Sensor
- Soil Moisture Sensor & LDR Module
- 2-Channel Relay Module (Water Pump & Cooling Fan)
- WS2812B RGB LED Ring (7 LEDs) & Passive Buzzer

## Setup Instructions

1. **Clone the Repository**: