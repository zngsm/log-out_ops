# Final Asset Drop Contract

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-08
- status: ready for human asset production
- purpose: Define exact asset paths and fallback behavior for LOG_OUT final art/audio delivery.

## Root Path

All production assets should be placed in the code repo under:

`log-out/public/assets`

The game must continue to build if any final asset is missing. Missing final assets should fall back to CSS/R3F/WebAudio placeholders.

## 3D Models

| path | format | used in | required nodes/clips | spec | fallback |
| --- | --- | --- | --- | --- | --- |
| `public/assets/models/control-room.glb` | `.glb` | menu, opening, gameplay backdrop, ending | nodes: `Door_Main`, `Monitor_Main`, `Monitor_Frame`, `Door_Lock_Indicator`, `Desk`, `Keyboard`, `Mouse`, `Window`, `Ceiling_Lights_Normal`, `Emergency_Lights`, `Side_Console_L`, `Side_Console_R` | meters scale, origin near floor center, PBR materials, 2K textures max, target under 15 MB | current R3F procedural control room |
| `public/assets/models/player-hands-typing.glb` | `.glb` | opening 00:00~00:52 only | clips: `typing_loop`, `startle`, `desk_grip`, `idle_tense`, `hide_down` | rigged or baked animation, hands only, no full body required | current 2D hand placeholder |

## Images And UI

| path | format | used in | spec | fallback |
| --- | --- | --- | --- | --- |
| `public/assets/images/sensor_diagram.png` | `.png` or `.webp` | `/Logs/Sensors/sensor_diagram.png` viewer | 16:9 or 4:3 schematic, 1920px wide max, readable labels for `SENSOR-BIO-04` and Control Room Module #04 | text schematic card |
| `public/assets/images/fx/glitch-overlay.webp` | `.webp` | Warning/Critical terminal overlay | 1920x1080 transparent or dark overlay | CSS scanlines |
| `public/assets/images/fx/red-vignette.webp` | `.webp` | Critical state | 1920x1080 transparent red vignette | CSS radial vignette |
| `public/assets/images/ui/icon-file-log.svg` | `.svg` | file explorer | 64x64, Hermes cool-blue style | text `FILE` icon |
| `public/assets/images/ui/icon-file-conf.svg` | `.svg` | file explorer | 64x64, Hermes cool-blue style | text `FILE` icon |
| `public/assets/images/ui/icon-file-json.svg` | `.svg` | file explorer | 64x64, Hermes cool-blue style | text `FILE` icon |
| `public/assets/images/ui/icon-file-exe.svg` | `.svg` | file explorer | 64x64, Hermes cool-blue style | text `EXE` icon |
| `public/assets/images/ui/icon-folder-locked.svg` | `.svg` | locked directory state | 64x64, amber/red lock mark | text `LOCK` icon |

## Audio

Preferred delivery: both `.mp3` and `.ogg` if possible. If only one format is provided, `.mp3` is acceptable for MVP.

| path | trigger | spec | fallback |
| --- | --- | --- | --- |
| `public/assets/audio/ambience-ship-hum.mp3` | menu/opening/gameplay ambient bed | seamless loop, 44.1 kHz, 192 kbps | WebAudio low sine hum |
| `public/assets/audio/sfx-keyboard-typing.mp3` | opening 00:00~00:10, ECHO typing moments | short loop or 3~6 sec bed | WebAudio ticks |
| `public/assets/audio/sfx-warning-siren.mp3` | opening alarm, Critical state | low heavy warning siren | WebAudio saw pulse |
| `public/assets/audio/sfx-door-lockdown.mp3` | opening door seal, ending door release variant | heavy pneumatic/clunk | WebAudio square thump |
| `public/assets/audio/sfx-notification-pop.mp3` | crew message stack 3 times | short UI pop | WebAudio sine ping |
| `public/assets/audio/sfx-comm-glitch.mp3` | network cut, Warning state | glitch/static burst | WebAudio square burst |
| `public/assets/audio/sfx-echo-ping.mp3` | ECHO message start | cold synthetic ping | WebAudio triangle ping |
| `public/assets/audio/sfx-power-surge.mp3` | wrong submission/power penalty | electrical surge, short | WebAudio saw burst |
| `public/assets/audio/sfx-success-chime.mp3` | Act success | controlled positive chime | WebAudio sine chime |
| `public/assets/audio/sfx-blackout-clunk.mp3` | power 0% blackout | heavy cutoff hit, followed by silence in logic | WebAudio low square |
| `public/assets/audio/sfx-reboot.mp3` | post-blackout recovery | boot/relay restart | WebAudio triangle chirp |

## Scene Trigger Map

| scene/trigger | expected assets |
| --- | --- |
| main menu standby | `control-room.glb`, `ambience-ship-hum.mp3` |
| click computer / approach | `control-room.glb`, monitor frame node, optional camera markers |
| opening 00:00~00:10 | `player-hands-typing.glb`, `sfx-keyboard-typing.mp3`, `ambience-ship-hum.mp3` |
| opening 00:10~00:20 | `sfx-warning-siren.mp3`, emergency light nodes |
| opening 00:20~00:30 | `sfx-door-lockdown.mp3`, `Door_Main`, `Door_Lock_Indicator` |
| opening 00:30~00:42 | `sfx-notification-pop.mp3`, `sfx-comm-glitch.mp3` |
| opening 00:42~00:52 | `sfx-echo-ping.mp3`, `sfx-keyboard-typing.mp3` |
| terminal focus handoff | `Monitor_Main`, `Monitor_Frame`, `sfx-reboot.mp3` or HUD ignition cue |
| wrong evidence | `sfx-power-surge.mp3`, glitch overlay |
| blackout | `sfx-blackout-clunk.mp3`, red vignette/glitch overlay |
| ending A | `Door_Main`, `sfx-door-lockdown.mp3`, `sfx-success-chime.mp3` |

## Naming Rules

- Use lowercase kebab-case filenames.
- Do not include spaces or Korean characters in final asset filenames.
- Keep source/design files outside `public/assets`; only runtime-ready assets should be dropped there.
- If multiple versions exist, suffix with role, not dates. Example: `control-room-low.glb`, `control-room-final.glb`.

## Human Delivery Checklist

- [ ] `control-room.glb` matches node names or includes a node map note.
- [ ] `player-hands-typing.glb` includes required clips or a note if baked as one timeline.
- [ ] Audio clips are normalized and not painfully loud.
- [ ] Looping ambience has no audible seam.
- [ ] Image/UI assets are readable at 1920x1080 and responsive down to laptop width.
- [ ] Any missing asset is intentionally deferred and placeholder fallback is acceptable.

