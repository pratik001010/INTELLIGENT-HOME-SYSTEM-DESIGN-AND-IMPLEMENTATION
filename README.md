# 🏠 Intelligent Home System — Design & Implementation

A **smart, secure, and energy-efficient home automation prototype** integrating multiple subsystems — weather-based control, biometric and RFID security, hazard detection, and multi-mode control — all coordinated through an **Arduino Mega 2560** master controller.

This project demonstrates how embedded systems, sensor networks, and intelligent decision-making can together create an adaptive living environment that responds to both **human commands** and **environmental conditions**.

<p align="center">
  <img src="https://raw.githubusercontent.com/<your_username>/Intelligent-Home-System/main/docs/images/overview.jpg" 
       alt="Intelligent Home System Overview" 
       width="720"
       style="object-fit:cover;border-radius:10px;"/>
</p>

   <p align="center">
  <img src="https://github.com/pratik001010/INTELLIGENT-HOME-SYSTEM-DESIGN-AND-IMPLEMENTATION/blob/0b1e670df23cef9e7f049d1e49f619f0ed5c5a53/Untitled%20video%20-%20Made%20with%20Clipchamp%20(1).gif" width="250" alt="Intelligent Home System Demo"/>
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

### 🌤️ 1. Weather-Responsive Environment
- **Lighting Control:**  
  A **Light Dependent Resistor (LDR)** monitors ambient brightness. When light levels fall below a threshold, the **WS2812B RGB LED** strip turns on automatically, simulating smart lighting behavior.
- **Temperature-Based Cooling:**  
  A **DHT11** sensor tracks room temperature. When temperature ≥ 28°C, a **DC fan** (driven by an **L9110 H-bridge motor driver**) activates automatically.
- **Rain Detection & Ventilation:**  
  A **YL-83 rain sensor** detects precipitation. If rain is detected, a **servo motor** automatically closes the window to prevent interior damage.

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

## 🔩 Hardware Architecture

**Main Controller:** Arduino Mega 2560  
**Communication Interfaces:** SPI, UART, I²C, PWM


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


