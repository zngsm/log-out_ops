# feat-012 Add DOCX-reference main menu and directed opening sequence

## Status

- status: todo
- type: feat
- priority: 16
- owner agent: dev-agent
- branch: `feat-012-add-docx-reference-main-menu-and-directed-opening-sequence`
- commit message: `feat-012 add docx reference main menu and directed opening sequence`

## Goal

Recreate the original LOG_OUT entry experience from the DOCX visual references: a control-room computer menu, then a directed opening sequence that explains why the player is trapped before handing control to the terminal.

## Scope

- Add main menu state with `LOGOUT` branding, `PLAY`, and `QUIT`.
- Support DOCX title treatment: `LOGOUT ISOLATION` and `THE ECHO PROTOCOL` may appear as subtitle/lockdown branding, while the project title remains LOG_OUT.
- Present PLAY/QUIT as monitor or holographic UI controls over the central computer, not as generic webpage buttons.
- Apply menu background blur near 8px and remove it during PLAY transition.
- On `PLAY`, transition from diagonal 3D control-room view to monitor focus.
- Implement an opening timeline with beats for peaceful work, alarm, door lock, crew messages, ECHO interruption, and terminal handoff.
- Include D-002/D-003 style ECHO lockdown messages from the original plan.
- Show crew message popups before ECHO cuts network communication.
- Support debug skip without removing the normal sequence path.
- Use placeholder visuals/audio if final assets are missing.

## Dependencies

- before: `feat-008`, `feat-009`, `feat-010`
- after: `feat-013`, `feat-018`, `feat-019`

## Acceptance Criteria

- [ ] Player understands they are Kim Wooju, trapped in Hermes control room by ECHO quarantine.
- [ ] Main menu composition matches DOCX/GIF intent: visible control room, central monitor/desk, window/starfield or placeholder, and monitor/holographic title/buttons.
- [ ] PLAY fades out the 2D menu layer, clears blur, and starts a camera move toward the monitor.
- [ ] Opening includes door lock, crew interruption, ECHO network cutoff, and oxygen/session start.
- [ ] Opening uses hands only during cutscene beats if the hands model or placeholder is available.
- [ ] Normal path can play as a timed sequence; debug path can skip or accelerate it.
- [ ] Terminal gameplay begins only after the opening handoff.
- [ ] Missing final assets do not break the sequence.

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT visual 기획서.md`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/phase_2_original_source_replan.md`
- `project/docx_source_reassessment.md`

## Asset Inputs

- `public/assets/models/control-room.glb`
- `public/assets/models/player-hands-typing.glb`
- `public/assets/images/space/space-panorama.webp`
- `public/assets/images/ui/logout-title.svg`
- `public/assets/audio/amb_ship_hum_loop.ogg`
- `public/assets/audio/sfx_play_start.ogg`
- `public/assets/audio/sfx_warning_siren.ogg`
- `public/assets/audio/sfx_decompression.ogg`
- `public/assets/audio/sfx_door_lock_clunk.ogg`
- `public/assets/audio/sfx_notification_popup.ogg`
- `public/assets/audio/sfx_comm_glitch.ogg`
- `public/assets/audio/sfx_echo_ping.ogg`
- `public/assets/audio/sfx_hud_ignition.ogg`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
