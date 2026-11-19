# Contributing to AURA

## Branch strategy

- `main` — stable, reviewed project baseline.
- `develop` — integration branch for completed work before it reaches `main`.
- `feature/<name>` — a user-facing or firmware feature, for example `feature/dht22-driver`.
- `hardware/<name>` — hardware bring-up, wiring, or bench-test work, for example `hardware/rtc-test`.
- `docs/<name>` — documentation work, for example `docs/power-audit`.
- `fix/<name>` — defect corrections, for example `fix/sd-init`.

Create new work branches from `develop`. Merge only tested, documented work back into `develop`; promote stable milestones from `develop` to `main`.

## Commit messages

Use concise, imperative commit messages with one of these prefixes:

- `feat:` — add a feature
- `fix:` — correct a defect
- `docs:` — update documentation
- `test:` — add or update tests
- `refactor:` — reorganize code without changing behavior
- `chore:` — maintenance work

Examples:

```text
feat: add DHT22 driver
fix: repair touch calibration
docs: update pin map
test: add Wi-Fi failure test
refactor: improve command manager
```

## Before committing

1. Keep secrets, Wi-Fi credentials, API keys, and personal data out of the repository.
2. Build the PlatformIO project when firmware changes.
3. Test changes on real hardware when the task involves a peripheral.
4. Record test results and known limitations in the relevant document.
5. Do not mark a hardware feature complete without evidence of a real test.
