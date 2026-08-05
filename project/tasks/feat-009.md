# feat-009 Build R3F spaceship computer scene

## Status

- status: done
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

- [x] The app renders a 3D spaceship/computer scene behind or around the Hermes OS.
- [x] The Hermes OS remains readable and usable.
- [x] Final GLB assets are not required.
- [x] The implementation leaves a clean path for later replacing placeholders with real models.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | R3F spaceship computer scene implementation started |
| 2026-08-05 | review-agent | review approved | no blocking findings; R3F/three bundle size warning noted as follow-up optimization risk |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |
| 2026-08-05 | dev-agent | conflict resolved | merged latest main after feat-004, preserved Hermes OS shell, and integrated R3F scene as background layer |

## Validation

- `npm run build`: pass
- Build output confirmed: `dist/index.html`, `dist/assets/index-2-UtdFsp.css`, `dist/assets/index-B9dqfCgS.js`
- `npm run build`: pass after main merge conflict resolution
- Build output confirmed after merge resolution: `dist/index.html`, `dist/assets/index-C2oKmYKz.css`, `dist/assets/index-D52-tGXC.js`
- Non-blocking warning: Vite reported a chunk larger than 500 kB after adding R3F/three.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for placeholder R3F scene scope | closed |
| 2 | review-agent | approve | merge conflict resolved; latest Hermes OS shell is preserved with R3F backdrop; build passed with known chunk warning | closed |

## Deliverables

- code changes: `package.json`, `package-lock.json`, `src/App.tsx`, `src/styles.css`, `src/game/SpaceshipComputerScene.tsx`
- branch: `feat-009-build-r3f-spaceship-computer-scene`
- commit: `4c5c255`
- conflict resolution commit: `55e0a5b`
- tests: `npm run build`

## PR Draft

- pr title: FEAT-009 R3F 우주선 컴퓨터 씬 구현
- pr description:
  - `## Summary`
  - React Three Fiber 기반 우주선 통제실과 컴퓨터 placeholder scene을 추가하고, 최신 main의 Hermes OS shell과 충돌을 해결해 3D scene이 UI 뒤 배경 레이어로 렌더링되도록 통합함
  - `## Changes`
  - `package.json`, `package-lock.json`: `three`, `@react-three/fiber` 의존성 추가
  - `src/game/SpaceshipComputerScene.tsx`: control room shell, computer frame, console deck placeholder R3F scene 추가
  - `src/App.tsx`: 최신 Hermes OS shell을 유지하면서 R3F scene을 background layer로 렌더링하도록 통합
  - `src/styles.css`: scene backdrop layer, canvas sizing, Hermes OS shell layering/responsive style 조정
