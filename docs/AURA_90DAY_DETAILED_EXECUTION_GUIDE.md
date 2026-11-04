# AURA — 90-Day Roadmap: Detailed Daily Execution Guide

**Project:** AURA — Stationary AI Desk Assistant (V1.0)
**Source of truth:** `docs/90_DAYS_ROADMAP.md`
**Related documents:** `AURA_CURRENT_STATUS.md`, `AURA_SOFTWARE_ARCHITECTURE.md`, `AURA_PINMAP_V1.md`, `AURA_V1_REQUIREMENTS.md`

---

## 1. Project Overview

AURA is a stationary AI desk assistant: an ESP32-based, networked, voice + touch + vision enabled desk 
device that senses its environment (temperature, humidity, motion), plays audio, speaks back, answers via a 
cloud AI, runs a structured UI, and can study/tutor. V1.0 explicitly excludes movement (wheels/motors/navigation).

### 1.1 Hardware inventory (V1)

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.
- **TFT** — 3.5" TFT SPI display (SPI; pins TBD until new display inspected — see AURA_PINMAP_V1.md) — UI output.
- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **DS3231** — DS3231 RTC (I2C, SDA=21, SCL=22) — time/date/alarms.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **DFPlayer** — DFPlayer Mini MP3 module (UART2, RX=16, TX=17) — audio playback.
- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.
- **INMP441** — INMP441 MEMS microphone (I2S, BCLK=26) — voice input.
- **PIR** — PIR motion sensor (currently missing) — presence detection.
- **Camera** — Camera module — vision / computer vision.
- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.
- **Buzzer** — Buzzer — boot/feedback/error tones.
- **LED** — Status LED — visual state indication.
- **Power** — Power subsystem — battery, charger, BMS, buck converter, 5V/3.3V rails.
- **Button** — Physical/touch buttons — interaction input.

> Note: Per `AURA_CURRENT_STATUS.md`, PIR and the touch controller are currently **MISSING**; a charger/battery 
> configuration discrepancy (multi-cell vs. 1S) is to be reconciled on Day 5. All other components are present.

### 1.2 Phase map

| Phase | Days | Objective |
|------:|:----:|-----------|
| Phase 1 | 1–7 | Audit & Architecture |
| Phase 2 | 8–20 | Hardware Foundation |
| Phase 3 | 21–32 | Firmware Core |
| Phase 4 | 33–42 | UI & Interaction |
| Phase 5 | 43–52 | Audio & Voice |
| Phase 6 | 53–63 | Wi-Fi, AI & Decision Engine |
| Phase 7 | 64–70 | Study & Assistant Features |
| Phase 8 | 71–77 | Camera & Computer Vision |
| Phase 9 | 78–84 | Full Integration & Casing |
| Phase 10 | 85–90 | Testing & Final Prototype |
| — | 91–180 | Future roadmap (memory, vision, smart home, security, AURA AI, product engineering) |

### 1.3 How to use this document

- One section per roadmap day **Day 1 – Day 90**, in order.
- Each day includes: **Goal / Purpose**, **Phase**, **Plan & Tasks** (from the roadmap, expanded),
  **Components & Interfaces**, **Definition of Done**, **Verification & Testing**, and **Risks / Notes**.
- "Milestone" days end a phase; a phase-level checklist is included at each phase boundary.

---

---

## Phase 1 — Audit & Architecture (Days 1–7)

**Phase Objective:** Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Phase-level verification:** 
Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

### Day 1 — PROJECT AUDIT

**Phase:** Phase 1 — Audit & Architecture (Days 1–7)

**Goal / Purpose:** Establish an exact, evidence-based baseline of what exists, works, is missing, or is unknown.

**Plan & Tasks:**

##### Goal
Determine exactly what is currently working.
##### Tasks
- Inventory every physical component.
- Separate available, missing and damaged components.
- Check existing firmware.
- Check current Git repository.
- Test currently claimed working features.
- Record broken features.
- Record untested features.
- Record missing hardware.
##### Output
Create:
AURA_CURRENT_STATUS.md
##### Status categories
- WORKING
- PARTIAL
- NOT TESTED
- FAILED
- MISSING
##### Testing
Every hardware component must receive a status.
##### End-of-day requirement
No major hardware component should remain completely unknown.

**Definition of Done:**

- Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Verification & Acceptance:**

- Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.
- **LED** — Status LED — visual state indication.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 2 — FREEZE AURA V1 REQUIREMENTS

**Phase:** Phase 1 — Audit & Architecture (Days 1–7)

**Goal / Purpose:** Freeze the V1 feature scope — what MUST ship in the 90-day prototype and what is explicitly excluded.

**Plan & Tasks:**

Define the features that MUST be part of the 90-day prototype.
##### Required
- ESP32
- 3.5" touchscreen
- Touch input
- DHT22
- DS3231
- MicroSD
- DFPlayer Mini
- Speaker
- INMP441 microphone
- Wi-Fi
- Cloud AI
- Command processing
- Decision Engine
- Error handling
- Study Mode
- PIR
- Camera
- Exhibition Mode
- Professional UI
##### Explicitly excluded
- Wheels
- Motors
- Navigation
- Obstacle avoidance
- Autonomous movement

**Definition of Done:**

- Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Verification & Acceptance:**

- Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.
- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **DS3231** — DS3231 RTC (I2C, SDA=21, SCL=22) — time/date/alarms.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **DFPlayer** — DFPlayer Mini MP3 module (UART2, RX=16, TX=17) — audio playback.
- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.
- **INMP441** — INMP441 MEMS microphone (I2S, BCLK=26) — voice input.
- **PIR** — PIR motion sensor (currently missing) — presence detection.
- **Camera** — Camera module — vision / computer vision.
- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 3 — FINAL SOFTWARE ARCHITECTURE

**Phase:** Phase 1 — Audit & Architecture (Days 1–7)

**Goal / Purpose:** Produce the final modular software architecture (folder/component layout) before major integration.

**Plan & Tasks:**

Create the following structure:
```text AURA/ ├── main.cpp ├── core/ │   ├── system/ │   ├── state_machine/ │   ├── decision_engine/ │   ├── command_manager/ │   ├── action_manager/ │   ├── response_manager/ │   ├── memory/ │   └── diagnostics/ ├── hardware/ │   ├── display/ │   ├── touch/ │   ├── audio/ │   ├── microphone/ │   ├── storage/ │   └── camera/ ├── sensors/ │   ├── dht22/ │   ├── ds3231/ │   └── pir/ ├── network/ │   ├── wifi/ │   └── api/ ├── ai/ │   ├── routing/ │   ├── language/ │   ├── speech/ │   └── vision/ ├── applications/ │   ├── assistant/ │   ├── study/ │   ├── entertainment/ │   └── exhibition/ ├── config/ ├── tests/ └── docs/ ```

**Definition of Done:**

- Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Verification & Acceptance:**

- Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **DS3231** — DS3231 RTC (I2C, SDA=21, SCL=22) — time/date/alarms.
- **PIR** — PIR motion sensor (currently missing) — presence detection.
- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 4 — PIN AND BUS AUDIT

**Phase:** Phase 1 — Audit & Architecture (Days 1–7)

**Goal / Purpose:** Document every pin, bus (GPIO/SPI/I2C/I2S/UART) and power rail to remove guesswork.

**Plan & Tasks:**

Document:
- GPIO
- SPI
- I2C
- I2S
- UART
- Power rails
- Chip-select lines
- Interrupt pins
Known interfaces:
- DS3231 → I2C
- TFT → SPI
- MicroSD → SPI
- INMP441 → I2S
- DFPlayer → UART
- PIR → GPIO
- Buzzer → GPIO
- Camera → TBD
Do NOT guess final camera pins.
Create:
AURA_PINMAP_V1.md

**Definition of Done:**

- Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Verification & Acceptance:**

- Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

**Components / Interfaces involved:**

- **TFT** — 3.5" TFT SPI display (SPI; pins TBD until new display inspected — see AURA_PINMAP_V1.md) — UI output.
- **DS3231** — DS3231 RTC (I2C, SDA=21, SCL=22) — time/date/alarms.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **DFPlayer** — DFPlayer Mini MP3 module (UART2, RX=16, TX=17) — audio playback.
- **INMP441** — INMP441 MEMS microphone (I2S, BCLK=26) — voice input.
- **PIR** — PIR motion sensor (currently missing) — presence detection.
- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.
- **Buzzer** — Buzzer — boot/feedback/error tones.
- **Power** — Power subsystem — battery, charger, BMS, buck converter, 5V/3.3V rails.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 5 — POWER AUDIT

**Phase:** Phase 1 — Audit & Architecture (Days 1–7)

**Goal / Purpose:** Determine the power budget and verify the power chain (battery, BMS, charger, regulators).

**Plan & Tasks:**

Calculate:
- ESP32 current
- Display current
- DFPlayer current
- Speaker/amplifier requirements
- Sensor consumption
- Camera consumption
- Wi-Fi consumption
Verify:
- Battery
- BMS
- Charger
- Buck converter
- 5V rail
- 3.3V rail
The current architecture uses a 2S Li-ion battery concept with proper 2S BMS/charging and regulated rails.

**Definition of Done:**

- Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Verification & Acceptance:**

- Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.
- **DFPlayer** — DFPlayer Mini MP3 module (UART2, RX=16, TX=17) — audio playback.
- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.
- **Camera** — Camera module — vision / computer vision.
- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.
- **Power** — Power subsystem — battery, charger, BMS, buck converter, 5V/3.3V rails.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 6 — GITHUB SETUP

**Phase:** Phase 1 — Audit & Architecture (Days 1–7)

**Goal / Purpose:** Set up the Git repository, branch strategy and documentation standards for the whole project.

**Plan & Tasks:**

Create:
main develop feature/* hardware/* docs/*
Commit style:
feat: add camera driver fix: repair touch calibration docs: update pin map test: add DHT22 test refactor: improve command manager
Create:
- README.md
- CHANGELOG.md
- CONTRIBUTING.md
- /docs
- /hardware
- /firmware
- /tests

**Definition of Done:**

- Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Verification & Acceptance:**

- Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 7 — WEEK 1 REVIEW

**Phase:** Phase 1 — Audit & Architecture (Days 1–7)

**Goal / Purpose:** Review week 1: confirm architecture/plan are frozen before integration begins; resolve conflicts.

**Plan & Tasks:**

##### Must be completed
- Hardware inventory
- Architecture
- Pin map
- Power plan
- Git repository
- Feature scope
##### Checkpoint
AURA architecture must be frozen before major integration begins.
##### Backup plan
If major hardware conflicts are discovered:
- Stop integration.
- Fix wiring/pin allocation.
- Re-test power.
- Update documentation.

**Definition of Done:**

- Audit evidence recorded (AURA_CURRENT_STATUS.md), V1 scope frozen, architecture & pinmap approved, Git repository initialized.

**Verification & Acceptance:**

- Cross-check physical hardware vs. documentation; identify missing/damaged/untested items; verify Git and firmware baseline.

**Components / Interfaces involved:**

- **Power** — Power subsystem — battery, charger, BMS, buck converter, 5V/3.3V rails.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 2 — Hardware Foundation (Days 8–20)

**Phase Objective:** Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Phase-level verification:** 
Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

### Day 8 — ESP32 BASE SYSTEM

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Bring up the ESP32 base system: init, serial logging, config, boot diagnostics and heartbeat.

**Plan & Tasks:**

Implement:
- ESP32 initialization
- Serial logging
- Configuration system
- Boot diagnostics
- System heartbeat
Expected boot:
AURA BOOT ESP32: OK Memory: OK Config: OK

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 9 — GPIO + BUZZER

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Implement and validate GPIO handling, the buzzer and (if available) a status LED.

**Plan & Tasks:**

Implement:
- GPIO testing
- Buzzer control
- Status LED if available
Test:
- startup beep
- button/touch feedback
- error beep

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.
- **Buzzer** — Buzzer — boot/feedback/error tones.
- **LED** — Status LED — visual state indication.
- **Button** — Physical/touch buttons — interaction input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 10 — DHT22

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Get the DHT22 temperature/humidity sensor working with validation and failure detection.

**Plan & Tasks:**

Implement:
- temperature reading
- humidity reading
- sensor validation
- sensor failure detection
Testing:
- 30-minute stability test
- disconnected sensor test

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 11 — DS3231

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Get the DS3231 RTC working: time/date read/write, persistence and alarm foundation.

**Plan & Tasks:**

Implement:
- time
- date
- RTC reading
- RTC setting
- alarm foundation
Test:
- power cycle
- time persistence
- alarm trigger

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **DS3231** — DS3231 RTC (I2C, SDA=21, SCL=22) — time/date/alarms.
- **Power** — Power subsystem — battery, charger, BMS, buck converter, 5V/3.3V rails.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 12 — SPI BUS

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Bring up the SPI bus shared by TFT and MicroSD; verify chip-select isolation and stability.

**Plan & Tasks:**

Bring up:
- TFT
- MicroSD
Verify:
- chip-select lines
- bus stability
- simultaneous operation

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **TFT** — 3.5" TFT SPI display (SPI; pins TBD until new display inspected — see AURA_PINMAP_V1.md) — UI output.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 13 — TFT DISPLAY

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Implement the TFT display driver primitives: init, text, shapes, icons, clearing, rendering.

**Plan & Tasks:**

Implement:
- initialization
- text
- rectangles
- icons
- screen clearing
- basic rendering

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **TFT** — 3.5" TFT SPI display (SPI; pins TBD until new display inspected — see AURA_PINMAP_V1.md) — UI output.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 14 — TOUCHSCREEN

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Implement touch reading, calibration, debounce and touch-button handling plus a diagnostic screen.

**Plan & Tasks:**

Implement:
- touch coordinate reading
- calibration
- debounce
- touch buttons
Create a touch diagnostic screen.

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **Button** — Physical/touch buttons — interaction input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 15 — MICROSD

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Implement MicroSD: mount, read/write, listing, config files and logs; handle card errors.

**Plan & Tasks:**

Implement:
- mount
- read
- write
- file listing
- configuration files
- logs
Test:
- card inserted
- card removed
- invalid file
- write failure

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 16 — DFPLAYER MINI

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Bring up the DFPlayer Mini: init, play/stop/next/previous and volume control.

**Plan & Tasks:**

Implement:
- initialization
- play
- stop
- next
- previous
- volume

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **DFPlayer** — DFPlayer Mini MP3 module (UART2, RX=16, TX=17) — audio playback.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 17 — SPEAKER

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Test the speaker output chain for speech, music, sound effects and volume control.

**Plan & Tasks:**

Test:
- speech
- music
- sound effects
- volume control

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 18 — INMP441

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Bring up the INMP441 microphone over I2S: capture, buffering and audio diagnostics.

**Plan & Tasks:**

Implement:
- I2S initialization
- microphone capture
- audio buffer
- audio diagnostics
The INMP441 provides digital I2S audio directly to the ESP32.

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.
- **INMP441** — INMP441 MEMS microphone (I2S, BCLK=26) — voice input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 19 — PIR

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Implement PIR motion detection with debounce, event generation and notification.

**Plan & Tasks:**

Implement:
- motion detection
- debounce
- event generation
- notification
Example:
"Motion detected."

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **PIR** — PIR motion sensor (currently missing) — presence detection.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 20 — HARDWARE INTEGRATION TEST

**Phase:** Phase 2 — Hardware Foundation (Days 8–20)

**Goal / Purpose:** Integrate and test all hardware together as one system; find interface conflicts.

**Plan & Tasks:**

Test:
ESP32       ✓ TFT         ✓ Touch       ✓ DHT22       ✓ DS3231      ✓ MicroSD     ✓ DFPlayer    ✓ Speaker     ✓ INMP441     ✓ PIR         ✓ Power       ✓
Camera is handled separately.

**Definition of Done:**

- Each hardware driver implemented on real hardware, tested in isolation, and a passing hardware integration test available.

**Verification & Acceptance:**

- Per-component functional tests on bench hardware; sensor validation and failure detection; bus stability checks.

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.
- **TFT** — 3.5" TFT SPI display (SPI; pins TBD until new display inspected — see AURA_PINMAP_V1.md) — UI output.
- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **DS3231** — DS3231 RTC (I2C, SDA=21, SCL=22) — time/date/alarms.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **DFPlayer** — DFPlayer Mini MP3 module (UART2, RX=16, TX=17) — audio playback.
- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.
- **INMP441** — INMP441 MEMS microphone (I2S, BCLK=26) — voice input.
- **PIR** — PIR motion sensor (currently missing) — presence detection.
- **Camera** — Camera module — vision / computer vision.
- **LED** — Status LED — visual state indication.
- **Power** — Power subsystem — battery, charger, BMS, buck converter, 5V/3.3V rails.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 3 — Firmware Core (Days 21–32)

**Phase Objective:** Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Phase-level verification:** 
Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

### Day 21 — CODE REFACTOR

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Refactor code for clarity, modularity and maintainability before feature growth.

**Plan & Tasks:**

Separate:
- hardware
- sensors
- UI
- audio
- network
- AI
- applications

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 22 — HARDWARE ABSTRACTION

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Introduce a hardware abstraction layer so drivers are swappable and testable.

**Plan & Tasks:**

Create interfaces:
Display Audio Sensor RTC Storage Microphone Camera

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **Camera** — Camera module — vision / computer vision.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 23 — CONFIGURATION SYSTEM

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Build the configuration system: storage, defaults, load/save and validation on SD.

**Plan & Tasks:**

Store:
- Wi-Fi settings
- volume
- brightness
- timezone
- user preferences
- API configuration
Do not hard-code everything into main.cpp.

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 24 — LOGGING

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Implement a logging framework (INFO/WARNING/ERROR/DEBUG) with timestamps and destinations.

**Plan & Tasks:**

Implement:
INFO WARNING ERROR DEBUG
Example:
[INFO] DHT22 initialized [INFO] WiFi connected [WARN] AI timeout [ERROR] SD unavailable

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 25 — SYSTEM STATE MACHINE

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Implement the system state machine that governs AURA behaviour across all states.

**Plan & Tasks:**

Implement:
BOOT ↓ IDLE ↓ LISTENING ↓ UNDERSTANDING ↓ DECIDING ↓ EXECUTING ↓ RESPONDING ↓ IDLE

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 26 — LOCAL COMMAND ROUTER

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Route localized commands to the correct handlers (time, date, temp, humidity, etc.).

**Plan & Tasks:**

Implement commands for:
- time
- date
- temperature
- humidity
- volume
- music
- system status

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 27 — ACTION MANAGER

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Build the action manager: execute verified actions and expose command feedback.

**Plan & Tasks:**

Architecture:
Command ↓ Action Manager ↓ Hardware/Application
Commands should not directly control hardware.

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 28 — RESPONSE MANAGER

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Build the response manager: turn action results into structured user-facing responses.

**Plan & Tasks:**

Decide whether a response goes to:
- TFT
- Speaker
- Buzzer
- Multiple outputs

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **TFT** — 3.5" TFT SPI display (SPI; pins TBD until new display inspected — see AURA_PINMAP_V1.md) — UI output.
- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.
- **Buzzer** — Buzzer — boot/feedback/error tones.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 29 — ERROR MANAGER

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Build the error manager: normalize and handle sensor, SD, audio, Wi-Fi and invalid-command failures.

**Plan & Tasks:**

Handle:
- sensor failure
- SD failure
- audio failure
- Wi-Fi failure
- invalid command
- AI timeout

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 30 — WATCHDOG AND RECOVERY

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Add a watchdog and recovery mechanism so AURA restarts safely on hangs/faults.

**Plan & Tasks:**

Implement:
- watchdog
- safe restart
- recovery state
- startup diagnostics

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 31 — DEVELOPER DIAGNOSTICS

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Expose developer diagnostics (system test screen/tool) for hardware and firmware checks.

**Plan & Tasks:**

Create:
```text SYSTEM TEST ├── Display ├── Touch ├── DHT22 ├── RTC ├── SD ├── Audio ├── Microphone ├── PIR ├── Wi-Fi └── Camera ```

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **PIR** — PIR motion sensor (currently missing) — presence detection.
- **Camera** — Camera module — vision / computer vision.
- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 32 — FIRMWARE MILESTONE

**Phase:** Phase 3 — Firmware Core (Days 21–32)

**Goal / Purpose:** Firmware milestone: freeze the core firmware and run a full system self-test.

**Plan & Tasks:**

##### Milestone
AURA must:
- boot reliably
- detect hardware
- display system status
- execute local commands
- handle basic failures
- recover from common errors

**Definition of Done:**

- Firmware core modules (config, logging, state machine, command/action/response/error/watchdog) implemented and unit-tested.

**Verification & Acceptance:**

- Unit tests + serial diagnostics for each module; boot loop verification; fault injection where applicable.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 4 — UI & Interaction (Days 33–42)

**Phase Objective:** UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Phase-level verification:** 
Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

### Day 33 — UI DESIGN SYSTEM

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Create the UI design system: style guide, components, spacing, fonts and theme.

**Plan & Tasks:**

Define:
- fonts
- colors
- buttons
- icons
- spacing
- navigation
- status indicators

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **Button** — Physical/touch buttons — interaction input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 34 — BOOT SCREEN

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Implement the boot screen with branding and boot-status feedback.

**Plan & Tasks:**

Create:
AURA AI DESK ASSISTANT
Initializing...

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 35 — HOME SCREEN

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Implement the home screen hub and primary navigation.

**Plan & Tasks:**

Show:
- time
- temperature
- Wi-Fi status
- system status
- quick actions

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 36 — ENVIRONMENT DASHBOARD

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Implement the environment dashboard (temperature/humidity/motion readings).

**Plan & Tasks:**

Display:
Temperature Humidity Motion Time

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 37 — AI SCREEN

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Implement the AI screen for AI interaction and status.

**Plan & Tasks:**

Create:
- input
- processing state
- response
- error state

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 38 — AUDIO SCREEN

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Implement the audio screen (playback controls and status).

**Plan & Tasks:**

Create:
- play
- pause
- next
- previous
- volume

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 39 — SETTINGS

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Implement the settings screen (config options).

**Plan & Tasks:**

Add:
- brightness
- volume
- Wi-Fi
- time
- system information

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 40 — NOTIFICATIONS

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Implement the notifications screen and shared notification system.

**Plan & Tasks:**

Create notifications for:
- alarms
- reminders
- sensor alerts
- errors
- AI errors

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 41 — UI TESTING

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** Test all UI screens thoroughly; capture and fix visual/interaction defects.

**Plan & Tasks:**

Test:
- every button
- every screen
- navigation
- back button
- invalid actions
- accidental touches

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **Button** — Physical/touch buttons — interaction input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 42 — UI MILESTONE

**Phase:** Phase 4 — UI & Interaction (Days 33–42)

**Goal / Purpose:** UI milestone: freeze screens and pass a complete UI review.

**Plan & Tasks:**

AURA should now look and behave like a real desktop electronic product even without advanced AI.

**Definition of Done:**

- UI design system and all screens implemented; screens tested on-g target; UI milestone passed.

**Verification & Acceptance:**

- Manual UI walk-through of every screen; touch calibration accuracy; rendering/refresh performance checks.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 5 — Audio & Voice (Days 43–52)

**Phase Objective:** Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Phase-level verification:** 
Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

### Day 43 — MICROPHONE PIPELINE

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Build the microphone capture pipeline (sample, buffer, noise handling).

**Plan & Tasks:**

Implement:
INMP441 ↓ I2S ↓ Audio Buffer

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **INMP441** — INMP441 MEMS microphone (I2S, BCLK=26) — voice input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 44 — SPEECH-TO-TEXT STRATEGY

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Select and validate the speech-to-text strategy for the ESP32+cloud stack.

**Plan & Tasks:**

Determine whether STT uses:
- cloud service
- external computer
- additional processing hardware
- local lightweight processing
Do not assume that the ESP32 can run a modern speech-recognition model by itself.

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 45 — BASIC VOICE COMMANDS

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Implement basic voice commands that route to the command manager.

**Plan & Tasks:**

Implement:
"What time is it?"
"Show temperature."
"Play music."
"What's the humidity?"

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 46 — COMMAND CLASSIFICATION

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Implement command classification so voice/intents map reliably to actions.

**Plan & Tasks:**

Classify requests into:
LOCAL CLOUD AI SYSTEM STUDY VISION ASSISTANT

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 47 — VOICE → LOCAL COMMAND

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Complete the voice prototype chain: voice -> STT -> command -> router -> action.

**Plan & Tasks:**

Implement:
Voice ↓ STT ↓ Command ↓ Router ↓ Action

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 48 — VOICE RESPONSE

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Implement the voice response chain: command -> response -> TFT + speaker.

**Plan & Tasks:**

Implement:
Command ↓ Response ↓ TFT + Speaker

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **TFT** — 3.5" TFT SPI display (SPI; pins TBD until new display inspected — see AURA_PINMAP_V1.md) — UI output.
- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 49 — VOICE ERROR HANDLING

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Add voice error handling: no speech, unknown speech, API failure, timeout, poor recognition.

**Plan & Tasks:**

Handle:
- no speech
- unknown speech
- API failure
- timeout
- poor recognition

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 50 — WAKE WORD PROTOTYPE

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Prototype the "AURA" wake word that switches the system into listening mode.

**Plan & Tasks:**

Attempt:
"AURA"
↓ Listening
If wake-word detection is unreliable, retain push-to-talk as the fallback.

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 51 — VOICE STRESS TEST

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Harden the voice pipeline and wake word reliability (timing, noise, retries).

**Plan & Tasks:**

Test:
- quiet room
- noisy room
- different distances
- different speakers
- repeated commands

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 52 — VOICE MILESTONE

**Phase:** Phase 5 — Audio & Voice (Days 43–52)

**Goal / Purpose:** Audio & voice milestone: demonstrate reliable end-to-end voice interaction.

**Plan & Tasks:**

AURA must successfully:
HEAR ↓ UNDERSTAND ↓ EXECUTE ↓ RESPOND
for a controlled command set.

**Definition of Done:**

- Microphone pipeline, STT, command classification, voice response and wake-word prototype operate end-to-end.

**Verification & Acceptance:**

- Live voice round-trip tests; STT accuracy; error handling for silence/unknown/malformed input.

**Components / Interfaces involved:**

- **LED** — Status LED — visual state indication.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Phase Objective:** Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Phase-level verification:** 
Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

### Day 53 — WIFI MANAGER

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Connect Wi-Fi reliably: connection lifecycle, retries and status reporting.

**Plan & Tasks:**

Implement:
- connect
- reconnect
- status
- timeout
- connection failure

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 54 — INTERNET DIAGNOSTICS

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Integrate the cloud AI/LLM API: request, response, parsing and error handling.

**Plan & Tasks:**

Display:
Wi-Fi: Connected Internet: Available AI: Available

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Components / Interfaces involved:**

- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 55 — API LAYER

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Drive AI conversation flow with the command/system context.

**Plan & Tasks:**

Implement:
- HTTP/HTTPS
- GET
- POST
- JSON
- timeouts
- retries

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 56 — AI REQUEST MANAGER

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Implement timeouts and request management for cloud AI calls.

**Plan & Tasks:**

Architecture:
User Input ↓ Prompt Builder ↓ API Request ↓ Response Parser

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 57 — AI DISPLAY

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Add offline fallback behavior when AI is unreachable.

**Plan & Tasks:**

Display:
User: What is artificial intelligence?
AURA: Artificial intelligence is...

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 58 — AI AUDIO

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Generate AI audio responses (TTS) and play them through the speaker.

**Plan & Tasks:**

Connect AI responses to:
- display
- speech output
- audio feedback

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 59 — AI FAILURE HANDLING

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Implement AI failure handling: fallbacks, retries and user-visible messages.

**Plan & Tasks:**

If internet fails:
Internet unavailable. Switching to offline mode.
Offline mode continues supporting predefined commands.

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 60 — DECISION ENGINE

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Implement the Decision Engine that routes intents to actions across subsystems.

**Plan & Tasks:**

Architecture:
INPUT ↓ CLASSIFY ↓ INTENT ↓ DECISION ↓ ACTION ↓ RESPONSE

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 61 — SHORT-TERM CONTEXT

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Integrate the Decision Engine with voice, UI and AI responses.

**Plan & Tasks:**

Implement context such as:
User: "What is the temperature?"
AURA: "24°C."
User: "Is that normal?"
AURA understands "that" refers to temperature.

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 62 — MEMORY FOUNDATION

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Handle multi-intent and follow-up interactions in the decision flow.

**Plan & Tasks:**

Store:
- settings
- preferences
- study subject
- recent events
- limited conversation context
Use SD/non-volatile storage where appropriate.

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Components / Interfaces involved:**

- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 63 — INTELLIGENCE MILESTONE

**Phase:** Phase 6 — Wi-Fi, AI & Decision Engine (Days 53–63)

**Goal / Purpose:** Wi-Fi/AI/Decision milestone: demonstrate the integrated AI decision loop.

**Plan & Tasks:**

AURA should now function as one assistant instead of a collection of unrelated features.

**Definition of Done:**

- Wi-Fi/cloud AI integration, AI audio, AI failure handling and the Decision Engine are implemented and verified.

**Verification & Acceptance:**

- Repeated AI calls; offline-fallback behavior; timeout/error recovery; decision engine logic tests.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 7 — Study & Assistant Features (Days 64–70)

**Phase Objective:** Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Phase-level verification:** 
Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

### Day 64 — STUDY ARCHITECTURE

**Phase:** Phase 7 — Study & Assistant Features (Days 64–70)

**Goal / Purpose:** Implement Study Mode baseline: subject content and learning interaction.

**Plan & Tasks:**

Study Mode:
Study ├── Subjects ├── Lessons ├── Quiz ├── Score ├── Timer └── Progress

**Definition of Done:**

- Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Verification & Acceptance:**

- Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 65 — SUBJECTS

**Phase:** Phase 7 — Study & Assistant Features (Days 64–70)

**Goal / Purpose:** Add Study Mode quiz/practice mechanics.

**Plan & Tasks:**

Initial subjects:
- Science
- Mathematics
- Computer/IT
- General Knowledge

**Definition of Done:**

- Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Verification & Acceptance:**

- Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

**Components / Interfaces involved:**

- **LED** — Status LED — visual state indication.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 66 — LEARNING MODE

**Phase:** Phase 7 — Study & Assistant Features (Days 64–70)

**Goal / Purpose:** Add Study Mode progress tracking and feedback.

**Plan & Tasks:**

Implement:
- explanations
- examples
- follow-up questions
- simple educational conversations

**Definition of Done:**

- Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Verification & Acceptance:**

- Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 67 — QUIZ ENGINE

**Phase:** Phase 7 — Study & Assistant Features (Days 64–70)

**Goal / Purpose:** Implement the alarm feature (set, trigger, dismiss, UI).

**Plan & Tasks:**

Implement:
- question database
- random questions
- multiple-choice answers
- answer validation
- score
- difficulty

**Definition of Done:**

- Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Verification & Acceptance:**

- Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 68 — STUDY TIMER

**Phase:** Phase 7 — Study & Assistant Features (Days 64–70)

**Goal / Purpose:** Implement the timer feature (countdown, completion alert).

**Plan & Tasks:**

Implement:
- timer
- Pomodoro
- completion alert

**Definition of Done:**

- Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Verification & Acceptance:**

- Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 69 — VOICE + STUDY

**Phase:** Phase 7 — Study & Assistant Features (Days 64–70)

**Goal / Purpose:** Implement reminders and their notifications.

**Plan & Tasks:**

Examples:
"Start Science quiz."
"Explain photosynthesis."
"Ask me a mathematics question."

**Definition of Done:**

- Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Verification & Acceptance:**

- Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 70 — STUDY MILESTONE

**Phase:** Phase 7 — Study & Assistant Features (Days 64–70)

**Goal / Purpose:** Study/assistant milestone: feature-complete assistant area works end-to-end.

**Plan & Tasks:**

AURA must demonstrate:
Subject ↓ Learn ↓ Ask ↓ Quiz ↓ Score ↓ Progress

**Definition of Done:**

- Study mode and assistant features (alarm, timer, reminders, notifications) are implemented and tested.

**Verification & Acceptance:**

- Feature acceptance tests (alarm triggers, timer countdown, reminders fire, notifications display).

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 8 — Camera & Computer Vision (Days 71–77)

**Phase Objective:** Camera capture and basic computer vision working with a demonstrated use case.

**Phase-level verification:** 
Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

### Day 71 — CAMERA HARDWARE VERIFICATION

**Phase:** Phase 8 — Camera & Computer Vision (Days 71–77)

**Goal / Purpose:** Bring up camera capture and preview.

**Plan & Tasks:**

Confirm:
- camera model
- voltage
- interface
- resolution
- frame rate
- memory requirements
- ESP32 compatibility
The exact camera model remains a design decision; the current documentation gives OV2640/OV7670-class options and notes that processing headroom must be verified.

**Definition of Done:**

- Camera capture and basic computer vision working with a demonstrated use case.

**Verification & Acceptance:**

- Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.
- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 72 — CAMERA COMMUNICATION

**Phase:** Phase 8 — Camera & Computer Vision (Days 71–77)

**Goal / Purpose:** Add basic computer vision processing (frame analysis).

**Plan & Tasks:**

Implement:
Camera ↓ Frame Capture ↓ Buffer

**Definition of Done:**

- Camera capture and basic computer vision working with a demonstrated use case.

**Verification & Acceptance:**

- Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

**Components / Interfaces involved:**

- **Camera** — Camera module — vision / computer vision.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 73 — IMAGE CAPTURE

**Phase:** Phase 8 — Camera & Computer Vision (Days 71–77)

**Goal / Purpose:** Implement face/person detection (minimum viable).

**Plan & Tasks:**

Implement:
- capture frame
- display image
- optionally save image
- memory monitoring

**Definition of Done:**

- Camera capture and basic computer vision working with a demonstrated use case.

**Verification & Acceptance:**

- Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 74 — BASIC COMPUTER VISION

**Phase:** Phase 8 — Camera & Computer Vision (Days 71–77)

**Goal / Purpose:** Implement object classification baseline.

**Plan & Tasks:**

Start with lightweight tasks:
- color detection
- QR detection
- simple image analysis

**Definition of Done:**

- Camera capture and basic computer vision working with a demonstrated use case.

**Verification & Acceptance:**

- Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 75 — OBJECT/PERSON DETECTION FEASIBILITY

**Phase:** Phase 8 — Camera & Computer Vision (Days 71–77)

**Goal / Purpose:** Wire camera results into the assistant context.

**Plan & Tasks:**

Benchmark:
- FPS
- RAM
- CPU
- latency
- heat
- reliability
Do not force advanced computer vision if the ESP32 cannot handle it reliably.

**Definition of Done:**

- Camera capture and basic computer vision working with a demonstrated use case.

**Verification & Acceptance:**

- Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

**Components / Interfaces involved:**

- **ESP32** — ESP32 MCU (Wi-Fi + Bluetooth) — the main controller.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 76 — VISION → AURA BRAIN

**Phase:** Phase 8 — Camera & Computer Vision (Days 71–77)

**Goal / Purpose:** Stress-test vision under real desk lighting/scenarios.

**Plan & Tasks:**

Architecture:
Camera ↓ Vision Processing ↓ Event ↓ Decision Engine ↓ Response
Example:
Person detected.
AURA:
"Hello."

**Definition of Done:**

- Camera capture and basic computer vision working with a demonstrated use case.

**Verification & Acceptance:**

- Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

**Components / Interfaces involved:**

- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 77 — VISION MILESTONE

**Phase:** Phase 8 — Camera & Computer Vision (Days 71–77)

**Goal / Purpose:** Vision milestone: demonstrate at least one useful visual capability.

**Plan & Tasks:**

Minimum requirement:
Camera ↓ Image processing ↓ Useful result
Stretch goal:
Object/person detection.

**Definition of Done:**

- Camera capture and basic computer vision working with a demonstrated use case.

**Verification & Acceptance:**

- Capture quality; detection accuracy; edge-case handling (low light, empty frame, disconnect).

**Components / Interfaces involved:**

- **Camera** — Camera module — vision / computer vision.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 9 — Full Integration & Casing (Days 78–84)

**Phase Objective:** All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Phase-level verification:** 
Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

### Day 78 — MASTER INTEGRATION

**Phase:** Phase 9 — Full Integration & Casing (Days 78–84)

**Goal / Purpose:** Begin full system integration: all subsystems running together.

**Plan & Tasks:**

Connect:
- Voice
- Touch
- Camera
- Sensors
- AI
- Decision Engine
- Display
- Audio
- Storage
- Notifications

**Definition of Done:**

- All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Verification & Acceptance:**

- Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 79 — EXHIBITION MODE

**Phase:** Phase 9 — Full Integration & Casing (Days 78–84)

**Goal / Purpose:** Implement Exhibition Mode (self-running showcase behaviour).

**Plan & Tasks:**

Create:
AURA DEMO
├── AI ├── VISION ├── ENVIRONMENT ├── STUDY ├── MY BRAIN └── AUDIO
Visitors should be able to understand the project quickly.

**Definition of Done:**

- All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Verification & Acceptance:**

- Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 80 — MY BRAIN MODE

**Phase:** Phase 9 — Full Integration & Casing (Days 78–84)

**Goal / Purpose:** Implement My Brain Mode (insight/status mode).

**Plan & Tasks:**

Create the core demonstration:
SENSE ↓ UNDERSTAND ↓ THINK ↓ DECIDE ↓ ACT ↓ RESPOND

**Definition of Done:**

- All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Verification & Acceptance:**

- Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 81 — AUTOMATIC DEMO

**Phase:** Phase 9 — Full Integration & Casing (Days 78–84)

**Goal / Purpose:** Implement the automatic demonstration sequence.

**Plan & Tasks:**

Create a guided automatic demonstration.
The demo should require minimal operator interaction.

**Definition of Done:**

- All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Verification & Acceptance:**

- Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 82 — PHYSICAL ASSEMBLY

**Phase:** Phase 9 — Full Integration & Casing (Days 78–84)

**Goal / Purpose:** Physically assemble the hardware into enclosure-ready form.

**Plan & Tasks:**

Move from temporary wiring to:
- secured wiring
- connectors
- mounting
- cable management
- serviceability

**Definition of Done:**

- All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Verification & Acceptance:**

- Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 83 — CASING

**Phase:** Phase 9 — Full Integration & Casing (Days 78–84)

**Goal / Purpose:** Build/refine the casing and physical arrangement.

**Plan & Tasks:**

Build the first functional enclosure.
Required areas:
- display opening
- camera mount
- speaker grille
- microphone opening
- sensor openings
- ventilation
- charging/USB access
- service panel
- cable routing

**Definition of Done:**

- All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Verification & Acceptance:**

- Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

**Components / Interfaces involved:**

- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.
- **Camera** — Camera module — vision / computer vision.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 84 — PHYSICAL INTEGRATION MILESTONE

**Phase:** Phase 9 — Full Integration & Casing (Days 78–84)

**Goal / Purpose:** Physical integration milestone: complete assembled prototype running.

**Plan & Tasks:**

AURA must exist as one integrated desktop device.
No loose critical wiring should remain where it can easily disconnect during demonstration.

**Definition of Done:**

- All subsystems integrated into the casing; physical integration milestone passed; full-system smoke test green.

**Verification & Acceptance:**

- Full-system integration smoke test; wiring/thermal checks; casing fit and cable management review.

**Components / Interfaces involved:**

- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

---

## Phase 10 — Testing & Final Prototype (Days 85–90)

**Phase Objective:** Hardware/software/long-duration/failure tests pass; demo rehearsed; V1.0 frozen and documented.

**Phase-level verification:** 
Long-duration soak (8–12h), intentional failure tests, restart tests, full demo rehearsal, release checklist.

### Day 85 — HARDWARE TEST

**Phase:** Phase 10 — Testing & Final Prototype (Days 85–90)

**Goal / Purpose:** Run a full hardware test pass on the assembled unit.

**Plan & Tasks:**

Check:
- power
- display
- touch
- DHT22
- DS3231
- SD
- DFPlayer
- speaker
- microphone
- PIR
- camera

**Definition of Done:**

- Hardware/software/long-duration/failure tests pass; demo rehearsed; V1.0 frozen and documented.

**Verification & Acceptance:**

- Long-duration soak (8–12h), intentional failure tests, restart tests, full demo rehearsal, release checklist.

**Components / Interfaces involved:**

- **Touch** — Touchscreen controller (currently missing / to be acquired) — input.
- **DHT22** — DHT22 temperature & humidity sensor — environment monitoring.
- **DS3231** — DS3231 RTC (I2C, SDA=21, SCL=22) — time/date/alarms.
- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **DFPlayer** — DFPlayer Mini MP3 module (UART2, RX=16, TX=17) — audio playback.
- **Speaker** — Speaker + amplifier (PAM8403 class) — voice/music/sound FX.
- **PIR** — PIR motion sensor (currently missing) — presence detection.
- **Camera** — Camera module — vision / computer vision.
- **Power** — Power subsystem — battery, charger, BMS, buck converter, 5V/3.3V rails.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 86 — SOFTWARE TEST

**Phase:** Phase 10 — Testing & Final Prototype (Days 85–90)

**Goal / Purpose:** Run a full software test pass on the integrated firmware.

**Plan & Tasks:**

Check:
- boot
- UI
- commands
- AI
- memory
- Study Mode
- camera
- error handling
- recovery

**Definition of Done:**

- Hardware/software/long-duration/failure tests pass; demo rehearsed; V1.0 frozen and documented.

**Verification & Acceptance:**

- Long-duration soak (8–12h), intentional failure tests, restart tests, full demo rehearsal, release checklist.

**Components / Interfaces involved:**

- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 87 — LONG-DURATION TEST

**Phase:** Phase 10 — Testing & Final Prototype (Days 85–90)

**Goal / Purpose:** Run a long-duration (8–12h) stability and soak test.

**Plan & Tasks:**

Target:
8–12 hours minimum if practical.
Monitor:
- crashes
- memory
- temperature
- Wi-Fi
- SD
- sensors
- audio
- camera

**Definition of Done:**

- Hardware/software/long-duration/failure tests pass; demo rehearsed; V1.0 frozen and documented.

**Verification & Acceptance:**

- Long-duration soak (8–12h), intentional failure tests, restart tests, full demo rehearsal, release checklist.

**Components / Interfaces involved:**

- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **Camera** — Camera module — vision / computer vision.
- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 88 — FAILURE TESTING

**Phase:** Phase 10 — Testing & Final Prototype (Days 85–90)

**Goal / Purpose:** Run intentional failure testing across Wi-Fi, AI, SD, sensor, camera, command and restart.

**Plan & Tasks:**

Intentionally test:
- Wi-Fi disconnected
- AI unavailable
- SD removed
- sensor disconnected
- camera unavailable
- invalid command
- unexpected restart
AURA must fail gracefully.

**Definition of Done:**

- Hardware/software/long-duration/failure tests pass; demo rehearsed; V1.0 frozen and documented.

**Verification & Acceptance:**

- Long-duration soak (8–12h), intentional failure tests, restart tests, full demo rehearsal, release checklist.

**Components / Interfaces involved:**

- **SD** — MicroSD (SPI, CS=5) — configuration storage + logs.
- **Camera** — Camera module — vision / computer vision.
- **Wi-Fi** — Wi-Fi (ESP32 internal) — connectivity and cloud AI calls.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 89 — DEMONSTRATION REHEARSAL

**Phase:** Phase 10 — Testing & Final Prototype (Days 85–90)

**Goal / Purpose:** Rehearse the complete demonstration repeatedly and fix issues.

**Plan & Tasks:**

Run the complete demonstration repeatedly.
Fix:
- slow transitions
- crashes
- confusing UI
- audio problems
- camera problems
- network failures

**Definition of Done:**

- Hardware/software/long-duration/failure tests pass; demo rehearsed; V1.0 frozen and documented.

**Verification & Acceptance:**

- Long-duration soak (8–12h), intentional failure tests, restart tests, full demo rehearsal, release checklist.

**Components / Interfaces involved:**

- **Camera** — Camera module — vision / computer vision.
- **AI** — Cloud AI / LLM APIs — language, decision and response intelligence.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.

### Day 90 — AURA V1.0 RELEASE

**Phase:** Phase 10 — Testing & Final Prototype (Days 85–90)

**Goal / Purpose:** Freeze the AURA V1.0 prototype and produce release documentation/artifacts.

**Plan & Tasks:**

Freeze the prototype.
Create:
```text AURA V1.0 ├── Firmware ├── Hardware ├── Documentation ├── Wiring Diagram ├── Pin Map ├── BOM ├── Demo Script ├── Known Issues └── Future Roadmap ```

**Definition of Done:**

- Hardware/software/long-duration/failure tests pass; demo rehearsed; V1.0 frozen and documented.

**Verification & Acceptance:**

- Long-duration soak (8–12h), intentional failure tests, restart tests, full demo rehearsal, release checklist.

**Risks / Notes:**

- Component availability/unknowns (e.g. missing sensor) must be flagged to the current-status log.


## Appendix A — Day 90 Release Artifacts

Freeze the V1.0 prototype and produce: Firmware, Hardware, Documentation, Wiring Diagram, Pin Map, BOM, 
Demo Script, Known Issues, and the Future Roadmap. Run the Day-90 final checklist (hardware, software, 
reliability, exhibition, documentation).

## Appendix B — Days 91–180 (Future Roadmap)

- **91–110 Memory + Context:** persistent memory, preferences, conversation history, context, personalization, task memory.
- **111–130 Advanced Vision:** object detection, person detection, QR recognition, camera processing, multimodal AI.
- **131–145 Smart Home:** Wi-Fi devices, MQTT, HTTP IoT APIs, relays, smart lights, smart plugs.
- **146–160 Security:** PIR + camera, event detection/monitoring/logging, alerts.
- **161–175 AURA AI:** combine Speech + Vision + Language AI + Memory + Decision Engine into "AURA BRAIN".
- **176–180 Product Engineering:** casing, thermal design, PCB planning, cable management, serviceability, privacy, security, manufacturing research.
