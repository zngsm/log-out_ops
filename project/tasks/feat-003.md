# feat-003 Implement oxygen and power game state

## Status

- status: todo
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

## Dependencies

- before: `feat-001`
- after: `feat-005`, `feat-007`, `qa-001`

## Acceptance Criteria

- Resource state can be updated deterministically.
- Power thresholds map to Normal, Caution, Warning, Critical, and Blackout.
- Oxygen reaching 0% produces a losing state.
- Timer implementation is configurable enough for QA without changing game rules.
