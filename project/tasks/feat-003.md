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
- Support normal 60-minute session configuration.
- Support debug 15-minute session configuration.

## Dependencies

- before: `feat-001`
- after: `feat-005`, `feat-007`, `qa-001`

## Acceptance Criteria

- Resource state can be updated deterministically.
- Power thresholds map to Normal, Caution, Warning, Critical, and Blackout.
- Oxygen reaching 0% produces a losing state.
- Normal mode drains oxygen from 100% to 0% over 60 minutes before multipliers.
- Debug mode drains oxygen from 100% to 0% over 15 minutes before multipliers.
- Blackout disables interaction for the configured blackout duration and restores power to 10%.
