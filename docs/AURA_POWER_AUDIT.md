# AURA Power Audit

**Project:** AURA AI Desk Assistant  
**Roadmap:** 90-Day AURA Development Roadmap  
**Phase:** Phase 1 — Audit and Architecture  
**Day:** 5 — Power Audit  
**Status:** Complete — design and regulated 5 V output confirmed

---

## 1. Purpose

This document records the AURA V1 power architecture, battery configuration, and regulated supply decision before hardware integration.

## 2. Confirmed Battery System

| Item | Confirmed specification |
|---|---|
| Cells | 4 × 18650 Li-ion cells |
| Per-cell rating | 3.7 V nominal, 3000 mAh |
| Configuration | 2S2P: two series pairs connected in parallel |
| Pack voltage | 7.4 V nominal; 8.4 V fully charged |
| Pack capacity | 6000 mAh |
| Battery protection | 2S BMS |

The 2S BMS matches the confirmed 2S2P battery configuration. The battery pack must be charged only with an appropriate 2S Li-ion charger (8.4 V CC/CV); it must not use a single-cell charger.

## 3. Regulated Power Rails

| Rail | Source | Status | Intended use |
|---|---|---|---|
| Battery rail | 2S2P pack through 2S BMS | Confirmed | Input to regulation stage |
| 5 V rail | Buck converter | Confirmed output: 5 V | ESP32 VIN/USB input where appropriate, display/module supply as specified, audio modules and other 5 V-compatible loads |
| 3.3 V rail | Regulated 3.3 V supply | Required for integration | ESP32 logic and 3.3 V-only peripherals such as the INMP441; verify each module before connection |
| GND | Common ground | Required | Shared reference for every powered module |

## 4. Planned Power Path

```text
2S2P 18650 battery pack
        ↓
      2S BMS
        ↓
Power switch / fuse (recommended)
        ↓
  Buck converter (5 V output verified)
        ↓
  5 V rail ──────────→ 5 V-compatible AURA modules
        ↓
Regulated 3.3 V rail ─→ ESP32 logic and 3.3 V-only peripherals
```

## 5. Current-Budget Planning

The main peak-power loads are expected to be the display, ESP32 Wi-Fi activity, camera, and the DFPlayer/PAM8403/speaker audio path.

| Load group | Planning estimate |
|---|---:|
| ESP32 plus Wi-Fi peak | Up to 0.5 A |
| TFT display | Approximately 0.2–0.5 A; verify actual display specification |
| ESP32-CAM | Approximately 0.2–0.4 A; verify actual camera specification |
| MicroSD and sensors | Approximately 0.1–0.3 A peak |
| Audio path at high volume | Approximately 1.5–3 A peak; verify with the installed amplifier/speaker |

**Buck-converter target:** 5 V output, at least 3 A continuous; 5 A continuous is recommended to provide safe headroom for simultaneous display, Wi-Fi, camera, and audio operation.

## 6. Safety and Integration Rules

1. Confirm each module's required supply voltage before wiring it.
2. Do not connect 3.3 V-only logic modules directly to the 5 V rail.
3. Do not energize the complete system until all converter outputs have been measured with a multimeter.
4. Connect all modules to a common ground.
5. Check the buck converter for output stability and excessive heating under load before final assembly.
6. Use an appropriate 8.4 V 2S Li-ion charger with the BMS configuration.

## 7. Day 5 Completion Checklist

- [x] Battery configuration reconciled: 2S2P, not 1S.
- [x] Battery nominal/full voltage and capacity documented.
- [x] 2S BMS confirmed as appropriate for the battery pack.
- [x] 5 V buck-converter output confirmed.
- [x] 5 V and 3.3 V rail roles defined.
- [x] Power path and common-ground requirement documented.
- [x] Peak-load planning and converter sizing guidance recorded.
- [x] Charging and wiring safety requirements recorded.

## 8. Follow-Up During Hardware Integration

Measure the actual 5 V/3.3 V rail voltage under load and confirm the final current rating, thermal behavior, and voltage requirement of the installed TFT, camera, amplifier, and other modules before permanent wiring.

---

**Next Roadmap Day:** Day 6 — GitHub setup and workflow
