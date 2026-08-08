# QA-003 DOCX Content Vertical Slice Report

## Document Meta

- version: 0.1
- qa agent: codex
- date: 2026-08-08
- status: pass with residual visual/asset risks
- code under test: `e60389a feat-024 rebuild opening to terminal flow from visual docx`
- ops baseline: `419c1dc chore-004 define final asset drop contract from docx references`

## Scope

Validate the DOCX-content conversion phase:

- `feat-021` DOCX Category A file content
- `feat-022` DOCX-based ECHO argument flow
- `feat-023` resource pressure feedback
- `feat-024` opening-to-terminal visual flow
- `chore-004` final asset drop contract

## Environment Checks

| check | result | notes |
| --- | --- | --- |
| `npm run build` | pass | Vite production build completed |
| `git diff --check` | pass | no whitespace errors in code or ops changes |
| local Vite server | pass | `npm run dev -- --host 127.0.0.1` started successfully |
| HTTP response | pass | `curl -I http://127.0.0.1:5173/` returned `200 OK` |

## DOCX Source QA Matrix

| source expectation | implementation result | result |
| --- | --- | --- |
| `우주선 탈출게임 로그 예시.docx`: Category A file tree includes Logs, Personnel, System/Security, Utilities, Recycle_Bin | Code fixture keeps the expected directories and canonical Category A evidence path | pass |
| `우주선 탈출게임 로그 예시.docx`: Act 1 relies on `sensor_calib.log` with 186-day calibration drift and ±2.3°C error | `sensor_calib.log` includes 186 days, +2.3C drift, manual scan verification language | pass |
| `우주선 탈출게임 로그 예시.docx`: Act 2 uses `email_chain_july.txt` to discover PIN `8842` and restore `quarantine_rules.conf` | Email thread includes PIN and Log_Fixer cue; security folder remains password-gated | pass |
| `우주선 탈출게임 로그 예시.docx`: `quarantine_rules.conf` exists as corrupted and recovered states | Code includes both corrupted and recovered content with `+17520_HOURS` | pass |
| `우주선 탈출게임 개요.docx`: ECHO argues in 3 stages and accepts success/partial/wrong/old evidence paths | Deterministic ECHO matrix now includes Act claims, partial handling, wrong submission, old evidence, repeat hints, prompt tampering | pass |
| `LOG_OUT visual 복사본.docx`: first screen should read as control room/computer before lockdown | Initial overlay now reads as standby control-room computer approach, not pre-locked terminal dashboard | pass |
| `LOG_OUT visual 복사본.docx`: opening should depict normal work, alert, door lock, crew interruption, ECHO declaration, terminal handoff | Opening timeline still carries all DOCX beats and gameplay starts only after handoff | pass |
| `LOG_OUT visual 복사본.docx`: resource thresholds should affect visual/audio feel | Power thresholds now show delay text, stronger CSS feedback, placeholder cues, blackout reboot text | pass |
| `asset_plan.md` / visual DOCX: final asset specs should be explicit | `project/final_asset_drop_contract.md` defines paths, formats, triggers, and fallbacks | pass |

## Manual Interaction Coverage

This QA pass did not use browser click automation. Based on static flow review and build/runtime checks, the intended manual happy path is:

1. Click the control-room computer.
2. Let the opening sequence reach terminal handoff or use the debug skip.
3. Read `/Logs/Sensors/sensor_calib.log`.
4. Attach `sensor_calib.log` and explain calibration drift/186 days/temperature error.
5. Read `/Personnel/Dr_Kim/email_chain_july.txt` for `8842`.
6. Unlock `/System/Security`.
7. Open `Log_Fixer.exe`, select `Text Reconstruction`, recover `/System/Security/quarantine_rules.conf`.
8. Attach recovered `quarantine_rules.conf` and explain `72_HOURS` plus `+17520_HOURS`.
9. Attach `ai_priority_matrix.json` and `deleted_override.txt`.
10. Complete final review and Normal Ending A.

## Residual Risks

- No pixel-level comparison against embedded DOCX images/GIF was performed.
- No browser click automation was available in this QA pass, so interactive path validation is reasoned from code plus server checks.
- Final GLB/audio/image assets are still missing; placeholder fallback behavior is expected.
- The current implementation still covers Category A only; 10-category replay remains out of scope.
- External AI/API ECHO remains deferred to `feat-007`.

## QA Decision

QA-003 passes for the DOCX-content vertical slice phase.

No new blocking bug tasks are required from this pass.

