# AURA_PINMAP_V1.md

## AURA V1 — Pin, Bus and Interface Map

**Project:** AURA — AI Desk Assistant  
**Document:** AURA_PINMAP_V1.md  
**Phase:** Phase 1 — Audit and Architecture  
**Day:** Day 4 — Pin and Bus Audit  
**Status:** COMPLETE — V1 pin/bus allocation documented with deliberate TBD entries  
**Controller:** ESP32 WROOM DevKit  
**Vision Controller:** ESP32-CAM (separate board)  

---

## 1. Purpose

This document freezes the current AURA V1 hardware interface plan before firmware integration.

It documents:

- GPIO allocation
- I²C bus
- SPI bus
- I²S bus
- UART
- chip-select lines
- interrupt/input pins
- power/interface notes
- reserved pins
- intentionally unresolved hardware

The roadmap requires these areas to be documented during Day 4 and specifically states that final camera pins must not be guessed.

---

# 2. Controller Architecture

AURA uses two ESP32-class boards:

```text
                    AURA SYSTEM

        ┌──────────────────────────────┐
        │       MAIN ESP32 WROOM       │
        │                              │
        │  UI / Sensors / Audio /      │
        │  Storage / Wi-Fi / Control   │
        └──────────────┬───────────────┘
                       │
                       │ Vision communication
                       │ TBD
                       ▼
        ┌──────────────────────────────┐
        │          ESP32-CAM           │
        │                              │
        │     Camera / Vision          │
        └──────────────────────────────┘
```

The main ESP32 remains the primary AURA controller.

The ESP32-CAM is treated as a separate vision subsystem.

---

# 3. Main ESP32 Pin Allocation

## 3.1 Confirmed / planned GPIO assignments

| GPIO | Function | Hardware | Interface | Direction | Status |
|---:|---|---|---|---|---|
| GPIO 21 | SDA | DS3231 | I²C | I/O | ASSIGNED |
| GPIO 22 | SCL | DS3231 | I²C | I/O | ASSIGNED |
| GPIO 18 | SCK | MicroSD / future TFT SPI | SPI | Output | ASSIGNED |
| GPIO 19 | MISO | MicroSD / future TFT SPI | SPI | Input | ASSIGNED |
| GPIO 23 | MOSI | MicroSD / future TFT SPI | SPI | Output | ASSIGNED |
| GPIO 5 | CS | MicroSD module | SPI | Output | ASSIGNED |
| GPIO 16 | RX2 | MP3-TF-16P V3.0 | UART2 | Input | ASSIGNED |
| GPIO 17 | TX2 | MP3-TF-16P V3.0 | UART2 | Output | ASSIGNED |
| GPIO 26 | BCLK | INMP441 | I²S | Output | ASSIGNED |
| GPIO 25 | WS/LRCLK | INMP441 | I²S | Output | ASSIGNED |
| GPIO 33 | SD/DOUT | INMP441 | I²S | Input | ASSIGNED |
| GPIO 27 | DATA | DHT22 | GPIO | Input | ASSIGNED |
| GPIO 13 | I/O | Buzzer | GPIO | Output | ASSIGNED |
| GPIO 34 | Motion input | PIR | GPIO | Input-only | RESERVED / CURRENTLY UNUSED |

---

# 4. I²C Bus

## Bus

```text
ESP32
 ├── GPIO 21 → SDA
 └── GPIO 22 → SCL
```

### Device

| Device | SDA | SCL | Status |
|---|---:|---:|---|
| DS3231 RTC | GPIO 21 | GPIO 22 | Assigned |

### Notes

- DS3231 uses I²C.
- GPIO 21 and GPIO 22 are the standard ESP32 I²C pins selected for AURA.
- Additional I²C devices may be added later if address and electrical compatibility are verified.
- DS3231 32K and SQW outputs are not assigned for the current V1 implementation.

---

# 5. SPI Bus

The main SPI bus is reserved for storage and the future TFT.

## Shared SPI lines

| SPI signal | ESP32 GPIO |
|---|---:|
| SCK | GPIO 18 |
| MISO | GPIO 19 |
| MOSI | GPIO 23 |

### Current device

| Device | CS | Status |
|---|---:|---|
| MicroSD module | GPIO 5 | Assigned |

### TFT

The TFT has intentionally been left unresolved at the user's request.

```text
TFT SCK   → TBD
TFT MOSI  → TBD
TFT MISO  → TBD
TFT CS    → TBD
TFT DC/RS → TBD
TFT RST   → TBD
```

The TFT pins will be finalized after the newly ordered 3.5-inch TFT is physically inspected.

**Do not wire the TFT according to this document until its exact board/interface is verified.**

### Touch

Touch controller pins are also intentionally left TBD until the ordered TFT is inspected.

```text
Touch SCK  → TBD
Touch MISO → TBD
Touch MOSI → TBD
Touch CS   → TBD
Touch IRQ  → TBD
```

---

# 6. I²S Bus — INMP441

The INMP441 is a digital I²S microphone.

## Assignment

| INMP441 signal | ESP32 GPIO |
|---|---:|
| SCK / BCLK | GPIO 26 |
| WS / LRCLK | GPIO 25 |
| SD / DOUT | GPIO 33 |

```text
INMP441
 ├── SCK/BCLK  → GPIO 26
 ├── WS        → GPIO 25
 └── SD/DOUT   → GPIO 33
```

### Notes

- The microphone output is digital I²S audio.
- No external analog ADC is required.
- L/R select handling will be verified during the Day 18 microphone test.
- INMP441 power and logic voltage must be wired according to the module's verified specification.

---

# 7. UART — MP3-TF-16P V3.0

The installed audio decoder is labelled:

**MP3-TF-16P V3.0**

It is being used as the AURA DFPlayer-compatible audio module.

## UART2

| Signal | ESP32 GPIO | MP3-TF-16P |
|---|---:|---|
| ESP32 TX2 | GPIO 17 | RX |
| ESP32 RX2 | GPIO 16 | TX |

```text
ESP32 GPIO 17 (TX2) ─────► MP3-TF-16P RX
ESP32 GPIO 16 (RX2) ◄───── MP3-TF-16P TX
```

### Audio output architecture

The current audio hardware is:

```text
ESP32
  │
  │ UART
  ▼
MP3-TF-16P V3.0
  │
  │ DAC_L / DAC_R
  ▼
PAM8403 amplifier
  │
  ▼
6 Ω / 15 W speaker
```

The speaker itself is not connected directly to the ESP32 GPIO.

---

# 8. DHT22

## Assignment

```text
DHT22 DATA → GPIO 27
```

| Signal | GPIO |
|---|---:|
| DATA | GPIO 27 |

Power and ground are handled separately through the appropriate supply rails.

---

# 9. Buzzer

## Assignment

```text
Buzzer I/O → GPIO 13
```

| Signal | GPIO |
|---|---:|
| I/O | GPIO 13 |

The buzzer is intended for:

- startup beep
- touch feedback
- warning/error indication
- alarm notification

The buzzer module's supply voltage must be verified before final enclosure wiring.

---

# 10. PIR Motion Sensor

The PIR sensor is currently removed from the physical build.

The roadmap still defines PIR as a V1 hardware requirement, therefore it is not permanently deleted from the architecture.

A GPIO is reserved for future use:

```text
PIR → GPIO 34
```

### Current status

**RESERVED / UNUSED**

GPIO 34 is input-only on the ESP32 and is therefore suitable as a future digital sensor input, but the PIR is not currently connected.

---

# 11. Camera — ESP32-CAM

The project uses the pictured ESP32-CAM board as the vision subsystem.

The ESP32-CAM is a separate ESP32 board and is not treated as a simple camera sensor connected directly to the main ESP32.

```text
Main ESP32
    │
    │ Vision communication — TBD
    ▼
ESP32-CAM
    │
    ▼
Camera sensor
```

## ESP32-CAM board pins

The provided board reference identifies the following exposed pins:

### Power

- 5V
- 3.3V
- GND

### Exposed GPIO

- GPIO 0
- GPIO 1 / U0TXD
- GPIO 2
- GPIO 3 / U0RXD
- GPIO 4
- GPIO 12
- GPIO 13
- GPIO 14
- GPIO 15
- GPIO 16

### Important

The final camera-sensor GPIO mapping and communication method are **TBD**.

This is intentional.

The roadmap explicitly requires:

> Do NOT guess final camera pins.

The exact camera communication architecture will be finalized during the camera hardware verification stage.

---

# 12. Power Interface Map

Day 4 records the required power/interface rails, but **Day 5 is responsible for the detailed power audit**.

## Expected rails

| Rail | Intended use | Status |
|---|---|---|
| 3.3 V | ESP32 logic / sensors / microphone and compatible peripherals | Requires verification |
| 5 V | Audio / selected modules / display as applicable | Requires verification |
| GND | Common reference | Required |

## Battery currently available

```text
1 × 18650
3.7 V nominal
3000 mAh
```

The current battery is a **1S single-cell arrangement**.

The previous project architecture described a 2S battery system, but the current physical battery is 1S. Therefore the final power conversion architecture is intentionally **not frozen in this Day 4 document**.

Power architecture will be finalized during Day 5.

---

# 13. BMS Status

BMS is currently deferred.

```text
BMS → DEFERRED
```

This does **not** mean the final battery system will operate without appropriate protection.

Battery protection, charging method, converter selection and rail stability are Day 5 tasks.

---

# 14. Buck / Power Converter

The available adjustable DC-DC converter is recorded as available hardware.

Its final output voltage and suitability for the AURA power architecture are **not yet frozen**.

Do not connect sensitive AURA electronics to an unverified converter output.

Day 5 will verify:

- input range
- output voltage
- output current capability
- efficiency
- thermal behavior
- 5 V rail
- 3.3 V rail
- battery charging/protection architecture

---

# 15. GPIO Reservation / Safety Notes

The ESP32 WROOM DevKit pin reference identifies special-purpose and input-only GPIOs.

## Avoid using

### GPIO 6–11

These are associated with the ESP32's internal flash interface and should not be assigned to AURA peripherals.

### GPIO 34–39

These are input-only pins.

They are suitable for inputs but cannot directly drive:

- buzzer
- LED
- display control
- other output devices

GPIO 34 is therefore reserved only as a possible PIR input.

## Boot/strapping pins

The following pins have boot/strapping considerations and should not be assigned casually:

- GPIO 0
- GPIO 2
- GPIO 5
- GPIO 12
- GPIO 15

GPIO 5 is currently assigned as MicroSD CS and must be verified during boot testing.

If boot problems occur, the SD chip-select behavior must be investigated before changing the architecture.

---

# 16. Main ESP32 Pin Summary

| GPIO | Assignment | Status |
|---:|---|---|
| 0 | Reserved / boot-related | RESERVED |
| 1 | USB/UART0 TX | RESERVED |
| 2 | Reserved / boot-related | RESERVED |
| 3 | USB/UART0 RX | RESERVED |
| 4 | Unassigned | AVAILABLE / RESERVED |
| 5 | MicroSD CS | ASSIGNED |
| 6–11 | Internal flash | DO NOT USE |
| 12 | Reserved / strapping | RESERVED |
| 13 | Buzzer | ASSIGNED |
| 14 | Unassigned | AVAILABLE |
| 15 | Reserved / strapping | RESERVED |
| 16 | MP3-TF-16P RX | ASSIGNED |
| 17 | MP3-TF-16P TX | ASSIGNED |
| 18 | SPI SCK | ASSIGNED |
| 19 | SPI MISO | ASSIGNED |
| 21 | I²C SDA | ASSIGNED |
| 22 | I²C SCL | ASSIGNED |
| 23 | SPI MOSI | ASSIGNED |
| 25 | INMP441 WS/LRCLK | ASSIGNED |
| 26 | INMP441 BCLK | ASSIGNED |
| 27 | DHT22 DATA | ASSIGNED |
| 32 | Unassigned | AVAILABLE |
| 33 | INMP441 SD/DOUT | ASSIGNED |
| 34 | PIR future input | RESERVED |
| 35 | Unassigned input-only | AVAILABLE INPUT |
| 36 | Unassigned input-only | AVAILABLE INPUT |
| 39 | Unassigned input-only | AVAILABLE INPUT |

---

# 17. Unassigned GPIO Budget

Currently available pins are intentionally retained for future hardware such as:

- TFT control
- TFT touch
- camera communication
- status LED
- additional sensors
- future peripherals

The remaining GPIOs must not be assigned until the TFT and camera architecture are finalized.

This prevents accidental pin conflicts.

---

# 18. Bus Summary

| Bus | Pins | Device(s) | Status |
|---|---|---|---|
| I²C | SDA 21 / SCL 22 | DS3231 | FROZEN |
| SPI | SCK 18 / MISO 19 / MOSI 23 | MicroSD + future TFT | PARTIALLY FROZEN |
| I²S | BCLK 26 / WS 25 / SD 33 | INMP441 | FROZEN |
| UART2 | TX 17 / RX 16 | MP3-TF-16P V3.0 | FROZEN |
| GPIO | 27 | DHT22 | FROZEN |
| GPIO | 13 | Buzzer | FROZEN |
| GPIO | 34 | PIR future input | RESERVED |
| Camera | TBD | ESP32-CAM | TBD |
| TFT | TBD | 3.5" ILI9486 | TBD |
| Touch | TBD | XPT2046 / actual ordered controller | TBD |

---

# 19. Chip-Select Lines

| Device | CS GPIO | Status |
|---|---:|---|
| MicroSD | GPIO 5 | Assigned |
| TFT | TBD | Waiting for ordered TFT verification |
| Touch | TBD | Waiting for ordered TFT verification |

Each SPI device must have its own chip-select line.

Only the currently verified MicroSD CS is frozen.

---

# 20. Interrupt / Event Inputs

| Source | GPIO | Type | Status |
|---|---:|---|---|
| PIR | GPIO 34 | Digital input | Reserved |
| Touch IRQ | TBD | Interrupt/input | TFT verification required |
| DS3231 SQW | Unassigned | Optional interrupt | Not required for V1 |
| Camera events | TBD | Vision subsystem | TBD |

---

# 21. Hardware Conflict Check

## Current known conflicts

**None identified in the currently frozen assignments.**

## Known unresolved areas

1. TFT SPI/control pins
2. Touch controller pins
3. ESP32-CAM communication method
4. ESP32-CAM final camera interface allocation
5. Final battery/power architecture

These are deliberately left unresolved rather than guessed.

---

# 22. Important Integration Rules

### Rule 1 — Do not use GPIO 6–11

These pins are associated with internal flash.

### Rule 2 — Do not treat GPIO 34–39 as outputs

They are input-only.

### Rule 3 — SPI devices share the bus

SCK/MISO/MOSI may be shared, but each device needs an independent CS.

### Rule 4 — TFT remains TBD

Do not assume the previous photographed TFT has the same interface as the newly ordered TFT.

### Rule 5 — Camera remains TBD

The ESP32-CAM board is identified, but its final camera communication architecture is not frozen here.

### Rule 6 — Power is not frozen by this document

Do not use this pin map as a substitute for the Day 5 power audit.

---

# 23. Day 4 Completion Status

## Required Day 4 areas

- [x] GPIO audit
- [x] SPI audit
- [x] I²C audit
- [x] I²S audit
- [x] UART audit
- [x] Power rail interfaces documented
- [x] MicroSD chip-select documented
- [x] Interrupt/input considerations documented
- [x] Camera explicitly kept TBD
- [x] Pin conflicts reviewed
- [x] Unassigned/reserved GPIO documented
- [x] AURA_PINMAP_V1.md created

## Deliberately deferred

- [ ] TFT final pin assignment
- [ ] Touch final pin assignment
- [ ] Camera final communication/pin assignment
- [ ] Final battery/BMS/power architecture

These are not failures of Day 4. They are intentionally deferred because the required hardware information is not yet frozen and the roadmap explicitly requires camera pins not to be guessed.

---

# 24. Next Step — Day 5

Day 5 is the **Power Audit**.

It must verify:

- ESP32 current
- display current
- DFPlayer current
- speaker/amplifier requirements
- sensor consumption
- camera consumption
- Wi-Fi consumption
- battery
- BMS
- charger
- buck/boost conversion
- 5 V rail
- 3.3 V rail

The current 1S 18650 battery architecture must be reconciled with the earlier 2S project concept before battery-powered AURA integration.

---

## Document Control

**Version:** V1.0  
**Phase:** Phase 1  
**Day:** 4  
**Status:** Complete with explicit TBD items  
**Major principle:** Never guess an unresolved hardware interface.
