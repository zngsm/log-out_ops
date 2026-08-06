# feat-014 Implement ECHO decision matrix and persona responses

## Status

- status: done
- type: feat
- priority: 18
- owner agent: dev-agent
- branch: `main`
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

- [x] Act 1 partial success can ask for explanation without power penalty.
- [x] Old evidence resubmission does not penalize the player and points back to the current claim.
- [x] Three failed attempts trigger a reverse-hint style ECHO response.
- [x] ECHO responses use formal, cold, rule-bound tone.
- [x] Response output can later be replaced or enriched by external AI.

## Implementation Notes

- Added `src/game/echoResponseMatrix.ts` as the deterministic ECHO response schema for success, partial, incorrect, old evidence, repeat hint, security threat, and emotional claim branches.
- Reworked `src/game/evidenceSubmission.ts` to return clean response metadata: `decisionKind`, `stabilityChange`, `suspicionChange`, and `countsAsFailedAttempt`.
- Added Act 1 and Act 2 synonym-group intent checks from the original ECHO prompt direction.
- Preserved Category A Act 3 behavior so `ai_priority_matrix.json` + `deleted_override.txt` succeeds regardless of explanation wording.
- Added Act 1 partial-intent handling without power penalty, old-evidence handling without power penalty, and 3-failed-attempt reverse hints.
- Added ECHO stability/suspicion HUD state and failed-attempt tracking in `src/App.tsx`.
- Added `echo-state-card` styling in `src/styles.css`.

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- review-agent result: approved

## Delivery

- workflow: latest `main` -> task commit -> push `main`
- code commit: `c91fdf9 feat-014 implement echo decision matrix and persona responses`

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT AI 프롬포트 예시.md`
- `project/phase_2_original_source_replan.md`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-06 | dev-agent | todo -> in_progress | ECHO decision matrix and persona response implementation started from latest main |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff validation passed; no blocking findings |
| 2026-08-06 | dev-agent | approved -> done | Code committed and pushed directly to main |
