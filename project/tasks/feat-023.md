# feat-023 Add DOCX resource pressure feedback as gameplay feel

## Status

- status: todo
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

- [ ] Power thresholds visibly change room/terminal state.
- [ ] O2 drain multiplier is readable and updates with power state.
- [ ] File access delay and Log_Fixer delay match the planned states.
- [ ] Wrong submission produces visible/audio-like feedback even with placeholder audio.
- [ ] Blackout is a distinct event, not only a disabled UI state.
- [ ] The game remains playable and does not soft-lock during or after blackout.
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Source References

- `project/human-input/우주선 탈출게임 개요.docx`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/docx_content_conversion_plan.md`

