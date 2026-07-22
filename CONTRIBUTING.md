# 🤝 Contributing to ESP8266 Evil Twin

Thank you for dedicating your time to improve this network security research simulation! Contributions from developers, designers, and documentation writers are highly valued.

---

## 🏁 Getting Started

Before you start writing code or updating directories:
1. Check the [Issues](https://github.com/chetanngavali/EVIL_TWINS_ESP8266/issues) tracker to see if there is an active discussion or issue you can address.
2. If you want to introduce a new feature or fix a bug, please open a new issue detailing your proposal first.

---

## 🔧 Development Workflow

### 🌿 Branching Model
- Always branch off of the `main` or `development` branch when implementing a feature or fixing a bug.
- Use descriptive branch names:
  - `feature/oled-custom-animation`
  - `bugfix/captive-portal-safari-redirect`
  - `docs/updating-readme`

### ✍️ Commit Messages
We follow the **Conventional Commits** specification to keep commit history readable:
- `feat(web): add dark mode styling switch`
- `fix(dns): resolve DNS packet fragmentation crash`
- `docs(readme): correct GPIO pinout assignments`
- `refactor(eeprom): optimize struct layout to save memory`

---

## 📝 Code Style & Formatting

To maintain a clean and readable codebase, please adhere to these standards:

### ⚙️ C++ / Firmware Code
- Use 2-space indentation.
- CamelCase or snake_case function naming, but keep consistent with the existing codebase styling.
- Keep comments concise and update them if they describe modified logic.

### 🌐 Frontend (HTML/CSS/JS)
- Keep files minimal and highly optimized to fit easily in the limited SPIFFS/Program memory of the ESP8266.
- Write vanilla Javascript and use standard CSS variables for styling modifications.
- Test responsive layouts on mobile devices before submitting.

---

## 🧪 Testing Your Changes

Before submitting your PR, ensure that:
1. Your code compiles cleanly with no compiler warnings (`-Wall`).
2. The physical OLED continues to render properly without overlapping text (SSID text limits).
3. The Admin panel remains responsive and does not cause a watchdog timer reset (WDT reset) on the ESP8266 under load.

---

## 🚀 Pull Request Checklist

When submitting a Pull Request, verify that:
- [ ] Your code is fully compiled and tested on physical hardware.
- [ ] Your branch is rebased onto the latest `main` branch.
- [ ] You have updated the [CHANGELOG.md](CHANGELOG.md) to reflect your changes.
- [ ] The hardware pin configurations match standard defaults unless customized.
- [ ] No personal credentials (Wi-Fi passwords, SSIDs) are committed to files.
