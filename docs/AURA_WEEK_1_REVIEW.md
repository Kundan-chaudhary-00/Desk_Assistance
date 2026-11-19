# AURA Week 1 Review — Architecture Freeze

**Project:** AURA AI Desk Assistant  
**Roadmap:** 90-Day AURA Development Roadmap  
**Phase:** Phase 1 — Audit and Architecture  
**Day:** 7 — Week 1 Review  
**Status:** Complete — approved to begin Phase 2 hardware foundation

---

## 1. Week 1 Completion Review

| Day | Deliverable | Result |
|---:|---|---|
| 1 | Project audit | Complete — current state, component inventory, firmware baseline, and Git state recorded. |
| 2 | V1 requirements | Complete — stationary AURA scope frozen. |
| 3 | Software architecture | Complete — modular project structure documented. |
| 4 | Pin and bus audit | Complete — I²C, SPI, I²S, UART, GPIO, and unresolved interfaces recorded. |
| 5 | Power audit | Complete — 2S2P battery, 2S BMS, 5 V buck output, and rail plan documented. |
| 6 | GitHub workflow | Complete — `main`, `develop`, and documented work-branch conventions established. |

## 2. Confirmed Hardware Decisions

- The previous presence-sensor requirement is removed from AURA V1 scope and from the project structure.
- The ESP32-CAM is the V1 vision subsystem.
- The display is a 3.5-inch ILI9488 TFT with integrated touch, 480 × 320 resolution, 4-wire SPI interface, and an on-board MicroSD slot.
- The display and touch interfaces are confirmed; final ESP32 GPIO assignments remain a Day 12–14 integration task.
- The power system uses four 3.7 V / 3000 mAh cells in a 2S2P configuration, with a 2S BMS.
- A compatible 2S charger is available.
- The buck converter's 5 V output has been checked with a multimeter.

## 3. Architecture and Pin-Map Checkpoint

No GPIO conflict has been reported. The following items remain intentionally unresolved until the corresponding hardware work begins:

1. Shared SPI chip-select allocation for the TFT, touch interface, and on-board MicroSD.
2. ESP32-CAM communication method with the main ESP32.
3. Final rail current/thermal measurements under real system load.

These are planned engineering tasks, not scope blockers.

## 4. Repository Checkpoint

- `main` is the stable baseline branch.
- `develop` is the integration branch.
- `feature/`, `hardware/`, `docs/`, and `fix/` are the approved work-branch prefixes.
- Repository guidance is provided by `README.md`, `CHANGELOG.md`, and `CONTRIBUTING.md`.

## 5. Phase 2 Entry Criteria

- [x] Hardware inventory recorded.
- [x] V1 scope frozen.
- [x] Software architecture documented.
- [x] Pin and bus audit documented.
- [x] Power plan documented.
- [x] Git/GitHub workflow established.
- [x] Display model and interface confirmed.
- [x] ESP32-CAM retained as the vision subsystem.
- [x] Presence-sensor requirement removed from scope and repository structure.

## 6. Next Step

Proceed to **Day 8 — ESP32 Base System**: implement serial logging, configuration loading, boot diagnostics, and a system heartbeat. Do not connect unverified peripherals until their voltage and GPIO assignments are confirmed.
