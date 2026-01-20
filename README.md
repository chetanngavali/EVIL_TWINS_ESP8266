# 🦅 ESP8266 Evil Twin - Advanced Security Audit Tool

> **⚠️ DISCLAIMER: FOR EDUCATIONAL & AUTHORIZED SECURITY RESEARCH ONLY.**  
> This tool is designed for network security auditing and educational purposes. Usage of this tool for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state, and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program.

---

## 📖 Overview

**Evil Twin ESP8266** is a state-of-the-art, feature-rich penetration testing tool designed for the ESP8266 platform. It allows security researchers to simulate an "Evil Twin" attack to audit the security awareness of wireless users. 

This project features a **Dual-Mode Interface**:
1.  **Physical OLED Menu**: Fully autonomous operation using physically attached buttons and an OLED display.
2.  **Web Management Console**: A responsive, professional web dashboard to control attacks remotely from a smartphone or laptop.

## ✨ Key Features

*   **🛡️ Autonomous Operation**: No external computer required; runs entirely on ESP8266.
*   **🖥️ OLED Display UI**: Crisp 128x64 display showing menus, network lists, and attack status.
*   **📱 Web Management Dashboard**: Professional dark-mode UI to scan, select targets, and view captured credentials.
*   **💾 Persistent Logging**: Saves captured credentials to EEPROM, surviving power cycles.
*   **🔒 Captive Portal**: Includes a realistic, Google-styled "Sign in to network" phishing page.
*   **⚡ Auto-Verification**: Automatically validates captured passwords against the target AP to ensure accuracy.
*   **🕵️ Stealth Mode**: Configurable SSID and stealthy operation.

---

## 🛠️ Hardware Requirements

| Component | Quantity | Description |
| :--- | :---: | :--- |
| **ESP8266 NodeMCU / Wemos D1 Mini** | 1 | The brain of the operation. |
| **0.96" OLED Display (I2C)** | 1 | SSD1306 128x64 Display for visual feedback. |
| **Push Buttons** | 4 | Tactile switches for menu navigation. |
| **Jumper Wires & Breadboard** | - | For connecting components. |

---

## 🔌 Wiring Diagram & Connections

Connect your components as follows. The buttons should connect the GPIO pin to Ground (GND) when pressed (Input Pullup is used internally).

### 🖥️ OLED Display (I2C)
| OLED Pin | ESP8266 Pin | GPIO |
| :--- | :--- | :--- |
| **SDA** | D1 | GPIO 5 |
| **SCL** | D2 | GPIO 4 |
| **VCC** | 3.3V | - |
| **GND** | GND | - |

### 🎮 Navigation Buttons
| Button Function | ESP8266 Pin | GPIO |
| :--- | :--- | :--- |
| **UP** | D3 | GPIO 0 |
| **DOWN** | D6 | GPIO 12 |
| **SELECT / ENTER** | D7 | GPIO 13 |
| **BACK / EXIT** | D5 | GPIO 14 |

> **Note**: Wiring may vary slightly depending on your specific board code definitions. Check `EVIL_TWINS_ESP8266.ino` lines 53-56 to confirm button pins.

### 📸 Connection Photos

**OLED Display Connection**
![OLED Connection](./ALL%20Connections/esp8266%20oled%20connection.png)

**Buttons Connection**
![Buttons Connection](./ALL%20Connections/esp8266%20Buttons%20Connections.png)

---

## 🚀 Installation Guide

1.  **Install Arduino IDE**: Download and install the latest [Arduino IDE](https://www.arduino.cc/en/software).
2.  **Add ESP8266 Support**:
    *   Go to `File` > `Preferences`.
    *   Add this URL to "Additional Boards Manager URLs": `http://arduino.esp8266.com/stable/package_esp8266com_index.json`
    *   Go to `Tools` > `Board` > `Boards Manager`, search for **esp8266**, and install it.
3.  **Install Required Libraries**:
    *   Go to `Sketch` > `Include Library` > `Manage Libraries`.
    *   Search for **"ESP8266 and ESP32 OLED driver for SSD1306 displays"** by *ThingPulse* (or `SSD1306Wire`). Install it.
4.  **Flash the Firmware**:
    *   Open `EVIL_TWINS_ESP8266.ino`.
    *   Select your board (e.g., `NodeMCU 1.0 (ESP-12E Module)`) under `Tools` > `Board`.
    *   Click **Upload**.

---

## 🕹️ Usage Guide

### Method 1: Using Physical Buttons
1.  **Startup**: Power on the device. You will see the splash screen.
2.  **Scan**: Navigate to **Scan Networks** and press **SELECT**.
3.  **Target**: Choose a target network from the list.
4.  **Attack**: Press **SELECT** to start the Evil Twin attack. The device will clone the SSID and wait for victims.
5.  **Monitor**: The OLED screen will show "ATTACK IN PROGRESS" and the number of victims.
6.  **Verify**: Once a password is entered by a victim, the ESP8266 checks it. If correct, it saves it and stops the attack.
7.  **Logs**: Go to **Show Logs** in the main menu to view captured passwords.

### Method 2: Using Web Interface
1.  Connect to the management WiFi:
    *   **SSID**: `Evil_Twins`
    *   **Password**: `chetangavali`
2.  Open a browser and go to: `http://192.168.4.1/menu`
3.  Use the **Dashboard** to:
    *   **SCAN**: Start a WiFi scan.
    *   **SELECT**: Choose a target from the results.
    *   **START/STOP**: Control the attack.
    *   **CLEAR**: Erase stored logs.
4.  Credentials will appear in the "Captured" table automatically.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1.  Fork the project.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

---

**Author**: [@chetanngavali](https://github.com/chetanngavali)  
**Version**: 1.0

