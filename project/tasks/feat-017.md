# feat-017 Rework Log_Fixer into mini-program flow

## Status

- status: done
- type: feat
- priority: 21
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-017 rework log fixer into mini program flow`

## Goal

Turn Log_Fixer from a simplified recovery action into the original mini-program interaction.

## Scope

- Open `Log_Fixer.exe` as a CUI-style popup when clicking `[OPEN WITH LOG_FIXER]` inside file viewer (Q36).
- Completely remove the left sidebar `Log fixer mini program` card/form (Q36).
- Let the player choose or enter the corrupted file path.
- Require repair mode selection from the manual: `Header Repair`, `Offset Correction`, or `Text Reconstruction`.
- Show progress, byte-scroll style feedback, and restored-line highlight.
- Enforce that corrupted/deleted file contents are concealed before recovery (Q39).
- Completely remove developer meta text like `Available for act-2 evidence` upon recovery completion (Q42).
- Handle wrong file or wrong repair mode with non-softlocking feedback.
- Respect resource-pressure modifiers, including Warning slowdown.

## Dependencies

- before: `feat-006`, `feat-016`
- after: `qa-002`

## Acceptance Criteria

- [x] Recovery requires a meaningful player action using manual information initiated via file viewer `[OPEN WITH LOG_FIXER]` button.
- [x] Left sidebar `Log fixer mini program` card/form is completely removed (Q36).
- [x] Corrupted/deleted file contents are concealed before Log_Fixer recovery (Q39).
- [x] Developer meta text like `Available for act-2 evidence` upon completion is completely removed (Q42).
- [x] Correct recovery makes `quarantine_rules.conf` usable for Act 2.
- [x] Wrong recovery attempts are understandable and recoverable.
- [x] The mini-program can be operated with mouse/keyboard in the current UI.
- [x] The flow remains deterministic for QA.

## Implementation Notes

- Replaced direct `RUN LOG_FIXER` recovery with a CUI-style Log_Fixer popup.
- Added target path input, repair mode radio choices, deterministic progress, byte-scroll feedback, and restored-line highlight.
- Correct path `/System/Security/quarantine_rules.conf` plus `Text Reconstruction` mode recovers and attaches the file.
- Wrong path or wrong mode produces recoverable CUI errors without softlock.
- Existing resource-pressure slowdown is respected through recovery delay.

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- review-agent result: approved

## Delivery

- workflow: latest `main` -> task commit -> push `main`
- code commit: `dfacbe0 feat-017 rework log fixer into mini program flow`

## Source References

- `project/human-input/LOG_OUT 로그파일 구조.md`
- `project/human-input/LOG_OUT 로그 예시.md`
- `project/phase_2_original_source_replan.md`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-06 | dev-agent | todo -> in_progress | Log_Fixer mini-program flow started after chore-003 main push |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff validation passed; no blocking findings |
| 2026-08-06 | dev-agent | approved -> done | Code committed and pushed directly to main |
