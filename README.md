# 🏠 Intelligent Home System — Design & Implementation

The **Intelligent Home System** is a **smart**, **secure**, and **energy-efficient** home automation prototype built around the **Arduino Mega 2560** as the **central controller**. It integrates multiple subsystems including **weather-based control**, **biometric and RFID security**, and **hazard detection** to create an **adaptive environment** that responds dynamically to both **user input** and **environmental conditions**. Through sensors like the **LDR**, **DHT11**, and **YL83 rain module**, the system **autonomously manages lighting, ventilation, and cooling** to maintain comfort while minimizing energy use.

For **security and interactivity**, the system combines **RFID** and **AS608 fingerprint authentication** with real-time **ESP32-CAM surveillance**, allowing **remote viewing** and **pan-tilt control** through a **web interface**. The **offline voice recognition module (DFRobot Gravity)** introduces a fully **voice-driven control mode**, where users can manage **all major functionalities** — including lights, fans, windows, doors, and other connected devices — through spoken commands without relying on an internet connection. A **wake-up phrase (“Intelligent Home Design”)** activates the voice mode, followed by direct verbal instructions to control specific systems. The setup also integrates a **DFPlayer Mini with an SD card and speaker**, providing **audio playback feedback** that confirms recognized commands and system actions. Together, these technologies form a **reliable** and **intelligent framework** that enhances **home safety**, **energy efficiency**, and **user convenience**.

<table align="center">
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/7e6efa735bccb3480ec767294fb9276b9885bc20/frontview.jpg" 
           alt="Front View of Intelligent Home System" 
           width="450"/>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/74869784f39ebad32bbad749d43681cdf4ec9ef7/back%20biew.jpg" 
           alt="Back View of Intelligent Home System" 
           width="450"/>
    </td>
  </tr>
</table>

<p align="center"><em>Front and Back Views of the Intelligent Home System Prototype</em></p>

<p align="center">
  <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/74869784f39ebad32bbad749d43681cdf4ec9ef7/topview.jpg" 
       alt="Top View of Intelligent Home System" 
       width="700"/>
  <br>
  <em>Top View of the Intelligent Home System Prototype</em>
</p>




---

## 🧠 System Concept

The **Intelligent Home System** was designed with the idea of combining **automation, safety, and interaction** within a unified embedded framework.  
It performs four major tasks:

1. **Weather-Adaptive Automation** — Automatically adjusts lighting, cooling, and ventilation using LDR, DHT11, and rain sensors.  
2. **Security & Access Control** — Dual authentication through RFID and fingerprint verification, supported by live ESP32-CAM video feed with pan–tilt control.  
3. **Hazard Detection & Response** — Continuous air quality monitoring (via MQ-135) with audible/visual alerts and automatic evacuation measures.  
4. **Multimodal Control** — Operation via autonomous logic, IR remote, or offline voice commands, providing flexibility and human-centered design.

---

## ⚙️ Key Features Explained

### 🌤️ 1. Weather Analysis and Control
- **Lighting Control:**  
  A **Light Dependent Resistor (LDR)** monitors ambient brightness. When light levels fall below a threshold, the **WS2812B RGB LED** strip turns on automatically, simulating smart lighting behavior.
<table align="center">
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/cbf8ef11208d18b8b9f2603323c26deaeb79d5a9/light%20systems.png" 
           alt="Light Control System Diagram and LDR Test" 
           width="380"/>
      <p><em>Function of WS2812B LED in response to light intensity from LDR</em></p>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/cbf8ef11208d18b8b9f2603323c26deaeb79d5a9/Untitled%20video%20-%20Made%20with%20Clipchamp%20(1).gif" 
           alt="Light System Demonstration GIF" 
           width="380"/>
      <p><em>Automatic lighting response demonstration</em></p>
    </td>
  </tr>
</table>

- **Temperature-Based Cooling:**  
  A **DHT11** sensor tracks room temperature. When temperature ≥ 28°C, a **DC fan** (driven by an **L9110 H-bridge motor driver**) activates automatically.
  <p align="center">
  <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/2ee41b3eb348e5597bb24a2325e2f8cfb49d672f/cooling%20systems.png" 
       alt="Cooling System Diagram and DHT11 Temperature Control" 
       width="500"/>
  <br>
  <em>Automatic cooling system controlled by DHT11 temperature readings</em>
</p>

  
- **Rain Detection & Ventilation:**  
  A **YL-83 rain sensor** detects precipitation. If rain is detected, a **servo motor** automatically closes the window to prevent interior damage.
  <table align="center">
  <tr>
    <td align="center">
      <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/c8301b7aafbd698fb00145eb322963f945926357/precipitation.png" 
           alt="Precipitation Detection Diagram and YL-83 Rain Sensor Test" 
           width="380"/>
      <p><em>Rain detection and automatic window control using YL-83 sensor</em></p>
    </td>
    <td align="center">
      <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/c8301b7aafbd698fb00145eb322963f945926357/precipitation.gif" 
           alt="Precipitation System Demonstration GIF" 
           width="380"/>
      <p><em>Real-time precipitation response demonstration</em></p>
    </td>
  </tr>
</table>

<p align="center">
  <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/4a0e1f9312deb889f0706c540b4c75773fbc9334/control%20weather.png" 
       alt="Weather Analysis and Control Flow Diagram" 
       width="650"/>
  <br>
  <em>Flow diagram of weather analysis and control logic</em>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/4a0e1f9312deb889f0706c540b4c75773fbc9334/circuit%20diagram%20weather%20control.png" 
       alt="Weather Control Circuit Diagram using Arduino Mega" 
       width="650"/>
  <br>
  <em>Circuit diagram of the weather control subsystem using Arduino Mega 2560</em>
</p>


### 🔐 2. Security & Access System
- **RFID Authentication:**  
  The **MFRC522 module** scans RFID tags/cards. Registered UIDs are matched in EEPROM; on successful authentication, the **door servo motor** rotates to unlock.
- **Fingerprint Access (AS608):**  
  Provides biometric verification for enhanced security, working in parallel with RFID for dual validation.
- **ESP32-CAM Integration:**  
  Streams real-time video via local Wi-Fi. Two **SG90 servos** allow pan and tilt, enabling flexible surveillance through a simple web interface.
- **Status Feedback:**  
  A **16×2 I²C LCD** displays system status, operation mode, and authentication results in real time.

### 🚨 3. Hazard Detection & Safety Response
- The **MQ-135 sensor** continuously measures air quality.  
  When dangerous gases (smoke, CO₂, LPG) exceed the threshold:
  - A **buzzer** activates to alert occupants.  
  - **WS2812B LEDs** switch to red for visual warning.  
  - **Ventilation servos** automatically open windows to allow gas escape.  
This ensures a prompt reaction to fire or toxic gas incidents.

### 🎙️ 4. Control Modes
Three operating modes allow flexible control and fault tolerance:

| Mode | Description | Control Hardware |
|------|--------------|------------------|
| **Mode 1 – Autonomous** | Default automatic operation responding to environment (LDR, DHT11, Rain). | Sensors only |
| **Mode 2 – IR Remote** | Manual override using IR remote. | IR receiver + remote |
| **Mode 3 – Voice Command** | Offline voice recognition via DFRobot Gravity module. Triggered by wake word *“Intelligent Home Design.”* | Voice module + mic |

---

## 🔩  System Architecture

### ⚙️ Microcontroller & Interfaces
- **MCU:** Arduino Mega 2560  
- **Communication Buses:**  
  - **I²C:** LCD (16x2 with backpack)  
  - **SPI:** RFID (MFRC522)  
  - **UART:** Fingerprint Sensor (AS608) and Voice Module  
  - **PWM:** Servos, WS2812B LEDs, and Fan Driver

---

### 🧩 Sensor–Actuator Mapping

| Sensor / Module | Pin Connection | Actuator / Output | Function |
|-----------------|----------------|-------------------|-----------|
| **LDR (Light Sensor)** | A0 | WS2812B RGB LED (DIN) | Auto room lighting based on ambient light |
| **DHT11 (Temp/Humidity)** | D8 | Fan via L9110 (D9, D10) | Automatic cooling when temperature ≥ threshold |
| **Rain Sensor (YL-83)** | A1 | Window Servo (D7) | Closes window during rain |
| **RFID (MFRC522)** | SPI pins | Door Servo | Opens door when authorized tag detected |
| **Fingerprint Sensor (AS608)** | Serial (TX2/RX2) | Door Servo + LCD (SDA, SCL) | Biometric access control and status display |
| **Gas Sensor (MQ-135)** | A2 (example) | Buzzer + WS2812B alert | Triggers alarm and red warning lights during gas leak |
| **IR Receiver** | D11 (example) | — | IR remote-based control (Mode 2) |
| **ESP32-CAM** | Wi-Fi | Pan/Tilt Servos | Wireless surveillance with live streaming |
| **Voice Module (DFRobot Gravity)** | UART | Multiple devices | Offline voice control (Mode 3) |

---

### 🔗 Data Flow Overview

[Sensors] → [Arduino Mega 2560] → [Decision Logic] → [Actuators / Outputs]

Each sensor continuously feeds data to the Mega.  
Depending on the selected **control mode**, the system decides whether to:
- Act automatically (weather-based)
- Respond to IR remote input
- Execute voice commands

Outputs like LEDs, fans, and servos are driven through PWM or digital pins accordingly.

---

### 🧠 Functional Summary
- **Autonomous Mode:** Weather and environment-driven control.  
- **Manual Mode (IR):** Direct user control via remote.  
- **Voice Mode:** Wake-word activation + command recognition.  
- **Security Layer:** RFID & fingerprint double authentication.  
- **Safety Layer:** Gas & smoke monitoring with audible + visual alerts.

> Separate power supplies for **logic** and **motors/servos** to prevent brownout or reset during high current draw.

---

## 🧰 Components Summary

| Category | Components Used |
|-----------|-----------------|
| MCU | Arduino Mega 2560 |
| Environmental | LDR, DHT11, YL-83 Rain Sensor |
| Security | MFRC522 RFID Reader, AS608 Fingerprint, ESP32-CAM |
| Hazard | MQ-135 Gas Sensor, Piezo Buzzer |
| Actuators | SG90 Servos, L9110 Motor Driver, WS2812B RGB Strip |
| User Interface | LCD 1602 I²C Display, IR Remote, Voice Recognition Module |
| Power | Regulated 5V logic + independent 5V/6V for servos & LEDs |

---

## 🧩 Software & Libraries

- **Arduino IDE** (C/C++)  
- **Libraries Used:**
  - `Adafruit_NeoPixel.h` or `FastLED.h` (RGB control)
  - `Servo.h`
  - `DHT.h`
  - `LiquidCrystal_I2C.h`
  - `MFRC522.h`
  - `Adafruit_Fingerprint.h`
  - `IRremote.h`
  - `SoftwareSerial.h`
  - `WiFi.h` (for ESP32-CAM)
  - `ESPAsyncWebServer.h` (web interface)

---

## 🧠 Control Algorithm Summary

### Automated Control (Mode 1)
1. Read LDR → Control LEDs  
2. Read DHT11 → Fan ON if temp ≥ 28 °C  
3. Read YL-83 → Close windows on rain  
4. Continuously check MQ-135 → Alert + ventilation if gas detected  

### Manual Control (Modes 2 & 3)
- IR remote toggles each device manually.
- Voice recognition interprets predefined commands:  
  “Turn on light”, “Open window”, “Lock door”, “Activate fan”, etc.

### Security Flow
1. Scan RFID card → verify UID  
2. If valid → unlock door  
3. If invalid → buzzer alert


