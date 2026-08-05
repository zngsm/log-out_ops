# feat-003 Implement oxygen and power game state

## Status

- status: done
- type: feat
- priority: 3
- owner agent: dev-agent
- branch: `feat-003-implement-oxygen-and-power-game-state`
- commit message: `feat-003 implement oxygen and power game state`

## Goal

Implement the MVP resource model for oxygen, power, wrong submissions, blackout, and loss state.

## Scope

- Track oxygen percentage.
- Track power percentage.
- Apply wrong answer penalty of power -15%.
- Apply power-based oxygen drain multiplier.
- Add blackout state when power reaches 0%.
- Restore temporary power after blackout according to the planning docs.
- Support normal 60-minute session configuration.
- Support debug 15-minute session configuration.

## Dependencies

- before: `feat-001`
- after: `feat-005`, `feat-007`, `qa-001`

## Acceptance Criteria

- [x] Resource state can be updated deterministically.
- [x] Power thresholds map to Normal, Caution, Warning, Critical, and Blackout.
- [x] Oxygen reaching 0% produces a losing state.
- [x] Normal mode drains oxygen from 100% to 0% over 60 minutes before multipliers.
- [x] Debug mode drains oxygen from 100% to 0% over 15 minutes before multipliers.
- [x] Blackout disables interaction for the configured blackout duration and restores power to 10%.

## Validation

- `npm run build`: pass
- Build output confirmed: `dist/index.html`, `dist/assets/index-DuEYgauW.css`, `dist/assets/index-Dy7o_4NI.js`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | oxygen and power state implementation started |
| 2026-08-05 | review-agent | review approved | no blocking findings; UI files intentionally untouched to avoid parallel branch conflicts |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for deterministic resource state model | closed |

## Deliverables

- code changes: `src/game/resourceState.ts`
- branch: `feat-003-implement-oxygen-and-power-game-state`
- commit: `16e7a2d`
- tests: `npm run build`

## PR Draft

- pr title: FEAT-003 산소/전력 게임 상태 모델 구현
- pr description:
  - `## Summary`
  - 산소, 전력, 오답 페널티, 전력 구간, 블랙아웃, normal/debug 세션 길이를 계산하는 deterministic resource state 모델을 추가함
  - `## Changes`
  - `src/game/resourceState.ts`: resource state 타입, power state 판정, 오답 페널티, 시간 경과, 블랙아웃 복구, 입력 잠금 계산 로직 추가
