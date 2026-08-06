# DOCX Source Reassessment

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-06
- status: task updates applied
- purpose: Reassess planning after the original markdown documents were reattached as DOCX files with intact images.

## DOCX Sources Reviewed

- `project/human-input/우주선 탈출게임 개요.docx`
- `project/human-input/우주선 탈출게임 로그 예시.docx`
- `project/human-input/우주선 탈출 게임 로그 파일 구조.docx`
- `project/human-input/우주선 탈출 게임 AI 프롬프트 예시.docx`
- `project/human-input/LOG_OUT visual 복사본.docx`

## PM Judgment

The DOCX files do not invalidate the Phase 2 direction. They make the intended experience sharper and more visual.

Current Phase 2 should remain a Category A vertical slice, but the implementation bar must be raised from "systems exist" to "the game looks and feels like the attached DOCX references."

The strongest missing intent is visual framing:

- Main menu should be a 3D Hermes control-room/computer composition, not a flat overlay.
- Menu title treatment should allow `LOGOUT ISOLATION` / `THE ECHO PROTOCOL` style branding, while preserving `LOGOUT` as the project title.
- PLAY/QUIT should feel like monitor/holographic UI elements layered over the central computer.
- Opening should use the player's hands only during cutscene beats, not during terminal gameplay.
- In-game UI should feel embedded inside the physical monitor frame.
- Red Alert, power loss, and oxygen depletion should affect both the OS chrome and surrounding room.
- The door is a core narrative object. Door lock/unlock must be visible, not only described in text.

## Implementation Feasibility

The current stack can implement the DOCX reference direction:

- Vite + React can drive scene/game UI state.
- React DOM can render the Hermes OS and menu overlay sharply.
- R3F/Three can render the control room, monitor frame, door, window, lights, and camera transitions.
- CSS can provide blur, scanline, glitch, vignette, particles, and monitor chrome effects.
- WebAudio or static audio files can cover the required placeholder soundscape.

The main technical limitation is asset quality, not framework capability. Final fidelity depends on a suitable control-room GLB, hands model/animation, space background, and audio pack. Until then, dev agents must provide placeholder geometry and CSS/WebAudio fallbacks that preserve behavior and composition.

## Conflict Resolution

The new DOCX set repeats the known Act 3 conflict:

- `우주선 탈출게임 로그 예시.docx` supports the current Category A MVP pair: `ai_priority_matrix.json` + `deleted_override.txt`.
- `우주선 탈출 게임 로그 파일 구조.docx`, `우주선 탈출게임 개요.docx`, and `LOG_OUT visual 복사본.docx` also include the power-route example: `auxiliary_capacitor.log` + `emergency_grid_switch.conf`.

Current Phase 2 keeps the already-confirmed Category A MVP pair:

- `/System/Security/ai_priority_matrix.json`
- `/Recycle_Bin/deleted_override.txt`

The power-route remains a later expansion candidate. It must not be silently substituted into current dev tasks.

## Updated Task Mapping

No extra duplicate feature task is needed. The existing Phase 2 task set is still correct, but these tasks now have DOCX-specific acceptance requirements:

| task id | update from DOCX review |
| --- | --- |
| feat-012 | Main menu must match DOCX/GIF reference composition: oblique control room, central monitor, holographic title/buttons, blur fade, PLAY-to-opening camera transition |
| feat-015 | Resource pressure must match red-alert monitor and surrounding-room treatment from overview DOCX images |
| feat-016 | Hermes OS must feel embedded inside monitor chrome with top resource bars, window controls, tree/path/preview, and ECHO panel |
| feat-018 | Audio cues must cover hum, siren, decompression, door clunk, notifications, ECHO ping, typing, wrong surge, success, blackout, reboot, and HUD ignition |
| feat-019 | 3D scene must support menu computer view, door-focused view, terminal-focused view, red/cool lighting, window/starfield, console props, and visible door lock/release |
| feat-020 | Ending A must show the physical door release and a clear result panel, not just a text completion state |
| qa-002 | QA must compare implementation against DOCX text and embedded image/GIF references |

## Asset Requirements Confirmed By DOCX

Runtime asset paths remain under `log-out/public/assets`.

### Required For Phase 2 Visual Fidelity

| asset | path | requirement |
| --- | --- | --- |
| Control room model | `public/assets/models/control-room.glb` | Must include central monitor desk, side consoles, rear/side door, window, ceiling lights, wall panels, pipes, keyboard, mouse, mug/clipboard props or placeholders |
| Player hands | `public/assets/models/player-hands-typing.glb` | Opening-only hands with typing, startle, desk grip, idle tense, hide-down clips |
| Space background | `public/assets/images/space/space-panorama.webp` | Starfield/nebula visible through windows; 2048x1024 minimum, 4096x2048 preferred |
| Menu logo treatment | `public/assets/images/ui/logout-title.svg` | Optional; can be implemented as CSS text first. Should support `LOGOUT ISOLATION` and `THE ECHO PROTOCOL` visual treatment if provided |
| Monitor UI icons | `public/assets/images/ui/file-icons/*.svg` | Folder, log, txt, conf, json, exe, locked, corrupted, recovered |
| Crisis overlays | `public/assets/images/fx/glitch-noise.webp`, `public/assets/images/fx/red-vignette.webp` | Used for warning/critical/blackout monitor effects |

### Required Audio Pack

| asset | path |
| --- | --- |
| Ship hum loop | `public/assets/audio/amb_ship_hum_loop.ogg` |
| PLAY transition | `public/assets/audio/sfx_play_start.ogg` |
| Warning siren | `public/assets/audio/sfx_warning_siren.ogg` |
| Pneumatic decompression | `public/assets/audio/sfx_decompression.ogg` |
| Door lock/release | `public/assets/audio/sfx_door_lock_clunk.ogg` |
| Notification popup | `public/assets/audio/sfx_notification_popup.ogg` |
| Communication glitch | `public/assets/audio/sfx_comm_glitch.ogg` |
| ECHO ping | `public/assets/audio/sfx_echo_ping.ogg` |
| Typing loop | `public/assets/audio/sfx_typing_loop.ogg` |
| HUD ignition | `public/assets/audio/sfx_hud_ignition.ogg` |
| Wrong evidence surge | `public/assets/audio/sfx_wrong_surge.ogg` |
| Success chime | `public/assets/audio/sfx_success_chime.ogg` |
| Blackout cutoff | `public/assets/audio/sfx_blackout_clunk.ogg` |
| Reboot | `public/assets/audio/sfx_reboot.ogg` |

## QA Rule

For Phase 2, "placeholder allowed" means final art can be missing. It does not mean the experience can ignore the DOCX composition. A placeholder must still express camera view, monitor framing, door state, light state, OS layout, and audio trigger intent.
