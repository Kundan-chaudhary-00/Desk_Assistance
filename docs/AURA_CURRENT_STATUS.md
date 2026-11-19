# AURA Current Status

**Project:** AURA AI Desk Assistant
**Roadmap:** 90-Day AURA Development Roadmap
**Phase:** Phase 1 — Audit and Architecture
**Day:** 1 — Project Audit
**Status:** IN PROGRESS — Audit recorded; hardware verification and repository check complete

---

## 1. Purpose

This document records the exact current state of the AURA project at the start of development, per Day 1 of the roadmap. It answers:

- What hardware do we have, and what is its status?
- What firmware exists, and what works?
- What is the state of the Git repository?
- Which features are working, untested, broken, or missing?

**Status categories** used throughout: `WORKING`, `PARTIAL`, `NOT TESTED`, `FAILED`, `MISSING`.

---

## 2. Audit Sources

| Source | Used for |
|---|---|
| `AURA_Component_Verification.xlsx` / `.pdf` | Hardware inventory and component cross-check |
| `AURA_V1_REQUIREMENTS.md` | Frozen V1 scope reference |
| `AURA_PINMAP_V1.md` | Pin/bus assignments |
| Project repository (`src/`, module folders, git) | Firmware + version control status |

---

## 3. Hardware Inventory & Status

All components are **physically inventoried and verified present** (per the Component Verification report) unless stated otherwise.
No component is yet wired or firmware-tested — hardware bring-up begins in Phase 2 (Days 8–20).

| # | Component | Status | Notes |
|---:|---|---|---|
| 1 | ESP32 (WROOM DevKit) | NOT TESTED | Main controller. Matches V1 requirement. |
| 2 | 3.5" ILI9488 TFT with integrated touch | AVAILABLE / NOT TESTED | Confirmed 480×320 4-wire SPI module with MicroSD slot. ESP32 wiring and touch-controller identification are deferred to Days 12–14. |
| 3 | DHT22 Temperature & Humidity | NOT TESTED | GPIO 27. |
| 4 | DS3231 RTC | NOT TESTED | I²C GPIO 21 (SDA) / 22 (SCL). |
| 5 | DFPlayer Mini (MP3-TF-16P V3.0) | NOT TESTED | **Purchase link in docx is WRONG** (points to TFT screen, not DFPlayer). |
| 6 | Speaker (6Ω / 15W) | NOT TESTED | Via PAM8403 amplifier chain. |
| 7 | INMP441 Microphone | NOT TESTED | I²S GPIO 26 / 25 / 33. |
| 8 | Camera (ESP32-CAM) | NOT TESTED | Separate vision board; main-ESP32 comm method TBD. |
| 9 | MicroSD Card Reader | NOT TESTED | SPI, CS GPIO 5. |
| 10 | 5V Buzzer | NOT TESTED | GPIO 13. |
| 11 | PAM8403 Amplifier | NOT TESTED | Audio path: DFPlayer → PAM8403 → Speaker. |
| 12 | Buck Converter (LM2596) | VERIFIED PLAN | 5 V output confirmed; load and thermal testing occur during hardware integration. |
| 13 | AQI Sensor (MQ-135) | EXTRA | In docx but **OUTSIDE frozen V1 scope**. Do not integrate during the 90-day roadmap without approval. |
| 14 | Battery Cells (4× 18650) | VERIFIED PLAN | Confirmed 2S2P pack: 7.4 V nominal, 8.4 V full, 6000 mAh; see `AURA_POWER_AUDIT.md`. |

### Missing / damaged hardware
- **Missing components:** None recorded.
- **Damaged components:** None reported.
- **Out-of-scope extras:** AQI MQ-135 (13) — flagged, not part of V1.

---

## 4. Firmware Status

| Area | Status | Detail |
|---|---|---|
| `src/main.cpp` | PARTIAL | **Default PlatformIO template only** (empty `setup()`/`loop()`, demo `myFunction()`). No AURA logic. |
| `core/` (system, state_machine, decision_engine, command_manager, action_manager, response_manager, memory, diagnostics) | EMPTY SCAFFOLD | Folders exist, no source files. |
| `hardware/` (display, touch, audio, microphone, storage, camera) | EMPTY SCAFFOLD | Folders exist, no source files. |
| `sensors/` (dht22, ds3231) | EMPTY SCAFFOLD | Folders exist, no source files. |
| `network/` (wifi, api) | EMPTY SCAFFOLD | Folders exist, no source files. |
| `ai/` (language, routing, speech, vision) | EMPTY SCAFFOLD | Folders exist, no source files. |
| `applications/` (assistant, entertainment, exhibition, study) | EMPTY SCAFFOLD | Folders exist, no source files. |
| `config/` | EMPTY | No configuration files. |
| Build (`.pio/build/esp32dev`) | PARTIAL | Skeleton compiles; nothing functional built. |

**Conclusion:** No AURA feature is implemented yet. Firmware is scaffolding only.

---

## 5. Git Repository Status

- **Branch:** `main`, up to date with `origin/main`.
- **History (5 commits):**
  1. `f30d286` — Initial ESP32 PlatformIO project create
  2. `963c0df` — Add Requirement File
  3. `bfadfed` — Update AURA V1 Requirements: mark required hardware as available
  4. `c469b70` — docs: add 90-day development roadmap for AURA project
  5. `28c8327` — docs: create AURA_PINMAP_V1 and AURA Software Architecture documents
- **Uncommitted / untracked:** `AURA_Component_Verification.pdf`, `AURA_Component_Verification.xlsx`, `CLAUDE.md`.

---

## 6. Feature Status (claimed vs actual)

| Feature | Claimed | Actual Status |
|---|---|---|
| Basic UI | Not claimed | NOT STARTED |
| Clock/RTC display | Not claimed | NOT STARTED |
| Temp/humidity monitoring | Not claimed | NOT STARTED |
| Cloud AI chat / voice-to-text | Not claimed | NOT STARTED |
| MP3 playback | Not claimed | NOT STARTED |
| SD logging/config | Not claimed | NOT STARTED |
| Decision Engine / Commands | Not claimed | NOT STARTED |
| Study / Exhibition modes | Not claimed | NOT STARTED |

No features are claimed as working. All are untested/not implemented.

---

## 7. Summary

| Item | Count / Status |
|---|---|
| Components verified present | 14 documented components |
| Components NOT TESTED (awaiting Phase 2) | 14 |
| Components MISSING | None recorded |
| Out-of-scope EXTRA | MQ-135 (1) |
| Warnings (battery/charging mismatch) | 2 → resolve Day 5 |
| Firmware | Scaffold only (default template) |
| Git | Clean branch, 5 commits, 3 untracked files |
| Damaged hardware | None |

---

## 8. Action Items (from Day 1 audit)

1. **Verify display and touch operation** on the confirmed 3.5" ILI9488 module during Days 13–14.
2. **Fix DFPlayer Mini purchase link** in the component docx (currently points to the TFT screen).
3. **Remove MQ-135** from scope (outside frozen V1) or get explicit approval.
4. **Measure final rail voltage/current under load** during hardware integration.

---

## 9. Day 1 Completion Criteria

| Criterion | Status |
|---|---|
| Inventoried every physical component | ✅ Done |
| Separated available / missing / damaged | ✅ Done |
| Checked existing firmware | ✅ Done (scaffold only) |
| Checked current Git repository | ✅ Done |
| Tested currently claimed working features | ✅ Done (none claimed) |
| Recorded broken features | ✅ Done (none broken, none implemented) |
| Recorded untested features | ✅ Done (all not tested) |
| Recorded missing hardware | ✅ Done (none recorded) |
| Created `AURA_CURRENT_STATUS.md` | ✅ Done |

---

## Document Control

**Version:** V1.0
**Phase:** Phase 1
**Day:** 1
**Status:** Complete (audit recorded)
**Next Roadmap Day:** Day 2 — Freeze AURA V1 Requirements (complete)
