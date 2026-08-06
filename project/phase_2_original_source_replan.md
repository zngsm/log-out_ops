# Phase 2 Original Source Replan

## Document Meta

- version: 0.2
- pm agent: codex
- date: 2026-08-06
- status: ready for task execution
- purpose: Re-plan the next phase from the original `LOG_OUT **.md` documents, not from the already-simplified task output.

## Source Hierarchy

When planning, implementing, or reviewing LOG_OUT, agents must use this priority order:

1. Primary source: `project/human-input/LOG_OUT 기획서.md`
2. Primary source: `project/human-input/LOG_OUT visual 기획서.md`
3. Primary source: `project/human-input/LOG_OUT 로그 예시.md`
4. Primary source: `project/human-input/LOG_OUT AI 프롬포트 예시.md`
5. Primary source: `project/human-input/LOG_OUT 로그파일 구조.md`
6. Primary source with intact images: `project/human-input/우주선 탈출게임 개요.docx`
7. Primary source with intact images: `project/human-input/LOG_OUT visual 복사본.docx`
8. Primary source: `project/human-input/우주선 탈출게임 로그 예시.docx`
9. Primary source: `project/human-input/우주선 탈출 게임 로그 파일 구조.docx`
10. Primary source: `project/human-input/우주선 탈출 게임 AI 프롬프트 예시.docx`
11. Human answers: `project/human-input/LOG_OUT_PM_QA.md`
12. PM-derived specs and task docs

If derived specs conflict with `LOG_OUT **.md`, PM must not let dev agents infer a direction. PM must either apply the primary-source rule or ask the human.

## Canonical Decisions For Current Phase

- MVP scenario is Category A only.
- Current Act 3 canonical evidence is `ai_priority_matrix.json` + `deleted_override.txt`.
- `LOG_OUT 기획서.md` also contains a later rough-section power-route idea using `auxiliary_capacitor.log` + `emergency_grid_switch.conf`. For this phase, the top 1-hour timeline plus `LOG_OUT 로그 예시.md` wins. The power-route idea can become a later phase expansion only after human approval.
- External AI remains deferred until provider/model/env/fallback policy is answered. Phase 2 must therefore improve ECHO with deterministic scripted behavior first.
- Placeholder assets are allowed, but placeholder behavior must still express the original game direction.
- The DOCX versions exist because MD image references can break. For visual implementation, dev/QA agents must treat the DOCX embedded images/GIF as the practical visual reference.

## Original Intent Summary

LOG_OUT is not only a file-submission puzzle. It is a first-person SF mystery escape game where the player is physically trapped in the Hermes control room, under oxygen pressure, while dismantling ECHO's cold but flawed quarantine logic through logs, file recovery, and proof submission.

The intended experience depends on pacing and sensory detail:

- A main menu that starts from a 3D control room/computer composition.
- A menu composition where the central monitor/desk sits inside a visible control room, with `LOGOUT ISOLATION` / `THE ECHO PROTOCOL` style title treatment and PLAY/QUIT as monitor/holographic controls.
- A roughly 60-second opening sequence with peaceful work, alarm escalation, door lock, crew messages, ECHO interruption, and terminal focus transition.
- A Hermes OS that feels like an in-world ship computer rather than a generic app.
- ECHO acting as a procedural authority with staged claims, partial-success handling, redundant-evidence handling, wrong-answer escalation, and reverse hints after repeated failures.
- Oxygen and power becoming visible, audible pressure through HUD, lighting, delays, glitches, blackout, and reboot.
- Files that invite deduction through diegetic logs, not direct answer notes.

## Current Implementation Gap

| area | expected from original docs | current gap |
| --- | --- | --- |
| Main menu | 3D control room diagonal view with `LOGOUT`, `PLAY`, `QUIT` | No true menu-to-opening transition |
| Opening | 00:00-01:00 directed sequence with hands, alarm, door lock, crew messages, ECHO typing | Current intro is compact text overlay |
| Monitor framing | Hermes OS appears inside a physical monitor frame with window chrome and top resource bars | Current UI is full-page web layout with partial 3D backdrop |
| Scene pacing | Explicit Act beats and input lock during ECHO processing | Broad UI state changes only |
| ECHO | Cold procedural persona, decision matrix, partial/redundant/repeat-hint behavior | Mostly generic deterministic feedback |
| Resource pressure | O2 multiplier, power thresholds, delay/glitch/sound/reboot effects | Mechanics exist, presentation incomplete |
| File explorer | Path/search/tree/metadata, single/double/right-click behavior | Basic list/viewer interaction |
| Log_Fixer | CUI popup, path input, repair mode, progress, restored highlight | Simplified direct recovery |
| Content | Original Category A files, decoys, and clue density | Useful but still too checklist-like |
| Audio | Ship hum, siren, door clunk, ECHO ping, typing, surge, blackout silence | Mostly missing |
| 3D scene | Reacts to scene/power states and supports immersion | Mostly static backdrop |
| Ending | 5-second review mode, door release, result panel | Minimal ending-ready overlay |

## Next Phase Goal

Build a first vertical slice that feels like LOG_OUT as described in the original docs.

This phase should not chase all future categories or final-quality assets. It should make Category A feel paced, trapped, audible, reactive, and deductive.

## Next Phase Task Set

| task id | type | title | dependency | purpose |
| --- | --- | --- | --- | --- |
| feat-012 | feat | Add DOCX-reference main menu and directed opening sequence | feat-008, feat-009, feat-010 | Recreate the original menu-to-60-second-opening-to-terminal transition |
| feat-013 | feat | Add scene runtime and Act beat orchestration | feat-005, feat-010, feat-012 | Convert Act transitions into explicit scene beats with locks and ECHO timing |
| feat-014 | feat | Implement ECHO decision matrix and persona responses | feat-005, feat-013 | Make ECHO behave like the original rule-bound AI without external API |
| feat-015 | feat | Add resource pressure HUD and threshold effects | feat-003, bug-001, bug-002 | Make oxygen/power pressure visible and behaviorally meaningful |
| feat-016 | feat | Improve Hermes file explorer interaction fidelity | feat-002, feat-011 | Add path/search/tree/metadata/context-menu style interactions |
| feat-017 | feat | Rework Log_Fixer into mini-program flow | feat-006, feat-016 | Match original recovery tool fantasy instead of one-click recovery |
| chore-003 | chore | Rewrite Category A content into diegetic clue layer | feat-004, chore-002 | Align exact files with original examples and hide direct hints behind debug |
| feat-018 | feat | Add placeholder audio system and sound cues | feat-012, feat-014, feat-015 | Use WebAudio/static assets to communicate ship, ECHO, warning, success, blackout |
| feat-019 | feat | Integrate DOCX-reference 3D control room with scene and resource state | feat-009, feat-012, feat-015 | Make lighting/camera/monitor/door states react to the game |
| feat-020 | feat | Add directed Ending A and result panel | feat-013, feat-014, feat-018, feat-019 | Deliver the original final review, door release, and survival result beat |
| qa-002 | chore | Run original-source vertical slice QA | feat-012 through feat-020, chore-003 | Validate against original docs, not only task mechanics |

## Required Asset Specification

Agents must support placeholder fallback if an asset is missing. When the human provides final assets, place them under `log-out/public/assets`.

### 3D Models

| path | required for | format | spec |
| --- | --- | --- | --- |
| `public/assets/models/control-room.glb` | Main menu, opening, gameplay background | GLB/GLTF | Units in meters, origin near floor center, PBR materials, 2K textures max for MVP, recommended under 15 MB |
| `public/assets/models/player-hands-typing.glb` | Opening only | GLB/GLTF | Rigged or pre-animated hands with clips named `typing_loop`, `startle`, `desk_grip`, `idle_tense`, `hide_down` |

Expected control-room node names:

- `Door_Main`
- `Monitor_Main`
- `Monitor_Frame`
- `Door_Main`
- `Door_Lock_Indicator`
- `Desk`
- `Keyboard`
- `Mouse`
- `Window`
- `Side_Console_L`
- `Side_Console_R`
- `Ceiling_Lights_Normal`
- `Emergency_Lights`
- `Side_Panels`

### Images And UI Icons

| path | required for | format | spec |
| --- | --- | --- | --- |
| `public/assets/images/sensor_diagram.png` | `/Logs/Sensors/sensor_diagram.png` file viewer | PNG/WebP | 1024x1024 or 1920x1080, readable sensor schematic, references `SENSOR-BIO-04` and control room module |
| `public/assets/images/space/space-panorama.webp` | control room windows | WebP/PNG | 2048x1024 minimum, 4096x2048 preferred, starfield/nebula background |
| `public/assets/images/ui/logout-title.svg` | optional menu title asset | SVG | Optional; CSS text fallback is acceptable. Should support `LOGOUT ISOLATION` and `THE ECHO PROTOCOL` treatment if supplied |
| `public/assets/images/ui/echo-logo.svg` | ECHO panel branding | SVG | Monochrome or two-tone, visible on dark terminal UI |
| `public/assets/images/ui/file-icons/*.svg` | File explorer states | SVG | folder, locked folder, `.log`, `.txt`, `.conf`, `.json`, `.exe`, corrupted, recovered |
| `public/assets/images/fx/glitch-noise.webp` | Warning/Critical UI overlay | WebP/PNG | Tileable or full-screen transparent glitch/noise texture |
| `public/assets/images/fx/red-vignette.webp` | Critical oxygen/power state | WebP/PNG | Transparent vignette overlay, 1920x1080 preferred |

### Audio

Use `.ogg` as primary and optional `.mp3` fallback. Recommended 44.1 kHz, normalized for web playback.

| path | trigger | spec |
| --- | --- | --- |
| `public/assets/audio/amb_ship_hum_loop.ogg` | Menu/opening/gameplay background | Seamless 30-60s loop, low engine hum |
| `public/assets/audio/sfx_play_start.ogg` | PLAY click and camera transition | Short UI/terminal transition sound |
| `public/assets/audio/sfx_warning_siren.ogg` | Opening alarm and warning power state | Low warning siren, not painful on loop |
| `public/assets/audio/sfx_decompression.ogg` | Opening door pressure loss | Pneumatic decompression sound |
| `public/assets/audio/sfx_door_lock_clunk.ogg` | Opening door lock, ending release | Heavy mechanical lock sound |
| `public/assets/audio/sfx_notification_popup.ogg` | Crew/ECHO notification line appears | Short terminal popup sound |
| `public/assets/audio/sfx_comm_glitch.ogg` | ECHO cuts crew communication | Communication cutoff/glitch burst |
| `public/assets/audio/sfx_echo_ping.ogg` | ECHO message starts/ends | Cold digital ping |
| `public/assets/audio/sfx_typing_loop.ogg` | ECHO typing or opening work beat | Subtle keyboard/terminal typing loop |
| `public/assets/audio/sfx_hud_ignition.ogg` | HUD appears and O2 countdown starts | Short activation beep |
| `public/assets/audio/sfx_wrong_surge.ogg` | Wrong evidence power penalty | Electrical surge/glitch hit |
| `public/assets/audio/sfx_success_chime.ogg` | Correct evidence accepted | Restrained confirmation sound |
| `public/assets/audio/sfx_blackout_clunk.ogg` | Power reaches blackout | Sudden cutoff and low thud |
| `public/assets/audio/sfx_reboot.ogg` | 10-second reboot recovery | Boot sequence or relay restart |

### Data Files

| path | required for | spec |
| --- | --- | --- |
| `src/game/openingTimeline.ts` or `.json` equivalent | feat-012 | Timestamped beats for 00:00-01:00 opening |
| `src/game/sceneTimeline.ts` or `.json` equivalent | feat-013 | Scene ids, entry lines, lock durations, success transitions |
| `src/game/echoResponseMatrix.ts` or `.json` equivalent | feat-014 | success/partial/incorrect/redundant/repeat-hint response rules |

## Human Questions For Later

These do not block the phase 2 deterministic vertical slice unless a task explicitly marks them as required:

- Should external AI resume immediately after `feat-014`, or only after `qa-002` proves the scripted version?
- Should the opening always last the full 60 seconds, or should normal play allow skip after first completion?
- Should the power-route Act 3 variant become Phase 3, an alternate ending route, or be retired?
- Should final assets be produced now, or should placeholder assets remain through vertical-slice QA?

## PM Instruction

When a dev agent is assigned a task from this phase, it must read this document plus the relevant original `LOG_OUT **.md` source sections before implementation. It must not implement from old derived task assumptions if they contradict this replan.
