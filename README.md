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
| Turbidity Sensor | VCC | 5V (Microcontroller) |
| Turbidity Sensor | GND | GND |
| Turbidity Sensor | Analog Output | A0 (Analog Pin) |
| ESP32 / Microcontroller | VCC | Power Supply |
| ESP32 / Microcontroller | GND | Common Ground |
