# 📡 ESP8266 Evil Twin - Network Security Simulation

![Version](https://img.shields.io/badge/Version-5.0-blue)
![Platform](https://img.shields.io/badge/Platform-ESP8266-orange)
![License](https://img.shields.io/badge/License-MIT-green)

A professional-grade Network Security Research Tool designed for the ESP8266 platform. This tool demonstrates the **Evil Twin Attack**—a sophisticated phishing technique used to capture WiFi passwords by mimicking legitimate access points.

---

## 📌 1. About the Project

The **ESP8266 Evil Twin** is an all-in-one hardware and software solution that combines a powerful backend logic with a premium, responsive web interface and a physical interaction system (OLED + Buttons). Unlike basic simulations, this project features **Real-time Password Verification**, ensuring that only correct credentials are logged.

### 🌟 Key Features
- **Modern Responsive UI**: Premium Dashboards with Dark/Light mode support.
- **Physical Interface**: Full control via a 128x64 OLED display and 4 dedicated buttons.
- **Smart Scanning**: Async WiFi scanning to identify and target local networks.
- **Captive Portal**: Redirects victims to a realistic "Security Validation" page.
- **Persistent Logging**: Stores captured credentials in the ESP8266's EEPROM (survives reboots).
- **Auto-Stop Logic**: Automatically stops the attack and notifies the admin once a valid password is found.
- **Enterprise Dashboard**: A centralized hub to manage scans, view real-time stats, and export logs.

---

## ⚙️ 2. How It Works (The Process)

The tool operates in a structured sequence to ensure a successful "simulated" attack:

1.  **Scanning**: The admin initiates a scan (via Web or OLED). The ESP8266 switches to Station Mode briefly to sniff nearby SSIDs and their signal strengths (RSSI).
2.  **Cloning**: Once a target is selected, the ESP8266 creates a Soft Access Point (AP) with the **exact same name (SSID)** as the target.
3.  **Baiting**: Victims see an open network (or one with a known default password) and connect to it.
4.  **Redirection**: A DNS server on the ESP8266 intercepts all web requests and redirects the victim to a hosted "Security Validation" portal (`192.168.4.1`).
5.  **Deception**: The portal informs the user that a "security re-validation" is required for their network.
6.  **Capture & Verify**: 
    - The victim enters the password.
    - The ESP8266 disconnects its server temporarily and attempts to connect to the **Actual Target Network** using the provided credentials.
    - If connection succeeds (`WL_CONNECTED`), the password is verified as correct.
7.  **Finalization**: If verified, the credentials are saved to EEPROM, and the attack stops. The victim is shown a "Success" page.

---

## 🛠️ 3. Installation & Requirements

### 💎 Hardware Needed
- **Microcontroller**: ESP8266 (NodeMCU, Wemos D1 Mini, or generic ESP-12E).
- **Display**: SSD1306 128x64 I2C OLED (Address `0x3C`).
- **Input**: 4 Tactile Push Buttons (Up, Down, Select, Back).
- **Connections**:
    - **OLED**: SDA -> GPIO 5 (D1), SCL -> GPIO 4 (D2).
    - **Buttons**: UP (D3), DOWN (D6), SELECT (D7), BACK (D5).

### 🚀 Flashing via Binary (Recommended)

To get started quickly without compiling code, follow these steps to flash the pre-compiled production binary:

1.  **Binary Path**: `build/esp8266.esp8266.nodemcuv2/EVIL_TWINS_ESP8266.ino.bin`
2.  **Flash Tool**: Use **NodeMCU PyFlasher** (GUI) or **esptool.py** (CLI).
3.  **Download Settings**:
    - **Board**: NodeMCU v2 (ESP-12E)
    - **Flash Mode**: DIO
    - **Baud Rate**: 115200
    - **CPU Frequency**: 160MHz (recommended for better web UI performance)
4.  **Steps**:
    - Connect the ESP8266 to your PC via USB.
    - Open your flashing tool and select the `.bin` file.
    - Click **Flash** and wait for completion.
    - Press the **Reset** button on the board after flashing.

---

## 🖥️ 4. Web Interface & API

The tool exposes a powerful rest-based API and a premium web dashboard for control:

- **Dashboard**: `http://192.168.4.1/menu` (Admin Hub)
- **Scanning**: Initiates environmental WiFi analysis via background tasks.
- **Stats**: Real-time tracking of connected victims and system state.
- **Log Management**: Access and purge captured credentials directly from the browser.
- **Capture Portal**: Advanced HTML5/CSS3 portal designed to mimic enterprise security gateways.

---

## 📖 5. Usage Guide

1.  **Power On**: You'll be greeted by the splash screen.
2.  **Navigation**: Use the physical buttons to select "Scan Networks".
3.  **Targeting**: Once scanning is complete, go to "Select Target" and pick a network.
4.  **Execute**: Press "OK" to start the attack. The OLED will show "ATTACK IN PROGRESS".
5.  **Monitoring**: Access `192.168.4.1/menu` from any device connected to the ESP8266's AP (`EVIL_TWINS_BY_CHETAN` or the cloned SSID) to see the dashboard.
6.  **Capture**: When a victim enters a password, the OLED will show "Verifying...".
7.  **Success**: If correct, the device stops automatically. You can view the password in the "Show Logs" menu or via the web portal.

---

## ⚠️ Disclaimer

**This tool is for EDUCATIONAL PURPOSES ONLY.** 
Unauthorized access to computer systems or networks is illegal. The author (@chetanngavali) is not responsible for any misuse of this tool. Always ensure you have explicit, written permission before testing on any network you do not own.

---

## 💎 6. Small Details & Optimizations

To make the tool professional and robust, several "small features" were implemented:

- **Smart Truncation**: SSIDs and passwords are automatically truncated on the OLED display to fit the 128px width without breaking the UI.
- **Async Scanning**: Scanning doesn't block the main loop, allowing the OLED and Buttons to remain responsive.
- **Edge-Detection Debouncing**: Buttons use a state-change guard (500ms) to prevent accidental double-clicks or menu jumping.
- **EEPROM Integrity**: A magic-number style check ensures that logs are only read if the `logCount` is within valid bounds (0-20).
- **Realistic Redirection**: The captive portal handles `onNotFound` requests, ensuring that no matter what URL the victim types (e.g., `google.com`), they always end up on the login page.
- **Browser Compatibility**: The web interface uses standard CSS variables and minimal JS for compatibility across older and mobile browsers.
- **State Change Guard**: A 500ms lockout after menu changes ensures the "Select" action on one menu doesn't accidentally trigger an action on the next menu.

---

### 👨‍💻 Developed By
**Chetan Gavali**  
GitHub: [@chetanngavali](https://github.com/chetanngavali)  
Version: 5.0 Final
