# feat-013 Add scene runtime and Act beat orchestration

## Status

- status: todo
- type: feat
- priority: 17
- owner agent: dev-agent
- branch: `feat-013-add-scene-runtime-and-act-beat-orchestration`
- commit message: `feat-013 add scene runtime and act beat orchestration`

## Goal

Turn the current Act changes into explicit scene beats so the game unfolds like the original scripted experience rather than a generic UI state machine.

## Scope

- Add scene ids for opening, Act 1, Act 2, Act 3, ECHO review, Ending A, failure, and blackout/reboot.
- Define scene entry lines, exit conditions, interaction lock windows, and transition timing.
- Add ECHO response delay/typing phases before outcome is revealed.
- Add the 5-second final review mode before final door unlock.
- Keep the canonical Category A Act 3 evidence as `ai_priority_matrix.json` + `deleted_override.txt`.

## Dependencies

- before: `feat-005`, `feat-010`, `feat-012`
- after: `feat-014`, `feat-020`, `qa-002`

## Acceptance Criteria

- [ ] Each Act has an entry beat and success transition beat.
- [ ] Player input is locked during ECHO processing and final review.
- [ ] Scene state is inspectable enough for QA to verify sequence order.
- [ ] Existing deterministic evidence progression still works.
- [ ] Scene implementation does not require external AI.

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT visual 기획서.md`
- `project/phase_2_original_source_replan.md`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
