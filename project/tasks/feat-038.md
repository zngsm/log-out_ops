# feat-038 Remove start button shimmer animation, brighten 3d scene lights, remove start click broadcast flash, double explorer panel width to 360px, empty echo input and set korean placeholder

## Status

- status: done
- type: feat
- priority: 55
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-038 remove start button shimmer animation, brighten 3d scene lights, remove start click broadcast flash, double explorer panel width to 360px, empty echo input and set korean placeholder`

## Goal

Apply 5 UI/UX and 3D scene refinements:
1. `src/styles.css`: Remove START button (`.computer-hotspot`) animation/shimmer effect, fixed to static cyan glow theme.
2. `src/game/SpaceshipComputerScene.tsx`: Increase 3D backdrop brightness by setting `ambientLight` intensity to `1.8` and `pointLight` intensity to `16.0`.
3. `src/App.tsx`: Completely remove `<div className="lockdown-broadcast">` text block during START click transition phase (`appPhase === "transition"`).
4. `src/styles.css`: Expand `.explorer-panel` width from 190px to 360px (`flex: 0 0 360px; width: 360px;`) for improved file list readability.
5. `src/App.tsx`: Remove default prompt generator (`getDefaultPrompt(...)`) and initialize `messageInput` to empty string `""` on start and stage change, and add `placeholder="ECHO에게 제출할 증거를 입력하세요..."` to the ECHO textarea.

## Scope

- **Remove Button Shimmer**: Remove `@keyframes computer-hotspot-pulse` and `animation` property on `.computer-hotspot::before` for static cyan glow.
- **Brighten 3D Lights**: Set default `ambientLight` intensity to `1.8` and main `pointLight` intensity to `16.0`.
- **Remove Broadcast Flash**: Remove `<div className="lockdown-broadcast">` text block when `appPhase === "transition"`.
- **Double Explorer Panel Width**: Update `.explorer-panel` CSS rule to `flex: 0 0 360px; width: 360px;`.
- **Empty ECHO Input & Korean Placeholder**: Remove `getDefaultPrompt`, initialize `messageInput` to `""`, and set textarea placeholder to `"ECHO에게 제출할 증거를 입력하세요..."`.

## Acceptance Criteria

- [x] `.computer-hotspot` pulse/shimmer animation is completely removed, maintaining a static cyan glow theme.
- [x] `ambientLight` intensity set to `1.8` and `pointLight` intensity set to `16.0` in `SpaceshipComputerScene.tsx`.
- [x] `<div className="lockdown-broadcast">` text block is removed during transition phase.
- [x] `.explorer-panel` flex and width updated to `360px`.
- [x] `getDefaultPrompt` removed, `messageInput` initialized to `""`, and textarea placeholder updated to `"ECHO에게 제출할 증거를 입력하세요..."`.
- [x] `npm run build` passes cleanly.
- [x] `git diff --check` passes cleanly.

## Review History

- 2026-08-10: Created feat-038 specification and verified implementation. Review agent approved.
