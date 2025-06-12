Great! Here's your **GitHub-friendly README** with **badges**, **sections**, and clear formatting. You can copy and paste this directly into a `README.md` file in your GitHub repository.

---

````markdown
# ⚡ Smart EV Monitor with ESP32, PZEM-004T, OLED & ThingsBoard

[![Platform](https://img.shields.io/badge/platform-ESP32-blue.svg)](https://www.espressif.com/en/products/socs/esp32)
[![Display](https://img.shields.io/badge/display-OLED-ff69b4.svg)](https://learn.adafruit.com/monochrome-oled-breakouts)
[![ThingsBoard](https://img.shields.io/badge/cloud-ThingsBoard-orange.svg)](https://thingsboard.io)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://opensource.org/licenses/MIT)

A Smart Electric Vehicle (EV) energy monitor built with ESP32 and PZEM-004T that transmits real-time power data to **ThingsBoard** via MQTT and displays data on an **OLED screen**.

---

## 📦 Features

- 📉 Real-time voltage, current, power monitoring  
- 🌐 MQTT telemetry to ThingsBoard cloud  
- 📺 OLED display of live readings  
- 🧾 Serial "Energy Receipt" every 5 updates  
- ⚙️ Manual energy calculation for simulated environments (like Wokwi)

---

## 🔧 Hardware Requirements

| Component         | Description                        |
|------------------|------------------------------------|
| ESP32 Dev Board  | Wi-Fi + Serial capabilities        |
| PZEM-004T v3.0   | Voltage/Current/Energy sensor      |
| OLED Display     | SSD1306 128x64 I2C OLED            |
| Wires + Breadboard | For connections and prototyping  |

---

## 🔌 Pin Configuration

| Device  | ESP32 Pin |
|---------|-----------|
| PZEM RX | GPIO 16   |
| PZEM TX | GPIO 17   |
| OLED SDA | GPIO 21 |
| OLED SCL | GPIO 22 |

---

## 🚀 Getting Started

### 1️⃣ Install Arduino IDE

- 📥 Download: https://www.arduino.cc/en/software  
- 📦 Add ESP32 Board URL:  
  `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`  
  - Go to File > Preferences > Paste URL into "Additional Board URLs"
  - Then Tools > Board > Board Manager > Search and install **ESP32**

### 2️⃣ Install Required Libraries

Install these via **Library Manager** (Sketch > Include Library > Manage Libraries):

- [`PZEM004Tv30`](https://github.com/olehs/PZEM004T-v30)
- [`Adafruit_SSD1306`](https://github.com/adafruit/Adafruit_SSD1306)
- [`Adafruit_GFX`](https://github.com/adafruit/Adafruit-GFX-Library)
- [`PubSubClient`](https://github.com/knolleary/pubsubclient)

### 3️⃣ Configure Your Code

Edit these lines:

```cpp
const char* ssid = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";
const char* access_token = "YOUR_THINGSBOARD_ACCESS_TOKEN";
````

### 4️⃣ Upload & Monitor

* Select Board: **ESP32 Dev Module**
* Connect USB and select the correct COM port
* Click **Upload**
* Open **Serial Monitor** at **115200 baud**

---

## 📡 Telemetry Format (MQTT)

Published to: `v1/devices/me/telemetry`

```json
{
  "voltage": 229.1,
  "current": 1.55,
  "power": 355.0,
  "energy": 8.42
}
```

---

## 🖥 OLED Display Output

```
Smart EV Monitor
V: 229.1 V
I: 1.55 A
P: 355.0 W
```

---

## 🧾 Serial Energy Receipt

Printed every 5 readings (\~25 seconds):

```
=== Energy Receipt ===
Total Energy: 8.42 Wh
Duration: 0.2361 h
Avg Power: 35.67 W
=====================
```

---

## 🧠 Notes

* ⚠️ Energy value is **calculated manually** as `Power × Time` to support simulation tools like **Wokwi**
* Make sure you **create a device on ThingsBoard** and use the matching access token
* Real PZEM sensors will give `.energy()` values directly

---

## 📜 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

---