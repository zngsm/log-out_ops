# feat-037 Implement meter bars for oxygen power, brighten 3d lights, set start button and intranet monitor theme, remove stability suspicion meta texts

## Status

- status: done
- type: feat
- priority: 54
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-037 implement meter bars for oxygen power, brighten 3d lights, set start button and intranet monitor theme, remove stability suspicion meta texts`

## Goal

Apply 6 UI/UX and 3D scene refinements:
1. `src/App.tsx`: Add real-time draining progress bar gauges (`.hud-bar-track` / `.hud-bar-fill`) to `O₂ LEVEL` and `POWER GRID` inside `header-center-hud`.
2. `src/App.tsx`: Remove all start screen guidance copy (`평시 당직 모니터가 대기 중입니다`, `헤르메스호 통제실은 아직 정상 조명 상태입니다...`).
3. `src/App.tsx`: Re-align `THE ECHO PROTOCOL LOG_OUT` title logo to top-center of the start screen.
4. `src/App.tsx` & `src/styles.css`: Change main start button text to `START` and match color theme with Intranet login teal/cyan glow.
5. `src/App.tsx`: Remove `[stability ... / suspicion ...]` suffix text from ECHO response output (pure dialogue only).
6. `src/game/SpaceshipComputerScene.tsx`: Increase `ambientLight` and `pointLight` intensities for brighter 3D control room background, and set 3D monitor emissive color from orange (`#e98d42`) to Intranet theme (`#0f4b46`).

## Scope

- **Meter Bar Gauges**: Render `.hud-bar-track` and `.hud-bar-fill` in `header-center-hud` dynamically bound to `resourceState.oxygen` and `resourceState.power`.
- **Start Screen Clean-up**: Remove standby broadcast copy from initial start overlay.
- **Top-Center Title Logo**: Center-align title logo at top with cyan/teal text-shadow.
- **Intranet START Button**: Styled with teal/cyan glow, hover state, and `START` label.
- **ECHO Clean Output**: Output pure dialogue string without appending stability/suspicion stats.
- **3D Backdrop Brightness & Intranet Theme**: Increase light intensities, change menu emissive to `#0f4b46`.

## Acceptance Criteria

- [x] O₂ LEVEL and POWER GRID present `.hud-bar-track` and `.hud-bar-fill` gauge meters.
- [x] Initial menu screen guidance text is completely removed.
- [x] Title logo is center-aligned at the top of the start screen.
- [x] Main start button text is `START` with cyan/teal intranet theme styling.
- [x] ECHO response dialogue omits `[stability ... / suspicion ...]` text.
- [x] 3D control room background lights are brightened and monitor emissive is `#0f4b46`.
- [x] `npm run build` passes cleanly.
- [x] `git diff --check` passes cleanly.

## Review History

- 2026-08-10: Created feat-037 specification and verified implementation. Review agent approved.
