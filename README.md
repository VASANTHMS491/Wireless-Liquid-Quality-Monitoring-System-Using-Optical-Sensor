<div align="center">

# 💧 Wireless Liquid Quality Monitoring System

### Real-Time Optical Turbidity Monitoring & Wireless Alerts

[![ESP32](https://img.shields.io/badge/ESP32-Dev%20Module-blue?style=flat-square\&logo=espressif)](https://www.espressif.com/)
[![Arduino](https://img.shields.io/badge/Arduino-IDE-00979D?style=flat-square\&logo=arduino)](https://www.arduino.cc/)
[![LabVIEW](https://img.shields.io/badge/LabVIEW-NI-orange?style=flat-square)](https://www.ni.com/en/shop/labview.html)
[![Sensor](https://img.shields.io/badge/Sensor-SEN0189-green?style=flat-square)](https://www.dfrobot.com/)
[![License](https://img.shields.io/badge/License-MIT-brightgreen?style=flat-square)](LICENSE)

*An ESP32-based wireless liquid quality monitoring system that detects water contamination using an optical turbidity sensor (SEN0189) and provides real-time wireless alerts with LabVIEW visualization.*

</div>

---

## 📖 Table of Contents

* [Features](#-features)
* [Hardware Used](#-hardware-used)
* [Software Requirements](#-software-requirements)
* [Pin Connections](#-pin-connections-wiring-scheme)
* [Working Principle](#-working-principle)
* [Installation & Running](#-installation--running-the-project)
* [Troubleshooting](#-troubleshooting)
* [Project Structure](#-project-structure)

---

## ✨ Features

| Feature                            | Description                                                        |
| ---------------------------------- | ------------------------------------------------------------------ |
| 🔴 **Real-Time Monitoring**        | Continuously monitors turbidity levels in liquid samples           |
| 💡 **Optical Turbidity Detection** | Uses the Tyndall Effect to detect suspended particles              |
| 🚨 **Threshold-Based Alerts**      | Sends warning notifications when contamination exceeds safe limits |
| 📡 **Wireless Communication**      | ESP32 transmits turbidity data wirelessly                          |
| 💰 **Low-Cost Design**             | Built using affordable and easily available components             |
| ⚡ **Continuous Detection**         | Instantly detects contamination without manual testing             |

---

## 🔧 Hardware Used

1. ESP32 Dev Module
2. SEN0189 Turbidity Sensor
3. Breadboard
4. Jumper Wires
5. USB Cable
6. Monitoring Device (Phone/PC)

---

## 💻 Software Requirements

1. **Arduino IDE**
2. **LabVIEW**
3. **ESP32 Board Package**

### Required Libraries

| Library       | Purpose                                |
| ------------- | -------------------------------------- |
| `WiFi.h`      | Wireless communication                 |
| `Arduino ADC` | Reading analog turbidity values        |
| `LabVIEW VI`  | Prototype and simulation               |

---

## 📌 Pin Connections (Wiring Scheme)

### Turbidity Sensor to ESP32

| Sensor Pin | ESP32 Pin | Purpose                         |
| ---------- | --------- | ------------------------------- |
| VCC        | 3.3V / 5V | Power Supply                    |
| GND        | GND       | Common Ground                   |
| AOUT       | Resistor  | To Step down the sensor voltage | 
| Resistor   | GPIO34    | Analog Turbidity Output         |

### Wiring Diagram

```text
  +------------------------------+
  |     Turbidity Sensor         |
  |        (SEN0189)             |
  |                              |
  |  VCC  ───────── 3.3V/5V ─────┐
  |  GND  ───────── GND ─────────┤
  |  AOUT ───────── Resistor ────┤
  | Resistor ──────GPIO34────────|
  +------------------------------+
                                 |
                    +------------+-------+
                    |         ESP32      |
                    |                    |
                    |  VIN  ── Power     |
                    |  GND  ── Common    |
                    +--------------------+
```

> ⚠️ All components must share a **common ground** for stable ADC readings.

---

## 💡 Working Principle

The system uses the **Tyndall Effect** to measure liquid turbidity.

* A light source inside the **SEN0189 sensor** passes through the liquid.
* Suspended particles scatter the light.
* The sensor converts the scattered light intensity into an **analog voltage**.
* The ESP32 reads this voltage through **GPIO34 (ADC pin)**.
* If the turbidity exceeds a predefined threshold:

  * A contamination alert is triggered 📱
  * Data is transmitted wirelessly and continuously updates every 2 seconds
  * The status is displayed in a webpage

### Turbidity Behavior

| Water Quality      | Sensor Voltage |
| ------------------ | -------------- |
| Clean Water        | Higher Voltage |
| Contaminated Water | Lower Voltage  |

> 💡 Depending on sensor orientation and calibration, voltage response may vary slightly.

---

## 🚀 Installation & Running the Project

### Step 1 — Upload ESP32 Code

1. Open the **Arduino IDE**.
2. Connect the **ESP32 board** to your PC using a USB cable.
3. Select the correct **board** and **COM port** from:

   * `Tools → Board`
   * `Tools → Port`
4. Open the Arduino sketch (`turbidity_monitor.ino`).
5. Click **Upload** to flash the code.

> ⚠️ Ensure the SEN0189 sensor is connected to **GPIO34** before testing.

---

### Step 2 — Connect the Turbidity Sensor

Make the following connections:

```text
Sensor VCC   →  3.3V or 5V
Sensor GND   →  GND
Sensor AOUT  →  Resistor
Resistor     → GPIO34
```

> ⚠️ Incorrect grounding may cause unstable sensor readings.

---

### Step 3 — Power the System

Power options:

* USB connection from PC

Verify that the ESP32 powers on successfully.

---

### Step 4 — Run the LabVIEW Prototype Simulation

1. Open the provided **LabVIEW VI file**.
2. Start the simulation prototype.
3. Adjust the simulated turbidity input using:

   * Virtual controls inside LabVIEW
   * Potentiometer input during testing (optional)
4. Observe:

   * Simulated turbidity voltage
   * Water quality status
   * Alert indication behavior

> ⚠️ The LabVIEW interface is used as a **simulation prototype and visualization tool**, not as the primary sensing hardware.

### Step 5 — Monitor the Output

* ESP32 continuously reads turbidity values.
* The value is compared with a threshold.
* If contamination exceeds the threshold:

  * Warning alert is triggered 🚨
  * Data is transmitted wirelessly 📡
  * Webpage displays updated status 🖥️

---

## 📝 Notes & Tips

> 💡 Tips

* Use a **stable power supply** to reduce ADC noise.
* Avoid strong ambient light directly hitting the sensor.
* GPIO34 is recommended because it is an **ADC-capable input pin**.
* A potentiometer can simulate sensor output during testing.
* Sensor calibration improves accuracy for different liquids.

---

## 🛠️ Troubleshooting

### Sensor Not Giving Proper Readings

* Verify **AOUT → GPIO34** connection.
* Check VCC and GND wiring.
* Ensure the sensor is properly immersed/aligned.

---

### Noisy or Unstable Readings

* Use a regulated power supply.
* Reduce ambient light interference.
* Check for loose jumper connections.

---

### ESP32 Not Detected in Arduino IDE

Install the ESP32 board package:

```text
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
```

Then:

1. Open `Tools → Board → Boards Manager`
2. Search for **ESP32**
3. Install the package
4. Select the correct COM port

> ⚠️ Some USB cables are power-only and do not support data transfer.

---

## 📁 Project Structure

```text
wireless-liquid-quality-monitor/
│
├── Arduino_Code/
│   └── turbidity_monitor.ino
│
├── LabVIEW/
│   └── labview_simulation.vi
│
├── Images/
│   ├── wiring_diagram.png
│   └── setup_photo.jpg
│
├── README.md
├── LICENSE
└── .gitignore
```

---

## 📜 License

This project is open-source under the **MIT License**.

Feel free to use, modify, and distribute this project with proper attribution.
