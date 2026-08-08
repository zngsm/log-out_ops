# feat-022 Implement DOCX-based ECHO argument flow

## Status

- status: todo
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

- [ ] ECHO opens each Act with a specific claim the player must disprove.
- [ ] Correct evidence with missing explanation produces partial success without power penalty where applicable.
- [ ] Wrong evidence/text causes power penalty and a procedural warning.
- [ ] Old evidence resubmission is rejected without punishing the player.
- [ ] Prompt-injection style input is treated as tampering and increases suspicion.
- [ ] Repeated failures produce source-appropriate hints.
- [ ] ECHO tone remains calm, formal, non-emotional, and non-villainous.
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Source References

- `project/human-input/우주선 탈출 게임 AI 프롬프트 예시.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/docx_content_conversion_plan.md`

