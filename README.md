# AURA AI Desk Assistant

AURA is an ESP32-based stationary AI desk assistant being developed as a school prototype. It is designed to bring together touch interaction, environmental sensing, audio, Wi-Fi/cloud AI, study support, camera experiments, and a professional exhibition experience.

AURA V1.0 is **not** a mobile robot. Wheels, motors, navigation, obstacle avoidance, and autonomous movement are outside its scope.

## Hardware platform

- Main controller: ESP32 WROOM DevKit
- Build environment: PlatformIO
- PlatformIO board: `esp32dev`
- Framework: Arduino

The documented V1 hardware plan includes a TFT/touchscreen, DHT22, DS3231 RTC, MicroSD, DFPlayer-compatible audio module, speaker/amplifier, INMP441 microphone, PIR sensor, ESP32-CAM, buzzer, and a 2S2P battery system.

## Repository layout

```text
src/            Main PlatformIO firmware entry point
firmware/       Firmware architecture and future modular firmware assets
core/           Core system services and decision flow
hardware/       Hardware drivers and hardware documentation
sensors/        Sensor-specific code
network/        Wi-Fi and API code
ai/             Language, routing, speech, and vision code
applications/   Assistant, study, entertainment, and exhibition features
docs/           Project design, audit, and planning documents
tests/          Project tests
```

## Build

1. Install [PlatformIO](https://platformio.org/).
2. Open this repository as a PlatformIO project.
3. Select the `esp32dev` environment.
4. Build the project.
5. Connect the ESP32 and upload only after its wiring and power rails have been verified.

## Project documentation

- [90-day roadmap](docs/90_DAYS_ROADMAP.md)
- [Detailed execution guide](docs/AURA_90DAY_DETAILED_EXECUTION_GUIDE.md)
- [Current status audit](docs/AURA_CURRENT_STATUS.md)
- [V1 requirements](docs/AURA_V1_REQUIREMENTS.md)
- [Software architecture](docs/AURA_SOFTWARE_ARCHITECTURE.md)
- [Pin map](docs/AURA_PINMAP_V1.md)
- [Power audit](docs/AURA_POWER_AUDIT.md)

## Development workflow

`main` holds stable, reviewed work. Day-to-day work starts from `develop` and uses branches such as `feature/<name>`, `hardware/<name>`, `docs/<name>`, and `fix/<name>`.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the complete workflow.

## License

No license has been selected yet. All rights are reserved until one is added.
