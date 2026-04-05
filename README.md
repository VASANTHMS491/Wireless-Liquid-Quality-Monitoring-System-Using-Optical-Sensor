# 💧 Wireless Liquid Quality Monitoring System

> Real-time optical turbidity sensing with wireless contamination alerts — powered by ESP32 + SEN0189 + LabVIEW.

---

## 📖 Description

A wireless liquid quality monitoring system that uses an optical turbidity sensor (SEN0189) to detect suspended particles via the **Tyndall Effect**. The ESP32 reads the analog sensor output, compares it against a predefined threshold, and wirelessly transmits an alert when contamination is detected. System behavior is also visualized through a **LabVIEW simulation**.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔴 Real-Time Monitoring | Continuously reads and evaluates turbidity levels |
| 💡 Optical Turbidity Detection | Uses light scattering (Tyndall Effect) to detect impurities |
| 🚨 Threshold-Based Alerts | Triggers a warning when turbidity exceeds the set limit |
| 📡 Wireless Communication | ESP32 transmits monitoring data wirelessly |
| 🖥️ LabVIEW Simulation | Visualizes turbidity voltage and water quality status |
| 💰 Low Cost & Scalable | Built with affordable, off-the-shelf components |
| ⚡ Continuous Detection | Detects contamination instantly — no manual testing needed |

---

## 🔧 Hardware Components

### 1. ESP32
Reads sensor data from the ADC pin, processes turbidity values, and transmits data wirelessly.

### 2. Turbidity Sensor — SEN0189
Measures liquid turbidity by detecting light scattering caused by suspended particles. Outputs an analog voltage proportional to turbidity level.

### 3. Li-ion Battery
Provides a portable, rechargeable power supply for the system.

### 4. TP4056 Charging Module
Handles safe charging and over-discharge protection for the Li-ion battery.

### 5. Monitoring Interface
Receives turbidity data and contamination alerts wirelessly from the ESP32.

---

## 💻 Software Requirements

- [Arduino IDE](https://www.arduino.cc/en/software)
- [LabVIEW](https://www.ni.com/en/shop/labview.html)

---

## 🔌 Pin Connections

| Component | Pin | Connected To |
|---|---|---|
| Turbidity Sensor | VCC | 3.3V / 5V (ESP32 Power) |
| Turbidity Sensor | GND | GND |
| Turbidity Sensor | Analog Output | GPIO34 (ADC Pin) |
| ESP32 | VIN | 5V Power Supply |
| ESP32 | GND | Common Ground |

### Wiring Diagram

```
  +---------------------------+
  |     Turbidity Sensor      |
  |        (SEN0189)          |
  |                           |
  |  VCC  ───────── 3.3V/5V ──┐
  |  GND  ───────── GND ──────┤
  |  AOUT ───────── GPIO34 ───┤
  +---------------------------+  |
                                 |
                    +------------+-------+
                    |         ESP32      |
                    |                    |
                    |  VIN  ── Power     |
                    |  GND  ── Common    |
                    +--------------------+
```

---

## 🚀 Installation & Setup

### Step 1 — Upload ESP32 Code

1. Open **Arduino IDE**
2. Connect the **ESP32** to your PC via USB
3. Go to `Tools → Board` and select **ESP32**
4. Go to `Tools → Port` and select the correct COM port
5. Open the sketch file: `turbidity_monitor.ino`
6. Click **Upload** ⬆️

> ⚠️ Ensure the turbidity sensor is correctly connected to GPIO34 before uploading.

---

### Step 2 — Connect the Turbidity Sensor

Make the following connections:

```
Sensor VCC   →  3.3V or 5V (ESP32)
Sensor GND   →  GND
Sensor AOUT  →  GPIO34 (ADC Pin)
```

> ⚠️ All components must share a **common ground** for proper operation.

---

### Step 3 — Power the System

Power the ESP32 using one of the following:
- USB connection from your PC
- External 5V supply connected to the **VIN pin**

Verify that the ESP32 boots up correctly (onboard LED or serial monitor).

---

### Step 4 — Run the LabVIEW Simulation

1. Open the provided **LabVIEW VI file**
2. Start the **simulation**
3. Adjust the input signal (or use a potentiometer during testing) to simulate different turbidity levels
4. The interface will display the **live turbidity level and system status**

---

### Step 5 — Monitor the Output

- The ESP32 reads the analog voltage from the turbidity sensor
- The value is compared against the predefined contamination threshold
- If turbidity **exceeds the threshold** → a **warning alert is sent to your phone** 📱

---

## 📝 Notes & Tips

- **Common ground is essential** — the sensor and ESP32 must share a ground reference for correct ADC readings
- The sensor outputs an **analog voltage proportional to turbidity** — higher turbidity = lower voltage (varies by sensor orientation)
- Always use an **ADC-capable pin** such as GPIO34 on the ESP32
- **No sensor available?** Simulate varying turbidity using a potentiometer on GPIO34
- Use a **stable power supply** — voltage fluctuations will cause noisy ADC readings
- **Avoid direct strong light** hitting the sensor — ambient light can interfere with readings

---

## 🛠️ Troubleshooting

### ❌ Sensor not giving proper readings
- Verify **AOUT is connected to GPIO34** (an ADC-capable pin)
- Check that **VCC and GND connections are secure**
- Ensure the **water sample is correctly positioned** in front of the sensor window

### 📉 Unstable or noisy sensor values
- Provide a **stable power supply** to the ESP32
- Shield the sensor from **strong external or ambient light**
- Check all wiring for **loose connections**

### 🔌 ESP32 not detected in Arduino IDE
- Install the **ESP32 board package**: `File → Preferences → Additional Boards Manager URLs`
  - Add: `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`
  - Then go to `Tools → Board → Boards Manager` and search **ESP32**
- Verify the correct **COM port** is selected under `Tools → Port`
- Try a **different USB cable** — some cables are charge-only and won't transmit data

---

## 📁 Project Structure

```
wireless-liquid-quality-monitor/
├── turbidity_monitor.ino     # ESP32 Arduino sketch
├── labview_simulation.vi     # LabVIEW VI file
└── README.md                 # This file
```

---

## 📜 License

This project is open-source. Feel free to use, modify, and distribute with attribution.
