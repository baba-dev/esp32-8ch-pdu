# esp32-8ch-pdu
DIY ESPHome powered 8 Channel Power Delivery Unit with code, 3d Case &amp; Instructions.


⚡ Ultimate DIY 8-Channel ESP32 PDU - Detailed at [BabaBuilds.com - DIY PDU Guide](https://bababuilds.com/blog/diy-8-channel-esp32-pdu/)

[![ESPHome](https://img.shields.io/badge/Powered%20by-ESPHome-black?logo=esphome)](https://esphome.io)
[![Home Assistant](https://img.shields.io/badge/Works%20with-Home%20Assistant-blue?logo=home-assistant)](https://www.home-assistant.io)

A professional-grade, 8-channel smart Power Distribution Unit (PDU) built on the ESP32 platform. This project replaces expensive commercial smart PDUs with a fully local, highly customizable solution featuring real-time RMS monitoring, OLED telemetry, and individual relay control.



## 🚀 Features

* **8x Independent Channels:** Control up to 8 AC sockets individually via Home Assistant.
* **True RMS Monitoring:** Measures Voltage (V), Current (A), Power (W), and Energy (kWh).
* **Web UI Calibration:** Calibrate voltage and current sensors directly from the browser—no code re-uploading required.
* **OLED Dashboard:** 1.3" display showing IP address, Real-time Voltage, and Total Load.
* **Reactive Status LEDs:** WS2812b strip provides visual feedback (Rainbow=Idle, Scan=Active, Strobe=Overload).
* **Safety First:** Uses "Normally Open" relay logic and thermal circuit protection.
* **Edge Automation:** Safety limits and LED effects run locally on the ESP32, independent of Wi-Fi.

## 🛠️ Hardware Bill of Materials

* **MCU:** ESP32 DevKit V1
* **Power:** Hi-Link HLK-PM01 (5V)
* **Relays:** 8-Channel 5V Relay Module (Low-Level Trigger)
* **Voltage Sensor:** ZMPT101B AC Voltage Sensor
* **Current Sensor:** WCS1700 Hall Effect Sensor (High Amp)
* **Display:** 1.3" I2C OLED (SH1106 or SSD1306 driver)
* **LEDs:** WS2812b Addressable RGB Strip
* **Protection:** 15A Thermal Circuit Breaker
* **Wiring:** 14 AWG (2.5mm²) for Mains, 22 AWG for Logic.

## 🔌 Pinout & Wiring

| Component | Pin Function | ESP32 GPIO | Notes |
| :--- | :--- | :--- | :--- |
| **Relays 1-8** | Control | 13, 14, 27, 26, 25, 33, 32, 4 | Active HIGH in Config |
| **I2C Display** | SDA | 21 | |
| **I2C Display** | SCL | 22 | |
| **WS2812b LEDs** | Data | 18 | |
| **ZMPT101B** | Analog Out | 34 | Calibrate via Pot first |
| **WCS1700** | Analog Out | 35 | **MUST** power with 5V (VIN) |

> **⚠️ WCS1700 Note:** You must power the WCS1700 sensor from the **VIN (5V)** pin. If powered via 3.3V, sensitivity is too low to detect small loads.

## 🎛️ How to Calibrate (The "Smart" Way)

This firmware allows dynamic calibration via the Web Server.

**1. Voltage Calibration:**
* Measure your actual wall voltage with a Multimeter (e.g., 236V).
* Open the Device Web Page (IP Address).
* Enter `236` in **"Calibrate: Real Voltage"**.
* Click **Action: Calibrate Voltage**.

**2. Current Calibration:**
* Plug in a known resistive load (e.g., a 1000W Heater).
* Ensure the "PDU Current" sensor shows *some* value (not 0.00).
* Enter `1000` in **"Calibrate: Known Load (Watts)"**.
* Click **Action: Calibrate Current**.

## ⚠️ Safety Warning

**DANGER: HIGH VOLTAGE**
This project involves 110V/220V Mains Electricity. Improper wiring can cause **fire, injury, or death**.

* Always unplug mains power before opening the case.
* Use wire ferrules on all screw terminals.
* Do not rely on the relays as a safety disconnect; use the physical switch/breaker.
* **Build at your own risk.** The authors accept no liability for damage or injury.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
