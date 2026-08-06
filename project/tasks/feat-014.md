# feat-014 Implement ECHO decision matrix and persona responses

## Status

- status: todo
- type: feat
- priority: 18
- owner agent: dev-agent
- branch: `feat-014-implement-echo-decision-matrix-and-persona-responses`
- commit message: `feat-014 implement echo decision matrix and persona responses`

## Goal

Make deterministic ECHO feel like the original cold procedural AI by implementing staged response rules, partial success, redundant evidence, wrong evidence, and repeat-failure hints.

## Scope

- Implement success, partial success, incorrect, old evidence, and repeated wrong-attempt response branches.
- Use Act 1 and Act 2 synonym groups from the original plan for text intent checks.
- Act 3 succeeds when both canonical evidence files are attached, regardless of explanation wording.
- Add ECHO stability/suspicion changes or placeholders visible in the UI.
- Preserve future compatibility with external AI by keeping a clean response schema.

## Dependencies

- before: `feat-005`, `feat-013`
- after: `feat-018`, `feat-020`, `qa-002`

## Acceptance Criteria

- [ ] Act 1 partial success can ask for explanation without power penalty.
- [ ] Old evidence resubmission does not penalize the player and points back to the current claim.
- [ ] Three failed attempts trigger a reverse-hint style ECHO response.
- [ ] ECHO responses use formal, cold, rule-bound tone.
- [ ] Response output can later be replaced or enriched by external AI.

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT AI 프롬포트 예시.md`
- `project/phase_2_original_source_replan.md`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
