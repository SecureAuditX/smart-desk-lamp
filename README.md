# Smart Voice-Controlled Lighting Device (STM32 Based)

![MCU](https://img.shields.io/badge/MCU-STM32F103C6T6-blue)
![Architecture](https://img.shields.io/badge/Core-ARM%20Cortex--M3-orange)
![Power](https://img.shields.io/badge/Input-12V-green)
![Voltage](https://img.shields.io/badge/Regulation-12V→5V→3.3V-yellow)
![Status](https://img.shields.io/badge/Project-Prototype-informational)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> Embedded smart lighting control system integrating voice recognition, infrared communication, and dynamic RGB lighting — built around the STM32F103 microcontroller platform.

> ## 🚧 Development Status

This project is currently in active development.

The hardware prototype and core firmware are functional, while optimization, enclosure refinement, and extended feature integration are ongoing.

Updates, design revisions, and documentation improvements will continue as the system progresses toward a production-ready version.

---

## 📌 Project Overview

This project is a fully custom embedded hardware system that combines:

* 🎙 Voice Command Control
* 💡 High-Efficiency LED Illumination
* 🌈 Addressable RGB Dynamic Lighting Effects
* 📡 Infrared Transmission & Reception
* ⚡ Multi-Stage Power Regulation

The system is designed from the ground up, covering:

* Hardware schematic design
* PCB layout
* Power electronics engineering
* Embedded firmware architecture
* Mechanical enclosure modeling

The goal is to create a compact, efficient, and scalable smart lighting control device.

---

## 📷 Project Preview

### 🖥 Device Rendering

> Picture Coming Soon

![Device Render](images/device-render.png)

---

### 🔍 Exploded View (Internal Structure)

> Picture Coming Soon

![Exploded View](images/exploded-view.png)

---

### 🔧 PCB Design

> PCB layout or schematic screenshots

![PCB Layout](images/pcb-layout.png)
![Schematic](images/schematic.png)

---

# 🏗 System Architecture

Voice Module (VC-02_CN)  →  UART  →  STM32F103C6T6  →  Peripheral Control

Peripherals Controlled by MCU:

* WS2812B RGB LEDs
* PT4115 LED Driver (PWM dimming)
* Infrared Transmitter (MOSFET-driven)
* Infrared Receiver

---

# 🔩 Hardware Architecture

## 1️⃣ Main Control Module

**MCU:** STM32F103C6T6ATR
**Core:** ARM Cortex-M3
**Clock:** External 8MHz Crystal (8M-HC-49SMD)
**Debug:** SWD Interface (SWCLK / SWDIO)

### Responsibilities

* System scheduling
* UART voice data processing
* Infrared encoding and decoding
* WS2812B timing signal generation
* PWM dimming control

### Communication Interfaces

* UART → Voice module (VC-02_CN)
* GPIO → IR transmit / receive
* PWM → PT4115 DIM pin
* Single-wire → WS2812B DIN
* I²C reserved expansion (SDA/SCL)

---

## 2️⃣ Voice Recognition Module

**Module:** VC-02_CN

* Preset command instruction set
* Serial output via UART
* Dedicated configuration tool

### Interfaces

* MIC+ / MIC- (Microphone input)
* TX / RX (Serial communication)

The module directly transmits decoded voice commands to the STM32 for execution.

---

## 3️⃣ Lighting Driver Module

### 💡 Main Illumination

* Aluminum substrate LED
* PT4115 constant current driver
* PWM dimming support via DIM pin
* High-efficiency current regulation

### 🌈 RGB Lighting

* WS2812B addressable LEDs
* Single-wire serial protocol
* Precise timing control from STM32
* Supports animation and dynamic lighting effects

---

## 4️⃣ Infrared Module

### Transmitter

* IR17-21C infrared diode
* AO3400A MOSFET (Q1/Q2)
* GPIO-driven signal modulation

### Receiver

* IRM-H638T infrared receiver
* Decodes external remote control signals
* Outputs decoded signals to STM32

---

## 5️⃣ Power Management

**Input:** DC 12V (DC-005-A200 Interface)

### Voltage Conversion Stages

| Stage     | Component      | Function                             |
| --------- | -------------- | ------------------------------------ |
| 12V → 5V  | XL1509-5.0     | Buck converter for LED & IR modules  |
| 5V → 3.3V | LP5907QMFX-3.3 | Low-noise LDO for MCU & voice module |

### Protection & Stability

* Overcurrent protection fuse (BSMD1206-025)
* Reverse polarity protection diode
* Distributed decoupling capacitors (100uF / 0.1uF)
* Inductor-based filtering for stable switching regulation

---

# 🧠 Firmware Architecture

Core firmware responsibilities include:

* UART interrupt handling
* Command parsing logic
* IR encoding/decoding routines
* PWM brightness control
* WS2812B timing driver implementation
* System state management
* Peripheral abstraction layer

Firmware developed using STM32CubeIDE / Keil MDK.

---

# 🛠 Development Tools

## Hardware Design

* JLCPCB EDA

## Firmware Development

* STM32CubeIDE
* Keil MDK (μVision)

## Mechanical Design

* 3DMAX (Enclosure modeling and 3D printing)

---

# 📂 Recommended Repository Structure

```
├── Firmware/
│   ├── Core/
│   ├── Drivers/
│   ├── Middleware/
│   └── main.c
│
├── Hardware/
│   ├── Schematic/
│   ├── PCB/
│   └── BOM/
│
├── Mechanical/
│   └── Enclosure/
│
├── Documents/
│   ├── Detailed_Design.pdf
│   ├── Test_Report.pdf
│   └── User_Manual.pdf
│
├── images/
│   ├── device-render.png
│   ├── exploded-view.png
│   ├── pcb-layout.png
│   └── schematic.png
│
└── README.md
```

---

# 🔬 Engineering Highlights

* Multi-stage regulated power architecture
* Low-noise LDO for sensitive MCU domain
* MOSFET-driven infrared transmission
* Hardware-level protection circuitry
* Distributed power decoupling network
* Real-time RGB timing control
* Modular firmware abstraction
* Compact enclosure design

---

# 🚀 Project Status

* [x] System Architecture Defined
* [x] Hardware Schematic Designed
* [x] PCB Layout Completed
* [x] Firmware Core Functional
* [ ] Enclosure Optimization
* [ ] Thermal Optimization
* [ ] Power Consumption Optimization
* [ ] Production Revision

---

# 📈 Future Improvements

* Bluetooth / Wi-Fi module integration
* Mobile application control
* OTA firmware updates
* Advanced lighting presets
* Smart ambient sensing integration
* Battery-powered version

---

# 📜 License

This project is released under the MIT License.

---

# 👤 Author

ABDULKARIM UMAR
Software Engineer | Embedded Systems Developer | Hardware Design | Firmware Engineering | Power Electronics | ARM Architecture

---

> This repository documents the complete engineering process from concept to functional embedded prototype.
