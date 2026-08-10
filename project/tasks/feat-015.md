# feat-015 Add resource pressure HUD and threshold effects

## Status

- status: done
- type: feat
- priority: 19
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-015 add resource pressure hud and threshold effects`

## Goal

Make oxygen and power feel like emergency pressure, not only numbers.

## Scope

- Display O2 level, power level, and elapsed/session time in the planned HUD style (completely removing `NORMAL SESSION` / `Act-1` labels (Q43) and `drain x1.0x` text (Q48)).
- Apply power thresholds: Normal, Caution, Warning, Critical, Blackout.
- Match the DOCX crisis monitor direction: red alert status, strong monitor glow, oxygen/power bars, and surrounding-room warning signage or placeholder equivalents.
- Add Caution file/viewer delay, Warning Log_Fixer slowdown, Critical vignette/cursor shake, and Blackout reboot lock.
- On wrong submission, show a clear power surge moment with Korean warning title ("전력 서지 경고") and copy ("ECHO 경고: 잘못된 절차 주장은 헤르메스 전력 라인을 불안정하게 만듭니다.") for 2 seconds (2000ms) (feat-041 / Q64).
- On Blackout event (power 0%), render exactly ONE single alert popup (blocking duplicate Power Surge popup), positioned at **screen center (Center Modal)** with high-contrast emphasis styling and Korean alert text: `"⚠️ [전력 고갈] 주 전력 그리드 블랙아웃! OS 터미널 긴급 재부팅 중... (남은 시간: N초)"` (Q30 user feedback).
- Keep debug timer and normal 60-minute mode separated, and support HUD pause (`⏸️`) button and pause modal with O₂/timer freeze (feat-041).

## Dependencies

- before: `feat-003`, `bug-001`, `bug-002`
- after: `feat-018`, `feat-019`, `qa-002`

## Acceptance Criteria

- [x] HUD shows O2 percentage and power level, with `NORMAL SESSION`, `Act-1` labels and `drain x1.0x` text completely removed (Q43, Q48).
- [x] Red Alert/Critical presentation affects both monitor UI and surrounding scene treatment when available.
- [x] Power threshold changes affect visuals and at least one interaction timing behavior.
- [x] Blackout includes a timed reboot sequence before power recovery.
- [x] On Blackout event (power 0%), exactly one single popup is rendered at screen center (Center Modal) with high-contrast emphasis style and Korean copy ("⚠️ [전력 고갈] 주 전력 그리드 블랙아웃! OS 터미널 긴급 재부팅 중... (남은 시간: N초)"), preventing duplicate Power Surge popups.
- [x] Wrong evidence penalty feels like a ship-system event.
- [x] Resource behavior remains deterministic and testable.

## Implementation Notes

- Added session remaining/elapsed time, O2 drain multiplier, file access delay, recovery delay, and blackout reboot countdown to the HUD.
- Added power threshold timing behavior: Caution/Warning/Critical file access delay and Warning/Critical Log_Fixer slowdown.
- Added wrong-submission `POWER SURGE` event copy and temporary monitor surge styling.
- Added Critical jitter and stronger warning/blackout HUD glow.
- Preserved deterministic resource calculations from `resourceState.ts`.

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- review-agent result: approved

## Delivery

- workflow: latest `main` -> task commit -> push `main`
- code commit: `1e9cfd2 feat-015 add resource pressure hud and threshold effects`

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT visual 기획서.md`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/phase_2_original_source_replan.md`
- `project/docx_source_reassessment.md`

## Asset Inputs

- `public/assets/images/fx/glitch-noise.webp`
- `public/assets/images/fx/red-vignette.webp`
- `public/assets/audio/sfx_wrong_surge.ogg`
- `public/assets/audio/sfx_blackout_clunk.ogg`
- `public/assets/audio/sfx_reboot.ogg`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-06 | dev-agent | todo -> in_progress | Resource pressure HUD and threshold effects started from latest main |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff validation passed; no blocking findings |
| 2026-08-06 | dev-agent | approved -> done | Code committed and pushed directly to main |
