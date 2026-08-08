# feat-023 Add DOCX resource pressure feedback as gameplay feel

## Status

- status: done
- type: feat
- priority: 36
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-023 add docx resource pressure feedback as gameplay feel`

## Goal

Turn oxygen and power from visible numbers into felt game pressure.

## Scope

- Implement DOCX threshold behavior for Normal, Caution, Warning, Critical, and Blackout.
- Show O2 drain multiplier clearly.
- Add file/viewer lag in Caution.
- Double Log_Fixer execution time in Warning.
- Add stronger glitch/vignette/cursor instability in Warning/Critical.
- Add wrong-submission surge moment.
- Add blackout/reboot sequence: 10 seconds of lock/silence style feedback, then temporary 10% power recovery.
- Preserve current deterministic timer model.

## Dependencies

- before: `feat-021`, `feat-022`
- after: `qa-003`

## Acceptance Criteria

- [x] Power thresholds visibly change room/terminal state.
- [x] O2 drain multiplier is readable and updates with power state.
- [x] File access delay and Log_Fixer delay match the planned states.
- [x] Wrong submission produces visible/audio-like feedback even with placeholder audio.
- [x] Blackout is a distinct event, not only a disabled UI state.
- [x] The game remains playable and does not soft-lock during or after blackout.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Implementation Notes

- Updated Caution file access delay to the DOCX-planned 0.5 seconds.
- Updated Warning Log_Fixer delay so the base recovery runtime doubles.
- Added clearer HUD copy for each power threshold, including O2 multiplier and interaction penalty.
- Added threshold-triggered placeholder audio cues for Caution, Warning, Critical, and Blackout.
- Strengthened Warning scanline/glitch feedback and Blackout monitor dimming.
- Blackout alert now explicitly frames the 10-second silent reboot and 10% emergency recovery.

## Validation

- `npm run build` passed.
- `git diff --check` passed.

## Delivery

- code repo commit: `feat-023 add docx resource pressure feedback as gameplay feel`
- code repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-08 | dev-agent | todo -> in_progress | Started DOCX resource pressure feedback implementation after feat-022 |
| 2026-08-08 | dev-agent | in_progress -> done | Added threshold copy, timing updates, visual feedback, and placeholder audio hooks |

## Source References

- `project/human-input/우주선 탈출게임 개요.docx`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/docx_content_conversion_plan.md`
