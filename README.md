# Wireless-Liquid-Quality-Monitoring-System-Using-Optical-Sensor
## Description
Wireless liquid quality monitoring system using optical turbidity sensing. The system measures light scattering to estimate turbidity and triggers alerts when contamination exceeds a threshold. LabVIEW simulation with ESP32-based design.
## Features
### Real-Time Monitoring
The system continuously monitors the turbidity level of the liquid and provides real-time quality status.
### Optical Turbidity Detection
Uses an optical sensing method based on the Tyndall Effect to detect impurities in the liquid.
### Threshold Based Alert System
The system compares the turbidity value with a predefined threshold and triggers an alert when contamination is detected.
### Wireless Communication
Uses an ESP32 to enable wireless transmission of monitoring data.
### LabVIEW-Based Simulation
The system behavior was simulated using LabVIEW to visualize turbidity voltage and water quality status.
### Low Cost and Scalable Design
The system uses simple and affordable components, making it suitable for small-scale water monitoring applications.
### Continuous Contamination Detection
Unlike manual testing, the system can detect sudden contamination immediately.
## Hardware used
1. ESP32 - 
Reads sensor data, processes turbidity values, and transmits data wirelessly.
2. Turbidity Sensor (SEN0189) - 
Measures the turbidity level of the liquid by detecting light scattering caused by suspended particles.
3. Li-ion Battery - 
Provides portable power supply for the system.
4. TP4056 Charging Module - 
Used for safe charging and protection of the Li-ion battery.
5. Monitoring Interface - 
Receives turbidity data and contamination alerts wirelessly from the ESP32.
## Software Requirement

1. Arduino IDE
      
2. LabVIEW
## Pin Connections (Wiring Scheme)

| Component | Pin | Connected To |
|-----------|-----|--------------|
| Turbidity Sensor | VCC | 5V / 3.3V (ESP32 Power) |
| Turbidity Sensor | GND | GND |
| Turbidity Sensor | Analog Output | GPIO34 (ADC Pin) |
| ESP32 | VIN | 5V Power Supply |
| ESP32 | GND | Common Ground |
### Wiring Summary Diagram
## Wiring Summary Diagram

          +----------------------+
          |      Turbidity       |
          |        Sensor        |
          |                      |
          |  VCC  --------- 3.3V / 5V (ESP32)
          |  GND  --------- GND
          |  AOUT --------- GPIO34 (ADC)
          +----------------------+

                    |
                    |
             +-------------+
             |    ESP32    |
             |             |
             |  VIN  ---- Power Supply
             |  GND  ---- Common Ground
             +-------------+
## Notes / Tips

- Ensure that the turbidity sensor and ESP32 share a common ground for proper operation.
- The turbidity sensor outputs an analog voltage proportional to the turbidity level of the liquid.
- Use an ADC pin (e.g., GPIO34) on the ESP32 to read the analog signal from the sensor.
- If testing without the turbidity sensor, a potentiometer can be used to simulate varying turbidity levels.
- Provide a stable power supply to the ESP32 to avoid fluctuations in sensor readings.
## Installation & Running the Project

Follow these steps to set up and run the **Wireless Liquid Quality Monitoring System**.

---

### 1. Upload ESP32 Code
1. Open the **Arduino IDE**.
2. Connect the **ESP32** to your PC using a USB cable.
3. Select the correct **board** and **port** from `Tools → Board` and `Tools → Port`.
4. Open the ESP32 sketch (`turbidity_monitor.ino`).
5. Click **Upload** to flash the program to the ESP32.

> ⚠ Ensure the turbidity sensor is correctly connected to the ESP32 ADC pin.

---

### 2. Connect the Turbidity Sensor
Make the following connections:

- **Sensor VCC → 3.3V / 5V (ESP32)**
- **Sensor GND → GND**
- **Sensor Analog Output → GPIO34 (ADC Pin)**

Ensure all components share a **common ground**.

---

### 3. Power the System
1. The ESP32 can be powered using:
   - USB connection from PC, or  
   - External **5V supply to the VIN pin**.
2. Verify that the ESP32 powers on correctly.

---

### 4. Run the LabVIEW Simulation
1. Open the provided **LabVIEW VI file**.
2. Start the **simulation** to visualize turbidity values.
3. Adjust the input signal (or potentiometer during testing) to simulate different turbidity levels.

The interface will display the **turbidity level and system status**.

---

### 5. Monitoring the Output
- The ESP32 reads turbidity data from the sensor.
- The system processes the turbidity level.
- If the turbidity exceeds the predefined threshold, a **warning message is sent to the user’s phone**.

---

## Troubleshooting

### 1. Sensor Not Giving Proper Readings
- Ensure the **sensor output is connected to an ESP32 ADC pin (GPIO34)**.
- Verify that **VCC and GND connections are correct**.
- Check that the water sample is properly placed in front of the sensor.

### 2. Unstable Sensor Values
- Ensure a **stable power supply** for the ESP32.
- Avoid strong external light directly hitting the turbidity sensor.
- Check for loose connections in the circuit.

### 3. ESP32 Not Detected in Arduino IDE
- Install the **ESP32 board package** in the Arduino IDE.
- Verify the correct **COM port** is selected.
