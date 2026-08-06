# feat-012 Add DOCX-reference main menu and directed opening sequence

## Status

- status: done
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

- [x] Player understands they are Kim Wooju, trapped in Hermes control room by ECHO quarantine.
- [x] Main menu composition matches DOCX/GIF intent: visible control room, central monitor/desk, window/starfield or placeholder, and monitor/holographic title/buttons.
- [x] PLAY fades out the 2D menu layer, clears blur, and starts a camera move toward the monitor.
- [x] Opening includes door lock, crew interruption, ECHO network cutoff, and oxygen/session start.
- [x] Opening uses hands only during cutscene beats if the hands model or placeholder is available.
- [x] Normal path can play as a timed sequence; debug path can skip or accelerate it.
- [x] Terminal gameplay begins only after the opening handoff.
- [x] Missing final assets do not break the sequence.

## Implementation Notes

- Added explicit app phases: `menu`, `transition`, `opening`, and `gameplay`.
- Added DOCX-reference main menu with `LOGOUT ISOLATION`, `THE ECHO PROTOCOL`, PLAY/QUIT monitor controls, blur fade, and launch transition.
- Added `src/game/openingTimeline.ts` with the 00:00-01:00 opening beats: routine work, alarm, door lock, crew comms, ECHO lockdown, and terminal handoff.
- Reworked opening from manual cards to timed sequence with normal speed, debug fast-forward, and skip-to-terminal controls.
- Extended the R3F placeholder scene with phase-aware camera targets, door/window/starfield/side-console/desk props, red-alert lighting, and opening-only hand placeholders.
- Added CSS for menu monitor styling, opening timeline director cards, crew message stack, progress track, and cutscene hand placeholder.

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- review-agent result: approved

## Pull Request Draft

- PR title: `FEAT-012 DOCX 기준 메인 메뉴 및 오프닝 시퀀스 구현`
- branch: `feat-012-add-docx-reference-main-menu-and-directed-opening-sequence`
- code commit: `ac212d0 feat-012 add docx reference main menu and directed opening sequence`

## PR Description

```md
## Summary
DOCX/GIF reference 기준으로 메인 메뉴, PLAY 전환, 60초 오프닝 타임라인, 터미널 진입 흐름을 구현했습니다.

## Changes
src/App.tsx: 앱 phase를 menu/transition/opening/gameplay로 분리하고, 메인 메뉴와 timed opening sequence를 연결했습니다.
src/game/openingTimeline.ts: 00:00-01:00 오프닝 beat 데이터를 추가했습니다.
src/game/SpaceshipComputerScene.tsx: phase-aware 카메라, 문/창/별 배경/콘솔/책상/손 placeholder, red-alert 조명을 추가했습니다.
src/styles.css: DOCX-reference 메뉴 모니터, 홀로그램 버튼, 오프닝 진행/손/crew message 스타일을 추가했습니다.
```

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
| 2026-08-06 | dev-agent | todo -> in_progress | DOCX-reference main menu and directed opening sequence implementation started |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff validation passed; no blocking findings |
| 2026-08-06 | dev-agent | approved -> done | Code branch pushed and ops task updated |
