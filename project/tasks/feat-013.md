# feat-013 Add scene runtime and Act beat orchestration

## Status

- status: done
- type: feat
- priority: 17
- owner agent: dev-agent
- branch: `main`
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

- [x] Each Act has an entry beat and success transition beat.
- [x] Player input is locked during ECHO processing and final review.
- [x] Scene state is inspectable enough for QA to verify sequence order.
- [x] Existing deterministic evidence progression still works.
- [x] Scene implementation does not require external AI.

## Implementation Notes

- Added `src/game/sceneRuntime.ts` with explicit scene ids for menu, opening, Act 1/2/3 entry, ECHO review, Act success transitions, final review, Ending A, oxygen failure, and blackout/reboot.
- Added scene runtime state to `src/App.tsx` so current scene id, phase, line, exit condition, and input lock state are visible in the HUD and ECHO panel for QA.
- Changed evidence submission from immediate result reveal to `ECHO_REVIEW` delay, then success/failure scene transition.
- Added 5-second `SCENE_004_END_A_REVIEW` before setting `ending-ready` and showing the Ending A overlay.
- Kept Category A Act 3 evidence flow unchanged as `ai_priority_matrix.json` + `deleted_override.txt`.
- Added scene-lock feedback styling in `src/styles.css` so blackout lock and ECHO/scene lock are visually distinguishable. (Note: SCENE LOCK feedback popup is completely deleted in feat-042 / Q65).

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- review-agent result: approved

## Delivery

- workflow: latest `main` -> task commit -> push `main`
- code commit: `83391f4 feat-013 add scene runtime and act beat orchestration`

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT visual 기획서.md`
- `project/phase_2_original_source_replan.md`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-06 | dev-agent | todo -> in_progress | Scene runtime and Act beat orchestration started from latest main |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff validation passed; no blocking findings |
| 2026-08-06 | dev-agent | approved -> done | Code committed and pushed directly to main under updated workflow |
