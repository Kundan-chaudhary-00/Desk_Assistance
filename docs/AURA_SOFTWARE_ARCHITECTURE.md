# AURA Software Architecture

**Project:** AURA AI Desk Assistant
**Project Location:** `E:\Desk_Assistance`
**Roadmap:** AURA 90-Day Roadmap
**Phase:** Phase 1 — Audit and Architecture
**Day:** 3 — Final Software Architecture
**Status:** Architecture Defined

---

## 1. Purpose

This document defines the planned software architecture for AURA V1.

The architecture will separate the core system, hardware drivers, sensors, networking, AI, applications, configuration, tests, and documentation.

The architecture will be implemented progressively according to the 90-Day Roadmap.

---

# 2. Current Project Structure
The current PlatformIO project structure is:

```text
E:\Desk_Assistance
│
├── .pio/
│   └── build/
│       └── esp32dev/
│
├── .vscode/
├── docs/
├── include/
├── lib/
├── src/
└── test/
```

This is the **current structure at the beginning of Day 3**.

The existing PlatformIO folders will be preserved.

---

# 3. Planned AURA Architecture

The final AURA architecture defined by the roadmap is:

```text
AURA/
├── main.cpp
│
├── core/
│   ├── system/
│   ├── state_machine/
│   ├── decision_engine/
│   ├── command_manager/
│   ├── action_manager/
│   ├── response_manager/
│   ├── memory/
│   └── diagnostics/
│
├── hardware/
│   ├── display/
│   ├── touch/
│   ├── audio/
│   ├── microphone/
│   ├── storage/
│   └── camera/
│
├── sensors/
│   ├── dht22/
│   ├── ds3231/
│   └── pir/
│
├── network/
│   ├── wifi/
│   └── api/
│
├── ai/
│   ├── routing/
│   ├── language/
│   ├── speech/
│   └── vision/
│
├── applications/
│   ├── assistant/
│   ├── study/
│   ├── entertainment/
│   └── exhibition/
│
├── config/
├── tests/
└── docs/
```

This is the **planned architecture**, not a claim that all these folders currently exist.

---

# 4. Existing vs Planned Structure

| Current Folder | Purpose                            |
| -------------- | ---------------------------------- |
| `.pio/`        | PlatformIO generated build files   |
| `.vscode/`     | VS Code project settings           |
| `docs/`        | Project documentation              |
| `include/`     | Header files                       |
| `lib/`         | PlatformIO libraries               |
| `src/`         | Current firmware source            |
| `test/`        | Existing PlatformIO test directory |

The following architecture folders are currently **not yet created**:

* `core/`
* `hardware/`
* `sensors/`
* `network/`
* `ai/`
* `applications/`
* `config/`

They will be introduced at the appropriate development stage.

---

# 5. Core Architecture

## `core/`

The core contains AURA's main system logic.

### `core/system/`

Responsible for:

* System initialization
* Overall system control
* System-level services

### `core/state_machine/`

Responsible for:

* AURA operating states
* State transitions
* Mode management

### `core/decision_engine/`

Responsible for:

* Deciding what AURA should do
* Selecting appropriate actions
* Connecting commands with system actions

### `core/command_manager/`

Responsible for:

* Receiving commands
* Processing commands
* Managing command execution flow

### `core/action_manager/`

Responsible for:

* Executing selected actions
* Coordinating hardware and software actions

### `core/response_manager/`

Responsible for:

* Preparing AURA responses
* Coordinating response output

### `core/memory/`

Responsible for:

* Context
* Memory-related functionality

### `core/diagnostics/`

Responsible for:

* System diagnostics
* Error reporting
* Debugging information

---

# 6. Hardware Architecture

## `hardware/`

Hardware-specific interfaces will be separated from the main system logic.

### `hardware/display/`

3.5-inch TFT display interface.

### `hardware/touch/`

Touchscreen input interface.

### `hardware/audio/`

DFPlayer Mini and speaker-related functionality.

### `hardware/microphone/`

INMP441 microphone interface.

### `hardware/storage/`

MicroSD storage interface.

### `hardware/camera/`

Camera interface.

**Camera model and exact pin configuration remain TBD until the appropriate hardware audit.**

---

# 7. Sensor Architecture

## `sensors/`

Sensor-specific code will be separated into:

```text
sensors/
├── dht22/
├── ds3231/
└── pir/
```

### DHT22

Temperature and humidity.

### DS3231

Real-time clock.

### PIR

Motion detection.

---

# 8. Network Architecture

## `network/`

Network functionality will be separated into:

```text
network/
├── wifi/
└── api/
```

### Wi-Fi

Responsible for connecting AURA to the network.

### API

Responsible for communication with external services.

---

# 9. AI Architecture

## `ai/`

AI-related functionality will be separated into:

```text
ai/
├── routing/
├── language/
├── speech/
└── vision/
```

### Routing

Determines which AI capability should handle a request.

### Language

Language and conversational AI functionality.

### Speech

Speech-related processing.

### Vision

Camera and vision-related processing.

---

# 10. Application Architecture

## `applications/`

User-facing AURA applications will be separated into:

```text
applications/
├── assistant/
├── study/
├── entertainment/
└── exhibition/
```

### Assistant

Main AURA assistant functionality.

### Study

Study Mode functionality.

### Entertainment

Entertainment-related functionality.

### Exhibition

Science-exhibition demonstration functionality.

---

# 11. Configuration

## `config/`

Configuration files and settings will be kept separate from the main application logic.

Examples may include:

* Device settings
* User preferences
* System configuration
* Network configuration

Exact configuration contents will be defined later.

---

# 12. Testing

## `tests/`

The final architecture includes a dedicated testing area.

The existing PlatformIO `test/` folder will **not be removed or renamed at this stage**.

Testing structure will be finalized when the testing architecture is implemented.

---

# 13. Documentation

## `docs/`

Project documentation will be stored here.

Current and planned documents include:

```text
docs/
├── AURA_CURRENT_STATUS.md
├── AURA_V1_REQUIREMENTS.md
└── AURA_SOFTWARE_ARCHITECTURE.md
```

Additional documentation will be added as the project progresses.

---

# 14. AURA Software Flow

The planned high-level flow is:

```text
USER
  │
  ├── Touch
  ├── Voice
  └── Camera
       │
       ▼
INPUT PROCESSING
       │
       ▼
COMMAND MANAGER
       │
       ▼
DECISION ENGINE
       │
       ▼
ACTION MANAGER
       │
       ├── Display
       ├── Audio
       ├── Sensors
       └── Other Hardware
       │
       ▼
RESPONSE MANAGER
       │
       ▼
USER
```

---

# 15. ESP32 Responsibility

The ESP32 will act as the main embedded controller for AURA.

It will handle appropriate embedded tasks such as:

* Hardware interfaces
* Sensors
* Display communication
* Touch communication
* Audio interfaces
* Local control
* System state
* Networking
* Device coordination

Heavy AI processing may use cloud or additional processing where required by the final implementation.

---

# 16. Architecture Principles

AURA should follow these principles:

1. Keep hardware drivers separate from application logic.
2. Keep sensor interfaces modular.
3. Keep networking separate from core logic.
4. Keep AI functionality modular.
5. Keep applications separate from low-level hardware.
6. Avoid putting the entire system inside `main.cpp`.
7. Make individual modules independently testable.
8. Do not guess hardware details that have not yet been finalized.
9. Follow the dependency order of the 90-Day Roadmap.

---

# 17. Day 3 Scope

Day 3 defines the **software architecture**.

Day 3 does not require implementation of every module.

The following work belongs to later stages:

* Individual hardware drivers
* Final GPIO assignment
* Sensor integration
* Network implementation
* AI implementation
* Application implementation
* Full UI implementation
* Complete system integration

---

# 18. Current Architecture Status

**Current project structure:** Existing PlatformIO structure preserved.

**Planned AURA architecture:** Defined.

**Implementation status:** Not yet fully implemented.

**Camera interface:** TBD.

**Final GPIO mapping:** To be defined during the Pin & Bus Audit.

---

## Day 3 Completion Criteria

* [x] Planned architecture documented
* [x] Core modules defined
* [x] Hardware modules defined
* [x] Sensor modules defined
* [x] Network modules defined
* [x] AI modules defined
* [x] Application modules defined
* [x] Configuration area defined
* [x] Testing area defined
* [x] Documentation area defined
* [x] Existing PlatformIO structure preserved
* [x] No hardware pins guessed
* [x] `AURA_SOFTWARE_ARCHITECTURE.md` created

**Next Roadmap Day:** Day 4 — Pin & Bus Audit
