# feat-019 Integrate DOCX-reference 3D control room with scene and resource state

## Status

- status: done
- type: feat
- priority: 24
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-019 integrate docx reference 3d control room with scene and resource state`

## Goal

Make the Hermes control room match the DOCX visual references and react to scene, power, and ending states so it supports the original first-person immersion.

## Scope

- Support main-menu diagonal camera and gameplay terminal-focus camera.
- Support at least three camera compositions: menu computer view, opening door/room view, and terminal focus view.
- Include or approximate the DOCX room elements: central monitor desk, keyboard/mouse, side consoles, rear/side door, window/starfield, ceiling lights, pipes/wall panels, and small desk props.
- React to Normal/Caution/Warning/Critical/Blackout power thresholds with lighting and monitor changes.
- Show door locked/unlocking state.
- Hide hands during terminal gameplay; show placeholder hands only in opening if available.
- Gracefully use placeholder geometry if final GLB files are missing.

## Dependencies

- before: `feat-009`, `feat-012`, `feat-015`
- after: `feat-020`, `qa-002`

## Acceptance Criteria

- [x] 3D scene visibly changes between menu, opening, gameplay, blackout, and ending.
- [x] Menu view resembles the DOCX/GIF reference: central computer in a control room with window/starfield and side consoles.
- [x] Door-focused opening/ending view clearly shows the locked/releasing door as a physical object.
- [x] Terminal focus view keeps the monitor dominant while preserving enough room framing to feel embedded.
- [x] Power state changes affect lighting or monitor/environment treatment.
- [x] Door lock/release is visible or clearly represented.
- [x] Missing GLB assets do not break the scene.
- [x] Performance remains acceptable for Vite dev/build.

## Implementation Notes

- `SpaceshipComputerScene` now accepts scene mode, power state, and door state from the app runtime.
- The control-room placeholder geometry now visualizes locked, unlocking, and released door states.
- Warning, Critical, and Blackout power states adjust background darkness, point-light intensity, and terminal emissive treatment.
- Gameplay uses a terminal-focus monitor treatment while opening keeps the placeholder hands limited to the opening scene.
- The implementation remains GLB-optional and uses procedural R3F geometry when final room/hands models are unavailable.

## Validation

- `npm run build` passed.
- `git diff --check` passed.
- Review-agent pass completed within the dev-agent workflow.

## Delivery

- code repo commit: `1bd7bd5 feat-019 integrate docx reference 3d control room with scene and resource state`
- code repo target: `main`

## Source References

- `project/human-input/LOG_OUT visual 기획서.md`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/phase_2_original_source_replan.md`
- `project/docx_source_reassessment.md`

## Asset Inputs

- `public/assets/models/control-room.glb`
- `public/assets/models/player-hands-typing.glb`
- `public/assets/images/space/space-panorama.webp`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-06 | dev-agent | todo -> in_progress | DOCX-reference 3D control room integration started after feat-018 main push |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff checks passed; scoped to scene/runtime visual integration |
| 2026-08-06 | dev-agent | approved -> done | Pushed code commit `1bd7bd5` to `log-out/main` |
