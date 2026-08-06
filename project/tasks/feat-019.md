# feat-019 Integrate 3D control room with scene and resource state

## Status

- status: todo
- type: feat
- priority: 24
- owner agent: dev-agent
- branch: `feat-019-integrate-3d-control-room-with-scene-and-resource-state`
- commit message: `feat-019 integrate 3d control room with scene and resource state`

## Goal

Make the Hermes control room react to scene, power, and ending states so it supports the original first-person immersion.

## Scope

- Support main-menu diagonal camera and gameplay terminal-focus camera.
- React to Normal/Caution/Warning/Critical/Blackout power thresholds with lighting and monitor changes.
- Show door locked/unlocking state.
- Hide hands during terminal gameplay; show placeholder hands only in opening if available.
- Gracefully use placeholder geometry if final GLB files are missing.

## Dependencies

- before: `feat-009`, `feat-012`, `feat-015`
- after: `feat-020`, `qa-002`

## Acceptance Criteria

- [ ] 3D scene visibly changes between menu, opening, gameplay, blackout, and ending.
- [ ] Power state changes affect lighting or monitor/environment treatment.
- [ ] Door lock/release is visible or clearly represented.
- [ ] Missing GLB assets do not break the scene.
- [ ] Performance remains acceptable for Vite dev/build.

## Source References

- `project/human-input/LOG_OUT visual 기획서.md`
- `project/phase_2_original_source_replan.md`

## Asset Inputs

- `public/assets/models/control-room.glb`
- `public/assets/models/player-hands-typing.glb`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
