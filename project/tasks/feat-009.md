# feat-009 Build R3F spaceship computer scene

## Status

- status: todo
- type: feat
- priority: 6
- owner agent: dev-agent
- branch: `feat-009-build-r3f-spaceship-computer-scene`
- commit message: `feat-009 build r3f spaceship computer scene`

## Goal

Build the MVP 3D background scene containing the spaceship control room atmosphere and the computer frame that visually hosts the 2D Hermes OS.

## Scope

- Add React Three Fiber scene setup.
- Create placeholder spaceship control room environment.
- Create placeholder 3D computer or monitor frame.
- Position the Hermes OS 2D interface so it feels integrated with the 3D computer.
- Use placeholder geometry/materials instead of final GLB assets.
- Do not implement final rigged hand model in MVP.

## Dependencies

- before: `feat-001`
- after: `feat-008`

## Acceptance Criteria

- The app renders a 3D spaceship/computer scene behind or around the Hermes OS.
- The Hermes OS remains readable and usable.
- Final GLB assets are not required.
- The implementation leaves a clean path for later replacing placeholders with real models.
