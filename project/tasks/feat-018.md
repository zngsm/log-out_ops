# feat-018 Add placeholder audio system and sound cues

## Status

- status: done
- type: feat
- priority: 23
- owner agent: dev-agent
- branch: `main`
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

- [x] Audio starts only after user interaction and can be muted.
- [x] Correct and wrong evidence submissions have distinct audio feedback.
- [x] Opening and blackout are audibly different from normal gameplay.
- [x] Opening has distinct audio beats for PLAY, alarm, decompression, door lock, crew notifications, communication cutoff, ECHO typing/ping, and HUD activation.
- [x] Missing audio files fall back gracefully.
- [x] QA can verify triggers without external services.

## Implementation Notes

- Added `src/game/audioSystem.ts` with user-gesture-safe WebAudio synthetic fallback cues.
- Added mute, volume, and enable controls to the HUD.
- Wired cue triggers for PLAY, opening alarm/decompression/door lock/crew popup/comm glitch/ECHO typing/HUD ignition.
- Wired distinct success, wrong surge, blackout, and ending-door cues.
- No external services or static audio assets are required for QA verification.

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- review-agent result: approved

## Delivery

- workflow: latest `main` -> task commit -> push `main`
- code commit: `f30caed feat-018 add placeholder audio system and sound cues`

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
| 2026-08-06 | dev-agent | todo -> in_progress | Placeholder audio system and sound cue implementation started after feat-017 main push |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff validation passed; no blocking findings |
| 2026-08-06 | dev-agent | approved -> done | Code committed and pushed directly to main |
