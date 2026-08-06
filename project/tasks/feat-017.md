# feat-017 Rework Log_Fixer into mini-program flow

## Status

- status: todo
- type: feat
- priority: 21
- owner agent: dev-agent
- branch: `feat-017-rework-log-fixer-into-mini-program-flow`
- commit message: `feat-017 rework log fixer into mini program flow`

## Goal

Turn Log_Fixer from a simplified recovery action into the original mini-program interaction.

## Scope

- Open `Log_Fixer.exe` as a CUI-style popup.
- Let the player choose or enter the corrupted file path.
- Require repair mode selection from the manual: `Header Repair`, `Offset Correction`, or `Text Reconstruction`.
- Show progress, byte-scroll style feedback, and restored-line highlight.
- Handle wrong file or wrong repair mode with non-softlocking feedback.
- Respect resource-pressure modifiers, including Warning slowdown.

## Dependencies

- before: `feat-006`, `feat-016`
- after: `qa-002`

## Acceptance Criteria

- [ ] Recovery requires a meaningful player action using manual information.
- [ ] Correct recovery makes `quarantine_rules.conf` usable for Act 2.
- [ ] Wrong recovery attempts are understandable and recoverable.
- [ ] The mini-program can be operated with mouse/keyboard in the current UI.
- [ ] The flow remains deterministic for QA.

## Source References

- `project/human-input/LOG_OUT 로그파일 구조.md`
- `project/human-input/LOG_OUT 로그 예시.md`
- `project/phase_2_original_source_replan.md`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
