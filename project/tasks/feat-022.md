# feat-022 Implement DOCX-based ECHO argument flow

## Status

- status: done
- type: feat
- priority: 35
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-022 implement docx based echo argument flow`

## Goal

Make ECHO feel like a cold procedural AI opponent that defends each lockdown reason before it is logically defeated.

## Scope

- Use `우주선 탈출 게임 AI 프롬프트 예시.docx` and `우주선 탈출게임 개요.docx`.
- Add explicit ECHO default stance per Act.
- Add success, partial success, incorrect, redundant/old evidence, emotional demand, and prompt-injection/tampering responses.
- Add repeated-failure reverse hints after 3 failed attempts in the same Act.
- Preserve deterministic local rules for now; external AI remains deferred to `feat-007`.
- Ensure Act 3 includes the 5-second diagnostic/review framing from the DOCX.

## Dependencies

- before: `feat-021`
- after: `feat-023`, `qa-003`, optional `feat-007`

## Acceptance Criteria

- [x] ECHO opens each Act with a specific claim the player must disprove.
- [x] Correct evidence with missing explanation produces partial success without power penalty where applicable.
- [x] Wrong evidence/text causes power penalty and a procedural warning.
- [x] Old evidence resubmission is rejected without punishing the player.
- [x] Prompt-injection style input is treated as tampering and increases suspicion.
- [x] Repeated failures produce source-appropriate hints.
- [x] ECHO tone remains calm, formal, non-emotional, and non-villainous.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Implementation Notes

- Added Act-level default ECHO claims from the DOCX logic structure.
- Gameplay entry now posts the Act 1 claim instead of only static tutorial text.
- Act transitions now post the next Act's procedural defense line after the success beat.
- Reworded success, partial, incorrect, and repeated-failure lines toward the cold regulation style from the DOCX.
- Kept the implementation deterministic; external AI/API remains deferred to `feat-007`.

## Validation

- `npm run build` passed.
- `git diff --check` passed.

## Delivery

- code repo commit: `feat-022 implement docx based echo argument flow`
- code repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-08 | dev-agent | todo -> in_progress | Started scripted ECHO argument-flow implementation after feat-021 |
| 2026-08-08 | dev-agent | in_progress -> done | Added DOCX-based Act claims and procedural response copy |

## Source References

- `project/human-input/우주선 탈출 게임 AI 프롬프트 예시.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/docx_content_conversion_plan.md`
