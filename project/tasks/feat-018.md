# feat-018 Add placeholder audio system and sound cues

## Status

- status: todo
- type: feat
- priority: 23
- owner agent: dev-agent
- branch: `feat-018-add-placeholder-audio-system-and-sound-cues`
- commit message: `feat-018 add placeholder audio system and sound cues`

## Goal

Add the minimum audio layer needed for the original LOG_OUT pressure fantasy to register.

## Scope

- Add audio manager with mute, volume, and user-gesture-safe playback.
- Add ambient ship hum loop.
- Add cues for warning siren, door lock, notification popup, ECHO ping, typing, wrong surge, success, blackout, and reboot.
- Add cues for PLAY transition, pneumatic decompression, communication glitch, and HUD ignition.
- Use WebAudio synthetic fallback if static files are missing.
- Respect accessibility by allowing mute and avoiding painful looping sounds.

## Dependencies

- before: `feat-012`, `feat-014`, `feat-015`
- after: `feat-020`, `qa-002`

## Acceptance Criteria

- [ ] Audio starts only after user interaction and can be muted.
- [ ] Correct and wrong evidence submissions have distinct audio feedback.
- [ ] Opening and blackout are audibly different from normal gameplay.
- [ ] Opening has distinct audio beats for PLAY, alarm, decompression, door lock, crew notifications, communication cutoff, ECHO typing/ping, and HUD activation.
- [ ] Missing audio files fall back gracefully.
- [ ] QA can verify triggers without external services.

## Source References

- `project/human-input/LOG_OUT visual 기획서.md`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/phase_2_original_source_replan.md`
- `project/docx_source_reassessment.md`

## Asset Inputs

- `public/assets/audio/amb_ship_hum_loop.ogg`
- `public/assets/audio/sfx_play_start.ogg`
- `public/assets/audio/sfx_warning_siren.ogg`
- `public/assets/audio/sfx_decompression.ogg`
- `public/assets/audio/sfx_door_lock_clunk.ogg`
- `public/assets/audio/sfx_notification_popup.ogg`
- `public/assets/audio/sfx_comm_glitch.ogg`
- `public/assets/audio/sfx_echo_ping.ogg`
- `public/assets/audio/sfx_typing_loop.ogg`
- `public/assets/audio/sfx_hud_ignition.ogg`
- `public/assets/audio/sfx_wrong_surge.ogg`
- `public/assets/audio/sfx_success_chime.ogg`
- `public/assets/audio/sfx_blackout_clunk.ogg`
- `public/assets/audio/sfx_reboot.ogg`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
