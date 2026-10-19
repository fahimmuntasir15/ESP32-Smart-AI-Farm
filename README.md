# ESP32 AI Smart Farm System

An automated agricultural monitoring and control system built with ESP32, FreeRTOS dual-core processing, Adafruit ST7735 TFT display, and Edge Impulse machine learning for crop disease prediction.

---

## Features

- **Telemetry Monitoring**: Real-time tracking of Temperature, Humidity (DHT22), Soil Moisture, Ambient Light (LDR), and Digital pH.
- **Dual-Core Processing (FreeRTOS)**: Core 0 manages Wi-Fi & Telegram background communications; Core 1 handles sensor sampling, AI inference, display rendering, and manual UI navigation.
- **Embedded AI Inference**: Edge Impulse ML model running directly on the ESP32 to evaluate crop disease risks.
- **Remote Telegram Bot Control**: Query real-time telemetry (`/status`) and toggle actuators remotely (`/pump_on`, `/pump_off`, `/fan_on`, `/fan_off`, `/auto_on`, `/auto_off`).
- **Safety & Alerts**: On-screen visual warnings and automated Telegram notifications for High/Low pH, Extreme Temperatures, and AI Disease Alerts.

---

## Hardware Required

- ESP32 Development Board
- ST7735 1.8" SPI TFT Display (128x160 RGB)
- Analog Joystick Module (VRX, VRY, SW)
- DHT22 Temperature & Humidity Sensor
- Soil Moisture Sensor & LDR Module
- 2-Channel Relay Module (Water Pump & Cooling Fan)
- WS2812B RGB LED Ring (7 LEDs) & Passive Buzzer

---

## Pinout & Wiring Map

Connect your hardware components to the ESP32 using the pin assignments below:

| Hardware Component | ESP32 Pin | Function / Description |
| :--- | :--- | :--- |
| **ST7735 TFT CS** | GPIO 5 | Chip Select |
| **ST7735 TFT RST** | GPIO 4 | Reset |
| **ST7735 TFT DC** | GPIO 2 | Data / Command |
| **ST7735 TFT MOSI** | GPIO 23 | SPI Data Line |
| **ST7735 TFT SCLK** | GPIO 18 | SPI Clock Line |
| **Joystick X-Axis (VRX)** | GPIO 34 | Analog X Input |
| **Joystick Y-Axis (VRY)** | GPIO 39 | Analog Y Input |
| **Joystick Switch (SW)** | GPIO 27 | Button Press Input |
| **Water Pump Relay** | GPIO 16 | Relay Control 1 |
| **Cooling Fan Relay** | GPIO 17 | Relay Control 2 |
| **DHT22 Sensor** | GPIO 32 | Temp & Humidity Data |
| **Soil Moisture Sensor** | GPIO 33 | Analog Soil Moisture |
| **LDR Sensor Module** | GPIO 35 | Digital Light Level |
| **WS2812B LED Ring** | GPIO 19 | NeoPixel Data Signal |
| **Passive Buzzer** | GPIO 14 | Acoustic Alert Output |

---

## Step-by-Step Setup Guide

### Step 1: Clone the Repository
Open your terminal or command prompt and clone this repository to your local computer:
```bash
git clone https://github.com/fahimmuntasir15/ESP32-Smart-AI-Farm.git
cd ESP32-Smart-AI-Farm
```

### Step 2: Configure Credentials
1. Make a copy of the template configuration header named `config.h.example` and save it as `config.h`:
   ```bash
   cp config.h.example config.h
   ```
2. Open `config.h` in your text editor.
3. Update the credential definitions with your actual network and bot credentials:
   ```cpp
   #define SECRET_WIFI_SSID "YOUR_WIFI_NAME"
   #define SECRET_WIFI_PASS "YOUR_WIFI_PASSWORD"
   #define SECRET_BOT_TOKEN "YOUR_TELEGRAM_BOT_TOKEN"
   #define SECRET_CHAT_ID   "YOUR_TELEGRAM_CHAT_ID"
   ```

### Step 3: Install Required Libraries in Arduino IDE
Open Arduino IDE, go to Library Manager (**Ctrl + Shift + I**), and install the following dependencies:

- Adafruit GFX Library
- Adafruit ST7735 and ST7789 Library
- DHT sensor library
- Adafruit NeoPixel
- UniversalTelegramBot
- ArduinoJson

### Step 4: Upload Code to ESP32
1. Connect your ESP32 board to your computer via USB.
2. Open `ESP32_Smart_AI_Farm.ino` in Arduino IDE.
3. Select **ESP32 Dev Module** under **Tools $\rightarrow$ Board**.
4. Choose the correct COM port under **Tools $\rightarrow$ Port**.
5. Click **Upload** ($\rightarrow$) to flash the program.