# feat-012 Add main menu and directed opening sequence

## Status

- status: todo
- type: feat
- priority: 16
- owner agent: dev-agent
- branch: `feat-012-add-main-menu-and-directed-opening-sequence`
- commit message: `feat-012 add main menu and directed opening sequence`

## Goal

Recreate the original LOG_OUT entry experience: main menu over the Hermes control room, then a directed opening sequence that explains why the player is trapped before handing control to the terminal.

## Scope

- Add main menu state with `LOGOUT`, `PLAY`, and `QUIT`.
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
- [ ] Opening includes door lock, crew interruption, ECHO network cutoff, and oxygen/session start.
- [ ] Normal path can play as a timed sequence; debug path can skip or accelerate it.
- [ ] Terminal gameplay begins only after the opening handoff.
- [ ] Missing final assets do not break the sequence.

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT visual 기획서.md`
- `project/phase_2_original_source_replan.md`

## Asset Inputs

- `public/assets/models/control-room.glb`
- `public/assets/models/player-hands-typing.glb`
- `public/assets/audio/amb_ship_hum_loop.ogg`
- `public/assets/audio/sfx_warning_siren.ogg`
- `public/assets/audio/sfx_door_lock_clunk.ogg`
- `public/assets/audio/sfx_notification_popup.ogg`
- `public/assets/audio/sfx_echo_ping.ogg`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
