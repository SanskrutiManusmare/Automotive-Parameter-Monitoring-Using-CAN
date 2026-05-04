# 🚗Automotive-Parameter-Monitoring-Using-CAN (LPC2129)

## 📌 Project Overview
This project implements a **multi-node automotive dashboard system** using the **Controller Area Network (CAN) protocol**. The system consists of three nodes — **Main Node, Fuel Node, and Indicator Node** — communicating over a CAN bus to display real-time vehicle parameters like temperature, fuel level, and indicator status on an LCD.

🌡️ Engine Temperature — measured using DS18B20 digital temperature sensor (1-Wire interface)  
⛽ Fuel Level — acquired using ADC-based analog sensor and transmitted as percentage (0–100%)  
🔄 Turn Indicators (Left/Right) — controlled via switches and executed using LED blinking patterns  
📡 CAN Communication — reliable multi-node data exchange using CAN protocol  
📟 Live Display — all parameters are displayed in real-time on a 20×4 LCD

A central **Main Node** acts as the controller and display unit. It receives sensor data from other nodes over the CAN bus, processes it, and continuously updates the dashboard. The system demonstrates a distributed embedded architecture similar to real automotive networks.

---

## 🧠 System Architecture
The system follows a **distributed architecture**:

- **Main Node (Master)**
  - Displays data on LCD
  - Reads temperature sensor
  - Controls indicators via switches

- **Fuel Node**
  - Reads fuel level using ADC
  - Sends fuel data over CAN

- **Indicator Node**
  - Controls LED indicators
  - Receives commands from Main Node

---

## 🧩 Block Diagram
![Block Diagram](Blockdiagram.png)

---

## 🔧 Hardware Setup
![Hardware Setup](Hardware_setup.jpeg)

---

## 🔌 CAN Network
![CAN Network](CAN.jpeg)

---

## 📟 LCD Output
![LCD Output](lcd_output.jpeg)

---

## ⚙️ Components Used

- LPC2129 (ARM7 Microcontroller)
- MCP2551 CAN Transceiver
- DS18B20 Temperature Sensor
- 16x2 LCD (JHD 204A)
- Fuel Sensor (Analog via ADC)
- LEDs (Indicators)
- Switches
- Power Supply

---

## 🛠️ Software & Tools

- Embedded C
- Keil µVision IDE
- Flash Magic
- CAN Protocol (ISO 11898)

---

## 📂 Project Structure

Automotive-Parameter-Monitoring-Using-CAN/
│
├── MAIN_NODE/
│   ├── main_node.c
│   ├── ds18b20.c
│   ├── ds18b20.h
│   └── main_node.uvproj
│
├── FUEL_NODE/
│   ├── fuel_node.c
│   ├── adc.c
│   ├── adc.h
│   └── fuel_node.uvproj
│
├── INDICATOR_NODE/
│   ├── indicator_node.c
│   └── indicator_node.uvproj
│
├── DRIVERS/
│   ├── can.c
│   ├── can.h
│   ├── lcd.c
│   ├── lcd.h
│   ├── delay.c
│   ├── delay.h
│   └── types.h
│
├── STARTUP/
│   ├── startup.s          # ARM startup file
│   └── system.c           # system initialization (PLL, clock)
│
├── BUILD/
│   ├── main_node.hex
│   ├── fuel_node.hex
│   └── indicator_node.hex
│
└── README.md

---

## 🚀 Getting Started

### 🔹 Prerequisites
- Keil µVision
- Flash Magic
- LPC2129 Board
- CAN Setup (MCP2551)

---

### 🔹 Build & Flash
1. Open project in Keil
2. Compile the code
3. Generate `.hex` file
4. Flash using Flash Magic

---

### 🔹 CAN Bus Wiring
- Connect:
  - CANH ↔ CANH
  - CANL ↔ CANL
- Add **120Ω resistors** at both ends

---

### 🔹 Pin Configuration (LPC2129)

| Peripheral | Pins |
|-----------|------|
| CAN TX    | P0.0 |
| CAN RX    | P0.1 |
| LCD       | GPIO |
| ADC       | AD0.x |
| Switches  | GPIO |
| LEDs      | GPIO |

---

## 📊 Working

1. Fuel Node reads fuel level → sends via CAN  
2. Indicator Node controls LEDs based on command  
3. Main Node:
   - Reads temperature  
   - Receives fuel data  
   - Sends indicator control  
   - Displays all data on LCD  

---

## 💡 Key Features

- Multi-node CAN communication  
- Real-time dashboard  
- Embedded system design  
- Scalable architecture  

---

## 📚 Key Learnings

- CAN Protocol implementation  
- Embedded C programming  
- Sensor interfacing  
- Real-time systems  

---

## ⭐ Future Enhancements

- Speed sensor integration  
- IoT-based monitoring  
- Mobile app dashboard  
- Fault detection system  

---

## 👨‍💻 Author

**Sanskruti Manusmare**-Embedded Systems Major Project
Platform-Vector India's LPC2129 CAN Node Board|Keil µVision|Flash Magic

---
