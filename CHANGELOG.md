# 📋 Changelog

All notable changes to this project will be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to Semantic Versioning.

---

## [Unreleased]
*Features, modifications, or fixes being tested but not yet packaged into a production binary.*

### Added
- Placeholder for upcoming UI animations.
- Planned multi-language support for the captive portal interface.

---

## [5.0.0] - 2026-07-22
*Current final release with optimized system performance, physical configuration validation, and responsive front-end dashboard.*

### Added
- Real-time password verification logic checking against authentic target networks via connection testing.
- Persistence framework reading and writing logs to the ESP8266 EEPROM.
- Edge-detection debouncing framework (500ms lockout) to prevent double-press menu skipping.
- Responsive dark/light theme options for the dashboard console.
- SSIDs/password auto-truncation for proper 128x64 px OLED alignment.

### Changed
- Refactored scanning code to run asynchronously to prevent blocking hardware thread executions.

### Fixed
- Resolved watchdog timer reset (WDT) crashes during intensive DNS routing requests.

---

## 📝 How to Update the Changelog

When preparing a new release:
1. Move the items in the **[Unreleased]** section into a new versioned header (e.g., `## [5.1.0] - YYYY-MM-DD`).
2. Create a new empty **[Unreleased]** header at the top of the file.
3. Categorize changes using:
   - `Added` for new features.
   - `Changed` for changes in existing functionality.
   - `Deprecated` for soon-to-be-removed features.
   - `Removed` for now-removed features.
   - `Fixed` for any bug fixes.
