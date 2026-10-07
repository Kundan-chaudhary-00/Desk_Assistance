# AURA — 90-DAY DEVELOPMENT ROADMAP

## Stationary AI Desk Assistant — V1.0

---

# 1. PROJECT DEFINITION

AURA is a stationary AI Desk Assistant.

AURA is NOT a mobile robot in the current prototype.

The current version does NOT include:

* Wheels
* Motors
* Motor drivers
* Navigation
* Obstacle avoidance
* SLAM
* Autonomous movement
* Mobile-robot chassis

The project instead focuses on:

* Artificial intelligence
* Voice interaction
* Touch interaction
* Camera/vision
* Environmental sensing
* Study assistance
* Personal-assistant functions
* Audio interaction
* AI conversation
* Memory
* Notifications
* Exhibition demonstrations
* Modular architecture
* Reliability
* Professional physical design

The main objective of the next 90 days is to transform the existing AURA system into a reliable, integrated and impressive stationary AI Desk Assistant prototype.

---

# 2. CURRENT PROJECT STATE

The current project documentation reports the following status.

## 2.1 Completed

According to the current AURA onboarding documentation:

* ESP32 hardware assembled
* Touchscreen assembled
* INMP441 microphone assembled
* Speaker/DFPlayer assembled
* DHT22 assembled
* DS3231 assembled
* PIR assembled
* Buzzer assembled
* Wi-Fi working
* Basic UI working
* RTC working
* Cloud voice-to-text connected
* Basic cloud AI chat connected
* Temperature/humidity monitoring working
* Clock display working
* RTC-based alarms working
* MP3 audio playback working
* Basic conversational responses working
* System logging/configuration storage on SD
* Basic network/sensor error handling

Source:
AURA Project Onboarding Document.

---

# 2.2 Currently In Progress

* Full Study Mode
* Question database
* Voice Q&A
* Interactive quiz
* Quiz scoring
* Exhibition Demo Mode
* "My Brain" explanation content
* Improved offline handling
* Context memory
* Camera hardware integration tests

Source:
AURA Project Onboarding Document.

---

# 2.3 Planned

* Vision capabilities
* Object/QR detection
* Image capture
* Additional environment sensors
* Wake-word activation
* Improved voice commands
* Natural-language understanding
* Smart-home control
* Developer/diagnostics mode
* Refined UI

Source:
AURA Project Onboarding Document.

---

# 2.4 Future

* Local AI models
* Advanced computer vision
* Face recognition
* Object classification
* Security mode
* Fitness/health mode
* Commercial productization
* Expanded educational content
* Multi-language support

Source:
AURA Project Onboarding Document.

---

# 3. 90-DAY DEVELOPMENT STRATEGY

The project will follow this dependency chain:

VERIFY
↓
HARDWARE FOUNDATION
↓
DRIVERS
↓
MODULAR FIRMWARE
↓
UI
↓
AUDIO + VOICE
↓
WIFI + AI
↓
DECISION ENGINE
↓
STUDY + ASSISTANT
↓
CAMERA
↓
COMPUTER VISION
↓
FULL INTEGRATION
↓
CASING
↓
TESTING
↓
AURA V1.0

---

# 4. PHASE OVERVIEW

| Phase    |  Days | Objective                     |
| -------- | ----: | ----------------------------- |
| Phase 1  |   1–7 | Audit and architecture        |
| Phase 2  |  8–20 | Hardware foundation           |
| Phase 3  | 21–32 | Firmware core                 |
| Phase 4  | 33–42 | UI and interaction            |
| Phase 5  | 43–52 | Audio and voice               |
| Phase 6  | 53–63 | Wi-Fi, AI and Decision Engine |
| Phase 7  | 64–70 | Study and assistant features  |
| Phase 8  | 71–77 | Camera and computer vision    |
| Phase 9  | 78–84 | Full integration and casing   |
| Phase 10 | 85–90 | Testing and final prototype   |

---

# 5. PHASE 1 — AUDIT & ARCHITECTURE

## DAYS 1–7

---

## DAY 1 — PROJECT AUDIT

### Goal

Determine exactly what is currently working.

### Tasks

* Inventory every physical component.
* Separate available, missing and damaged components.
* Check existing firmware.
* Check current Git repository.
* Test currently claimed working features.
* Record broken features.
* Record untested features.
* Record missing hardware.

### Output

Create:

AURA_CURRENT_STATUS.md

### Status categories

* WORKING
* PARTIAL
* NOT TESTED
* FAILED
* MISSING

### Testing

Every hardware component must receive a status.

### End-of-day requirement

No major hardware component should remain completely unknown.

---

# DAY 2 — FREEZE AURA V1 REQUIREMENTS

Define the features that MUST be part of the 90-day prototype.

## Required

* ESP32
* 3.5" touchscreen
* Touch input
* DHT22
* DS3231
* MicroSD
* DFPlayer Mini
* Speaker
* INMP441 microphone
* Wi-Fi
* Cloud AI
* Command processing
* Decision Engine
* Error handling
* Study Mode
* PIR
* Camera
* Exhibition Mode
* Professional UI

## Explicitly excluded

* Wheels
* Motors
* Navigation
* Obstacle avoidance
* Autonomous movement

---

# DAY 3 — FINAL SOFTWARE ARCHITECTURE

Create the following structure:

```text
AURA/
├── main.cpp
├── core/
│   ├── system/
│   ├── state_machine/
│   ├── decision_engine/
│   ├── command_manager/
│   ├── action_manager/
│   ├── response_manager/
│   ├── memory/
│   └── diagnostics/
├── hardware/
│   ├── display/
│   ├── touch/
│   ├── audio/
│   ├── microphone/
│   ├── storage/
│   └── camera/
├── sensors/
│   ├── dht22/
│   ├── ds3231/
│   └── pir/
├── network/
│   ├── wifi/
│   └── api/
├── ai/
│   ├── routing/
│   ├── language/
│   ├── speech/
│   └── vision/
├── applications/
│   ├── assistant/
│   ├── study/
│   ├── entertainment/
│   └── exhibition/
├── config/
├── tests/
└── docs/
```

---

# DAY 4 — PIN AND BUS AUDIT

Document:

* GPIO
* SPI
* I2C
* I2S
* UART
* Power rails
* Chip-select lines
* Interrupt pins

Known interfaces:

* DS3231 → I2C
* TFT → SPI
* MicroSD → SPI
* INMP441 → I2S
* DFPlayer → UART
* PIR → GPIO
* Buzzer → GPIO
* Camera → TBD

Do NOT guess final camera pins.

Create:

AURA_PINMAP_V1.md

---

# DAY 5 — POWER AUDIT

Calculate:

* ESP32 current
* Display current
* DFPlayer current
* Speaker/amplifier requirements
* Sensor consumption
* Camera consumption
* Wi-Fi consumption

Verify:

* Battery
* BMS
* Charger
* Buck converter
* 5V rail
* 3.3V rail

The current architecture uses a 2S Li-ion battery concept with proper 2S BMS/charging and regulated rails.

---

# DAY 6 — GITHUB SETUP

Create:

main
develop
feature/*
hardware/*
docs/*

Commit style:

feat: add camera driver
fix: repair touch calibration
docs: update pin map
test: add DHT22 test
refactor: improve command manager

Create:

* README.md
* CHANGELOG.md
* CONTRIBUTING.md
* /docs
* /hardware
* /firmware
* /tests

---

# DAY 7 — WEEK 1 REVIEW

## Must be completed

* Hardware inventory
* Architecture
* Pin map
* Power plan
* Git repository
* Feature scope

## Checkpoint

AURA architecture must be frozen before major integration begins.

## Backup plan

If major hardware conflicts are discovered:

* Stop integration.
* Fix wiring/pin allocation.
* Re-test power.
* Update documentation.

---

# 6. PHASE 2 — HARDWARE FOUNDATION

## DAYS 8–20

---

# DAY 8 — ESP32 BASE SYSTEM

Implement:

* ESP32 initialization
* Serial logging
* Configuration system
* Boot diagnostics
* System heartbeat

Expected boot:

AURA BOOT
ESP32: OK
Memory: OK
Config: OK

---

# DAY 9 — GPIO + BUZZER

Implement:

* GPIO testing
* Buzzer control
* Status LED if available

Test:

* startup beep
* button/touch feedback
* error beep

---

# DAY 10 — DHT22

Implement:

* temperature reading
* humidity reading
* sensor validation
* sensor failure detection

Testing:

* 30-minute stability test
* disconnected sensor test

---

# DAY 11 — DS3231

Implement:

* time
* date
* RTC reading
* RTC setting
* alarm foundation

Test:

* power cycle
* time persistence
* alarm trigger

---

# DAY 12 — SPI BUS

Bring up:

* TFT
* MicroSD

Verify:

* chip-select lines
* bus stability
* simultaneous operation

---

# DAY 13 — TFT DISPLAY

Implement:

* initialization
* text
* rectangles
* icons
* screen clearing
* basic rendering

---

# DAY 14 — TOUCHSCREEN

Implement:

* touch coordinate reading
* calibration
* debounce
* touch buttons

Create a touch diagnostic screen.

---

# DAY 15 — MICROSD

Implement:

* mount
* read
* write
* file listing
* configuration files
* logs

Test:

* card inserted
* card removed
* invalid file
* write failure

---

# DAY 16 — DFPLAYER MINI

Implement:

* initialization
* play
* stop
* next
* previous
* volume

---

# DAY 17 — SPEAKER

Test:

* speech
* music
* sound effects
* volume control

---

# DAY 18 — INMP441

Implement:

* I2S initialization
* microphone capture
* audio buffer
* audio diagnostics

The INMP441 provides digital I2S audio directly to the ESP32.

---

# DAY 19 — PIR

Implement:

* motion detection
* debounce
* event generation
* notification

Example:

"Motion detected."

---

# DAY 20 — HARDWARE INTEGRATION TEST

Test:

ESP32       ✓
TFT         ✓
Touch       ✓
DHT22       ✓
DS3231      ✓
MicroSD     ✓
DFPlayer    ✓
Speaker     ✓
INMP441     ✓
PIR         ✓
Power       ✓

Camera is handled separately.

---

# 7. PHASE 3 — FIRMWARE CORE

## DAYS 21–32

---

# DAY 21 — CODE REFACTOR

Separate:

* hardware
* sensors
* UI
* audio
* network
* AI
* applications

---

# DAY 22 — HARDWARE ABSTRACTION

Create interfaces:

Display
Audio
Sensor
RTC
Storage
Microphone
Camera

---

# DAY 23 — CONFIGURATION SYSTEM

Store:

* Wi-Fi settings
* volume
* brightness
* timezone
* user preferences
* API configuration

Do not hard-code everything into main.cpp.

---

# DAY 24 — LOGGING

Implement:

INFO
WARNING
ERROR
DEBUG

Example:

[INFO] DHT22 initialized
[INFO] WiFi connected
[WARN] AI timeout
[ERROR] SD unavailable

---

# DAY 25 — SYSTEM STATE MACHINE

Implement:

BOOT
↓
IDLE
↓
LISTENING
↓
UNDERSTANDING
↓
DECIDING
↓
EXECUTING
↓
RESPONDING
↓
IDLE

---

# DAY 26 — LOCAL COMMAND ROUTER

Implement commands for:

* time
* date
* temperature
* humidity
* volume
* music
* system status

---

# DAY 27 — ACTION MANAGER

Architecture:

Command
↓
Action Manager
↓
Hardware/Application

Commands should not directly control hardware.

---

# DAY 28 — RESPONSE MANAGER

Decide whether a response goes to:

* TFT
* Speaker
* Buzzer
* Multiple outputs

---

# DAY 29 — ERROR MANAGER

Handle:

* sensor failure
* SD failure
* audio failure
* Wi-Fi failure
* invalid command
* AI timeout

---

# DAY 30 — WATCHDOG AND RECOVERY

Implement:

* watchdog
* safe restart
* recovery state
* startup diagnostics

---

# DAY 31 — DEVELOPER DIAGNOSTICS

Create:

```text
SYSTEM TEST
├── Display
├── Touch
├── DHT22
├── RTC
├── SD
├── Audio
├── Microphone
├── PIR
├── Wi-Fi
└── Camera
```

---

# DAY 32 — FIRMWARE MILESTONE

## Milestone

AURA must:

* boot reliably
* detect hardware
* display system status
* execute local commands
* handle basic failures
* recover from common errors

---

# 8. PHASE 4 — UI & INTERACTION

## DAYS 33–42

---

# DAY 33 — UI DESIGN SYSTEM

Define:

* fonts
* colors
* buttons
* icons
* spacing
* navigation
* status indicators

---

# DAY 34 — BOOT SCREEN

Create:

AURA
AI DESK ASSISTANT

Initializing...

---

# DAY 35 — HOME SCREEN

Show:

* time
* temperature
* Wi-Fi status
* system status
* quick actions

---

# DAY 36 — ENVIRONMENT DASHBOARD

Display:

Temperature
Humidity
Motion
Time

---

# DAY 37 — AI SCREEN

Create:

* input
* processing state
* response
* error state

---

# DAY 38 — AUDIO SCREEN

Create:

* play
* pause
* next
* previous
* volume

---

# DAY 39 — SETTINGS

Add:

* brightness
* volume
* Wi-Fi
* time
* system information

---

# DAY 40 — NOTIFICATIONS

Create notifications for:

* alarms
* reminders
* sensor alerts
* errors
* AI errors

---

# DAY 41 — UI TESTING

Test:

* every button
* every screen
* navigation
* back button
* invalid actions
* accidental touches

---

# DAY 42 — UI MILESTONE

AURA should now look and behave like a real desktop electronic product even without advanced AI.

---

# 9. PHASE 5 — AUDIO + VOICE

## DAYS 43–52

---

# DAY 43 — MICROPHONE PIPELINE

Implement:

INMP441
↓
I2S
↓
Audio Buffer

---

# DAY 44 — SPEECH-TO-TEXT STRATEGY

Determine whether STT uses:

* cloud service
* external computer
* additional processing hardware
* local lightweight processing

Do not assume that the ESP32 can run a modern speech-recognition model by itself.

---

# DAY 45 — BASIC VOICE COMMANDS

Implement:

"What time is it?"

"Show temperature."

"Play music."

"What's the humidity?"

---

# DAY 46 — COMMAND CLASSIFICATION

Classify requests into:

LOCAL
CLOUD AI
SYSTEM
STUDY
VISION
ASSISTANT

---

# DAY 47 — VOICE → LOCAL COMMAND

Implement:

Voice
↓
STT
↓
Command
↓
Router
↓
Action

---

# DAY 48 — VOICE RESPONSE

Implement:

Command
↓
Response
↓
TFT + Speaker

---

# DAY 49 — VOICE ERROR HANDLING

Handle:

* no speech
* unknown speech
* API failure
* timeout
* poor recognition

---

# DAY 50 — WAKE WORD PROTOTYPE

Attempt:

"AURA"

↓
Listening

If wake-word detection is unreliable, retain push-to-talk as the fallback.

---

# DAY 51 — VOICE STRESS TEST

Test:

* quiet room
* noisy room
* different distances
* different speakers
* repeated commands

---

# DAY 52 — VOICE MILESTONE

AURA must successfully:

HEAR
↓
UNDERSTAND
↓
EXECUTE
↓
RESPOND

for a controlled command set.

---

# 10. PHASE 6 — WIFI + AI + DECISION ENGINE

## DAYS 53–63

---

# DAY 53 — WIFI MANAGER

Implement:

* connect
* reconnect
* status
* timeout
* connection failure

---

# DAY 54 — INTERNET DIAGNOSTICS

Display:

Wi-Fi: Connected
Internet: Available
AI: Available

---

# DAY 55 — API LAYER

Implement:

* HTTP/HTTPS
* GET
* POST
* JSON
* timeouts
* retries

---

# DAY 56 — AI REQUEST MANAGER

Architecture:

User Input
↓
Prompt Builder
↓
API Request
↓
Response Parser

---

# DAY 57 — AI DISPLAY

Display:

User:
What is artificial intelligence?

AURA:
Artificial intelligence is...

---

# DAY 58 — AI AUDIO

Connect AI responses to:

* display
* speech output
* audio feedback

---

# DAY 59 — AI FAILURE HANDLING

If internet fails:

Internet unavailable.
Switching to offline mode.

Offline mode continues supporting predefined commands.

---

# DAY 60 — DECISION ENGINE

Architecture:

INPUT
↓
CLASSIFY
↓
INTENT
↓
DECISION
↓
ACTION
↓
RESPONSE

---

# DAY 61 — SHORT-TERM CONTEXT

Implement context such as:

User:
"What is the temperature?"

AURA:
"24°C."

User:
"Is that normal?"

AURA understands "that" refers to temperature.

---

# DAY 62 — MEMORY FOUNDATION

Store:

* settings
* preferences
* study subject
* recent events
* limited conversation context

Use SD/non-volatile storage where appropriate.

---

# DAY 63 — INTELLIGENCE MILESTONE

AURA should now function as one assistant instead of a collection of unrelated features.

---

# 11. PHASE 7 — STUDY + ASSISTANT FEATURES

## DAYS 64–70

---

# DAY 64 — STUDY ARCHITECTURE

Study Mode:

Study
├── Subjects
├── Lessons
├── Quiz
├── Score
├── Timer
└── Progress

---

# DAY 65 — SUBJECTS

Initial subjects:

* Science
* Mathematics
* Computer/IT
* General Knowledge

---

# DAY 66 — LEARNING MODE

Implement:

* explanations
* examples
* follow-up questions
* simple educational conversations

---

# DAY 67 — QUIZ ENGINE

Implement:

* question database
* random questions
* multiple-choice answers
* answer validation
* score
* difficulty

---

# DAY 68 — STUDY TIMER

Implement:

* timer
* Pomodoro
* completion alert

---

# DAY 69 — VOICE + STUDY

Examples:

"Start Science quiz."

"Explain photosynthesis."

"Ask me a mathematics question."

---

# DAY 70 — STUDY MILESTONE

AURA must demonstrate:

Subject
↓
Learn
↓
Ask
↓
Quiz
↓
Score
↓
Progress

---

# 12. PHASE 8 — CAMERA + COMPUTER VISION

## DAYS 71–77

---

# DAY 71 — CAMERA HARDWARE VERIFICATION

Confirm:

* camera model
* voltage
* interface
* resolution
* frame rate
* memory requirements
* ESP32 compatibility

The exact camera model remains a design decision; the current documentation gives OV2640/OV7670-class options and notes that processing headroom must be verified.

---

# DAY 72 — CAMERA COMMUNICATION

Implement:

Camera
↓
Frame Capture
↓
Buffer

---

# DAY 73 — IMAGE CAPTURE

Implement:

* capture frame
* display image
* optionally save image
* memory monitoring

---

# DAY 74 — BASIC COMPUTER VISION

Start with lightweight tasks:

* color detection
* QR detection
* simple image analysis

---

# DAY 75 — OBJECT/PERSON DETECTION FEASIBILITY

Benchmark:

* FPS
* RAM
* CPU
* latency
* heat
* reliability

Do not force advanced computer vision if the ESP32 cannot handle it reliably.

---

# DAY 76 — VISION → AURA BRAIN

Architecture:

Camera
↓
Vision Processing
↓
Event
↓
Decision Engine
↓
Response

Example:

Person detected.

AURA:

"Hello."

---

# DAY 77 — VISION MILESTONE

Minimum requirement:

Camera
↓
Image processing
↓
Useful result

Stretch goal:

Object/person detection.

---

# 13. PHASE 9 — FULL INTEGRATION + CASING

## DAYS 78–84

---

# DAY 78 — MASTER INTEGRATION

Connect:

* Voice
* Touch
* Camera
* Sensors
* AI
* Decision Engine
* Display
* Audio
* Storage
* Notifications

---

# DAY 79 — EXHIBITION MODE

Create:

AURA DEMO

├── AI
├── VISION
├── ENVIRONMENT
├── STUDY
├── MY BRAIN
└── AUDIO

Visitors should be able to understand the project quickly.

---

# DAY 80 — MY BRAIN MODE

Create the core demonstration:

SENSE
↓
UNDERSTAND
↓
THINK
↓
DECIDE
↓
ACT
↓
RESPOND

---

# DAY 81 — AUTOMATIC DEMO

Create a guided automatic demonstration.

The demo should require minimal operator interaction.

---

# DAY 82 — PHYSICAL ASSEMBLY

Move from temporary wiring to:

* secured wiring
* connectors
* mounting
* cable management
* serviceability

---

# DAY 83 — CASING

Build the first functional enclosure.

Required areas:

* display opening
* camera mount
* speaker grille
* microphone opening
* sensor openings
* ventilation
* charging/USB access
* service panel
* cable routing

---

# DAY 84 — PHYSICAL INTEGRATION MILESTONE

AURA must exist as one integrated desktop device.

No loose critical wiring should remain where it can easily disconnect during demonstration.

---

# 14. PHASE 10 — TESTING + FINAL V1.0

## DAYS 85–90

---

# DAY 85 — HARDWARE TEST

Check:

* power
* display
* touch
* DHT22
* DS3231
* SD
* DFPlayer
* speaker
* microphone
* PIR
* camera

---

# DAY 86 — SOFTWARE TEST

Check:

* boot
* UI
* commands
* AI
* memory
* Study Mode
* camera
* error handling
* recovery

---

# DAY 87 — LONG-DURATION TEST

Target:

8–12 hours minimum if practical.

Monitor:

* crashes
* memory
* temperature
* Wi-Fi
* SD
* sensors
* audio
* camera

---

# DAY 88 — FAILURE TESTING

Intentionally test:

* Wi-Fi disconnected
* AI unavailable
* SD removed
* sensor disconnected
* camera unavailable
* invalid command
* unexpected restart

AURA must fail gracefully.

---

# DAY 89 — DEMONSTRATION REHEARSAL

Run the complete demonstration repeatedly.

Fix:

* slow transitions
* crashes
* confusing UI
* audio problems
* camera problems
* network failures

---

# DAY 90 — AURA V1.0 RELEASE

Freeze the prototype.

Create:

```text
AURA V1.0
├── Firmware
├── Hardware
├── Documentation
├── Wiring Diagram
├── Pin Map
├── BOM
├── Demo Script
├── Known Issues
└── Future Roadmap
```

---

# 15. FINAL SOFTWARE ARCHITECTURE

```text
AURA/
├── main.cpp
├── core/
│   ├── system/
│   ├── state_machine/
│   ├── decision_engine/
│   ├── command_manager/
│   ├── action_manager/
│   ├── response_manager/
│   ├── memory/
│   └── diagnostics/
├── hardware/
│   ├── display/
│   ├── touch/
│   ├── audio/
│   ├── microphone/
│   ├── storage/
│   └── camera/
├── sensors/
│   ├── dht22/
│   ├── ds3231/
│   └── pir/
├── network/
│   ├── wifi/
│   └── api/
├── ai/
│   ├── routing/
│   ├── language/
│   ├── speech/
│   └── vision/
├── applications/
│   ├── assistant/
│   ├── study/
│   ├── entertainment/
│   └── exhibition/
├── config/
├── tests/
└── docs/
```

---

# 16. AURA AI ARCHITECTURE

The ESP32 should be treated as the embedded controller, not as a full modern AI computer.

## ESP32 responsibilities

* Sensors
* GPIO
* Display
* Touch
* Audio interfaces
* Local commands
* State management
* Communication
* Device control

## Cloud/additional processor responsibilities

Potentially:

* Large language model
* Speech recognition
* Text-to-speech
* Advanced computer vision
* Heavy AI inference

Architecture:

USER
↓
VOICE / TOUCH / CAMERA
↓
INPUT PROCESSING
↓
AURA BRAIN
├── Language AI
├── Context
└── Memory
↓
DECISION ENGINE
↓
ACTION MANAGER
├── Display
├── Audio
├── Sensors
└── External Devices
↓
RESPONSE

The current architecture documentation already separates input processing, AURA Brain, Decision Engine and Action Manager in this way.

---

# 17. HARDWARE INTEGRATION MATRIX

| Component            | Interface | Role                 | 90-Day Target |
| -------------------- | --------- | -------------------- | ------------- |
| ESP32                | —         | Main controller      | Required      |
| ILI9486 TFT          | SPI       | Display              | Required      |
| Touch                | TBD       | User input           | Required      |
| INMP441              | I2S       | Voice input          | Required      |
| DFPlayer Mini        | UART      | Audio                | Required      |
| Speaker              | Audio     | Voice/music          | Required      |
| DHT22                | GPIO      | Temperature/humidity | Required      |
| DS3231               | I2C       | Time                 | Required      |
| MicroSD              | SPI       | Storage              | Required      |
| PIR                  | GPIO      | Motion sensing       | Required      |
| Buzzer               | GPIO      | Alerts               | Required      |
| Camera               | TBD       | Vision               | Required      |
| Battery              | Power     | Portable operation   | Verify        |
| BMS                  | Power     | Battery protection   | Verify        |
| Buck converter       | Power     | Regulation           | Verify        |
| Additional processor | TBD       | Advanced AI/vision   | Decision gate |

---

# 18. CONTINUOUS TESTING STRATEGY

Every major feature follows:

BUILD
↓
UNIT TEST
↓
INTEGRATION TEST
↓
STRESS TEST
↓
DOCUMENT
↓
COMMIT

Testing categories:

## Unit Testing

Test individual functions.

## Hardware Testing

Test individual modules.

## Integration Testing

Test multiple modules together.

## Stress Testing

Test continuous operation.

## Recovery Testing

Test failure and restart behavior.

## User Testing

Test real human interaction.

---

# 19. GIT/GITHUB WORKFLOW

## Branches

main
develop
feature/*
hardware/*
fix/*

## Commit examples

feat: add DHT22 driver
feat: add AI command routing
feat: add study quiz engine
feat: add camera capture
fix: resolve SD initialization
fix: repair touch calibration
test: add WiFi failure test
docs: update architecture
refactor: separate action manager

## Version tags

v0.1 — hardware prototype
v0.2 — firmware foundation
v0.3 — UI
v0.4 — voice
v0.5 — AI
v0.6 — Study Mode
v0.7 — camera
v0.8 — integrated prototype
v0.9 — exhibition candidate
v1.0 — final 90-day prototype

---

# 20. WEEKLY REVIEW SYSTEM

At the end of every week:

## 1. What was completed?

List completed features.

## 2. What failed?

List bugs and hardware problems.

## 3. What was demonstrated?

Record working capabilities.

## 4. What remains?

Move unfinished tasks forward.

## 5. What is blocked?

Record missing components or dependencies.

## 6. Backup plan

If the next milestone fails, simplify rather than adding more features.

---

# 21. RISK AND FALLBACK PLAN

## Risk: ESP32 memory limitations

Fallback:

* reduce image resolution
* reduce buffers
* move heavy processing externally
* use cloud processing

---

## Risk: Camera processing too slow

Fallback:

Use:

* image capture
* QR detection
* simple vision

instead of advanced object recognition.

---

## Risk: Speech recognition unreliable

Fallback:

* push-to-talk
* touchscreen command selection
* cloud STT

---

## Risk: Wi-Fi unavailable

Fallback:

Offline mode supporting:

* clock
* alarms
* sensors
* music
* local commands
* Study content stored locally

---

## Risk: Power instability

Fallback:

* external adapter during exhibition
* battery as backup
* improve regulation
* reduce peak loads

---

## Risk: Too many features

Fallback:

Prioritize:

1. Reliability
2. Voice
3. AI
4. Touch
5. Study
6. Camera
7. Exhibition
8. Advanced features

---

## Risk: Casing not ready

Fallback:

Use a clean temporary enclosure while continuing development.

---

# 22. FINAL DAY-90 FEATURE TARGET

## Intelligence

* AI Q&A
* Basic conversation
* Command processing
* Decision Engine
* Short-term context
* Basic memory

## Interaction

* Voice
* Touch
* Audio
* Display

## Vision

* Camera capture
* Basic computer vision
* At least one useful visual demonstration

## Environment

* Temperature
* Humidity
* Motion
* Environmental information

## Assistant

* Time
* Date
* Alarm
* Timer
* Reminders
* Notifications

## Education

* Science
* Mathematics
* Computer/IT
* General Knowledge
* Learning mode
* Quiz
* Score
* Study timer
* Voice study

## Entertainment

* Music
* Audio control
* Sound effects

## Exhibition

* Exhibition Mode
* Automatic Demo
* My Brain
* Science demonstrations

## Engineering

* Modular firmware
* Diagnostics
* Logging
* Error handling
* Recovery
* Git/GitHub
* Documentation
* Stable power
* Integrated casing

---

# 23. FINAL 5–10 MINUTE EXHIBITION DEMONSTRATION

## 0:00–0:30 — Introduction

"AURA is a stationary AI Desk Assistant designed to sense, understand, decide, act and respond."

---

## 0:30–1:30 — Touch Interface

Demonstrate:

* Home
* Environment
* Time
* Settings

---

## 1:30–2:30 — Voice

Ask:

"AURA, what is the temperature?"

AURA reads the DHT22 and responds.

---

## 2:30–4:00 — AI

Ask:

"Explain artificial intelligence in simple terms."

AURA displays and speaks the answer.

---

## 4:00–5:00 — Vision

Demonstrate:

* camera
* image capture
* QR/object/basic vision feature

---

## 5:00–6:30 — Study Mode

Say:

"Start a Science Quiz."

Answer a question.

Show score.

---

## 6:30–7:30 — Science Demonstration

Show:

BEFORE
↓
CHANGE
↓
AFTER
↓
AURA ANALYSIS

---

## 7:30–8:30 — MY BRAIN

Show:

SENSE
↓
UNDERSTAND
↓
THINK
↓
DECIDE
↓
ACT
↓
RESPOND

---

## 8:30–10:00 — Automatic Demonstration

Run the automatic AURA demo sequence.

---

# 24. FINAL DAY-90 CHECKLIST

## Hardware

- [ ] ESP32 working
- [ ] Display working
- [ ] Touch working
- [ ] Microphone working
- [ ] Speaker working
- [ ] DFPlayer working
- [ ] DHT22 working
- [ ] DS3231 working
- [ ] MicroSD working
- [ ] PIR working
- [ ] Camera working
- [ ] Buzzer working
- [ ] Power system stable
- [ ] Wiring secured
- [ ] Casing assembled

---

# Software

- [ ] Firmware stable
- [ ] UI functional
- [ ] Voice interaction working
- [ ] AI interaction working
- [ ] Decision Engine working
- [ ] Memory working
- [ ] Study Mode working
- [ ] Quiz working
- [ ] Camera software working
- [ ] Error handling working
- [ ] Offline fallback working
- [ ] Logging working
- [ ] Diagnostics working

---

# Reliability

- [ ] Long-duration test completed
- [ ] Restart test completed
- [ ] Wi-Fi failure test completed
- [ ] SD failure test completed
- [ ] Sensor failure test completed
- [ ] Camera failure test completed
- [ ] Audio failure test completed
- [ ] Recovery test completed

---

# Exhibition

- [ ] Exhibition Mode working
- [ ] Automatic Demo working
- [ ] My Brain working
- [ ] AI demo working
- [ ] Voice demo working
- [ ] Study demo working
- [ ] Camera demo working
- [ ] Environmental demo working
- [ ] Complete 5–10 minute demonstration rehearsed

---

# Documentation

- [ ] README
- [ ] Architecture diagram
- [ ] Pin map
- [ ] Wiring diagram
- [ ] BOM
- [ ] Installation guide
- [ ] Troubleshooting guide
- [ ] API documentation
- [ ] Feature documentation
- [ ] Known limitations
- [ ] Future roadmap

---

# 25. DAYS 91–180 ROADMAP

After AURA V1.0, development should shift from "make more features" to "make AURA smarter, more reliable and more product-like."

---

# DAYS 91–110 — MEMORY + CONTEXT

Develop:

* persistent memory
* user preferences
* conversation history
* better context
* personalized responses
* task memory

---

# DAYS 111–130 — ADVANCED VISION

Develop:

* object detection
* person detection
* QR recognition
* better camera processing
* multimodal AI

---

# DAYS 131–145 — SMART HOME

Develop:

* Wi-Fi devices
* MQTT
* HTTP IoT APIs
* relays
* smart lights
* smart plugs

---

# DAYS 146–160 — SECURITY

Develop:

* PIR + camera
* event detection
* monitoring
* event logging
* alerts

---

# DAYS 161–175 — AURA AI

Combine:

Speech AI
+
Vision AI
+
Language AI
+
Memory
+
Decision Engine

into:

AURA BRAIN

---

# DAYS 176–180 — PRODUCT ENGINEERING

Focus on:

* improved casing
* thermal design
* PCB planning
* cable management
* serviceability
* privacy
* security
* product design
* manufacturing research

---

# 26. FINAL PROJECT PHILOSOPHY

The goal of the 90-day project is NOT:

"Add as many features as possible."

The goal is:

"Build one coherent AI Desk Assistant where the hardware, firmware, AI, UI, camera, memory and applications work together reliably."

The central AURA loop is:

SENSE
↓
UNDERSTAND
↓
THINK
↓
DECIDE
↓
ACT
↓
RESPOND
↓
SENSE AGAIN

AURA V1.0 should feel like one intelligent system rather than a collection of disconnected demonstrations.

---

# AURA V1.0

USER
↓
VOICE / TOUCH / CAMERA
↓
INPUT PROCESSING
↓
AURA BRAIN
↓
DECISION ENGINE
↓
ACTION MANAGER
↓
DISPLAY / AUDIO / HARDWARE
↓
RESPONSE
↓
USER

This is the foundation for turning AURA from a school prototype into a serious long-term AI desk-assistant platform.

---

# 27. 90-DAY DAILY CHECKLIST

- [x] Day 1
- [x] Day 2
- [x] Day 3
- [x] Day 4
- [ ] Day 5
- [ ] Day 6
- [ ] Day 7
- [ ] Day 8
- [ ] Day 9
- [ ] Day 10
- [ ] Day 11
- [ ] Day 12
- [ ] Day 13
- [ ] Day 14
- [ ] Day 15
- [ ] Day 16
- [ ] Day 17
- [ ] Day 18
- [ ] Day 19
- [ ] Day 20
- [ ] Day 21
- [ ] Day 22
- [ ] Day 23
- [ ] Day 24
- [ ] Day 25
- [ ] Day 26
- [ ] Day 27
- [ ] Day 28
- [ ] Day 29
- [ ] Day 30
- [ ] Day 31
- [ ] Day 32
- [ ] Day 33
- [ ] Day 34
- [ ] Day 35
- [ ] Day 36
- [ ] Day 37
- [ ] Day 38
- [ ] Day 39
- [ ] Day 40
- [ ] Day 41
- [ ] Day 42
- [ ] Day 43
- [ ] Day 44
- [ ] Day 45
- [ ] Day 46
- [ ] Day 47
- [ ] Day 48
- [ ] Day 49
- [ ] Day 50
- [ ] Day 51
- [ ] Day 52
- [ ] Day 53
- [ ] Day 54
- [ ] Day 55
- [ ] Day 56
- [ ] Day 57
- [ ] Day 58
- [ ] Day 59
- [ ] Day 60
- [ ] Day 61
- [ ] Day 62
- [ ] Day 63
- [ ] Day 64
- [ ] Day 65
- [ ] Day 66
- [ ] Day 67
- [ ] Day 68
- [ ] Day 69
- [ ] Day 70
- [ ] Day 71
- [ ] Day 72
- [ ] Day 73
- [ ] Day 74
- [ ] Day 75
- [ ] Day 76
- [ ] Day 77
- [ ] Day 78
- [ ] Day 79
- [ ] Day 80
- [ ] Day 81
- [ ] Day 82
- [ ] Day 83
- [ ] Day 84
- [ ] Day 85
- [ ] Day 86
- [ ] Day 87
- [ ] Day 88
- [ ] Day 89
- [ ] Day 90
