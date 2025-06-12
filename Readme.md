# Smart EV Monitor with ESP32, PZEM-004T, OLED, and ThingsBoard

This project is a **Smart Electric Vehicle (EV) Monitor** system that uses an **ESP32** microcontroller, a **PZEM-004T v3.0** energy meter, and an **OLED display**. It measures real-time power consumption and transmits the data to **ThingsBoard** via MQTT. It also displays data on the OLED and prints a "receipt" to the Serial Monitor.

---

## 🛠 Hardware Requirements

* ESP32 Dev Board
* PZEM-004T v3.0 Energy Meter
* Adafruit SSD1306 OLED (128x64, I2C)
* Wi-Fi Access Point (Wokwi or real device)
* Jumper wires, breadboard

---

## 📦 Features

* Live display of voltage, current, and power on OLED
* Periodic energy data publishing to **ThingsBoard**
* Simulated energy tracking using calculated power over time
* "Energy receipt" printout every 5 updates

---

## 📡 Pin Configuration

| Component | ESP32 Pin |
| --------- | --------- |
| PZEM TX   | GPIO 17   |
| PZEM RX   | GPIO 16   |
| OLED SDA  | GPIO 21   |
| OLED SCL  | GPIO 22   |

---

## 🔌 Configuration

Update these values in the code:

```cpp
const char* ssid = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";
const char* access_token = "YOUR_THINGSBOARD_ACCESS_TOKEN";
```

---

## 📥 Installation Guide

### 1. Set Up Arduino IDE

* Download and install [Arduino IDE](https://www.arduino.cc/en/software)
* Install the **ESP32 board package**:

  * File > Preferences > Additional Board URLs:

    ```
    https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
    ```
  * Tools > Board > Boards Manager > Search "ESP32" > Install

### 2. Install Required Libraries

Use Library Manager (`Sketch > Include Library > Manage Libraries`) to install:

* `PZEM004Tv30`
* `PubSubClient`
* `Adafruit_SSD1306`
* `Adafruit_GFX`

### 3. Upload and Run

* Select board: `ESP32 Dev Module`
* Connect ESP32 and select the correct COM port
* Click **Upload**
* Open Serial Monitor at `115200` baud

---

## 📊 Telemetry Sent to ThingsBoard

The following values are sent every 5 seconds:

* `voltage` (V)
* `current` (A)
* `power` (W)
* `energy` (Wh, calculated manually)

---

## 🖥 OLED Display

Live values shown:

* Voltage (V)
* Current (A)
* Power (W)

---

## 🧾 Sample Energy Receipt (Serial Output)

```
=== Energy Receipt ===
Total Energy: 8.42 Wh
Duration: 0.2361 h
Avg Power: 35.67 W
=====================
```

---

## 🧠 Notes

* PZEM004T address defaults to `0x01`, no need to change unless using multiple sensors.
* Energy calculation is based on `Power × Time` due to limited simulation support.
* Ensure ThingsBoard has a device configured with matching access token.

---

## 📎 License

This project is licensed under the MIT License.

---
