# feat-034 Implement ECHO update approval trigger, CSS/SVG reboot sequence, and lockdown HUD/timer transition

## Status

- status: todo
- type: feat
- priority: 49
- owner agent: dev-agent
- branch: `feat-034-implement-echo-update-approval-and-reboot-lockdown`
- commit message: `feat-034 implement echo update approval trigger css svg reboot sequence and lockdown hud timer transition`

## Goal

Apply Change-001 transition requirements and Q17, Q18, Q19 answers: embed "ECHO 시스템 업데이트 필요" proposal in the work mission list, trigger ECHO reboot upon approval click (exclusive transition trigger), present reboot using CSS / SVG in-game effects, and transition into emergency lockdown state with oxygen/power HUD display and 60-minute timer activation.

## Scope

- Embed "ECHO 시스템 업데이트 필요" (ECHO System Update Required) proposal task within the left work desktop UI.
- On player clicking [업데이트 승인] (Approve Update) — the exclusive transition trigger (Q17):
  - Trigger ECHO chat window reboot sequence (CSS / SVG visual glitch, rebooting animation, sound cue) (Q19).
- Post-reboot lockdown transition:
  - ECHO returns online, misidentifies player/ship environment as bio-hazard threat, and declares emergency quarantine lockdown.
  - Reveal oxygen/power emergency HUD (100% O2 / 100% Power) and START 60-minute countdown timer at lockdown onset (Q18).
  - Open Hermes OS file explorer and enable main puzzle evidence submission loop (Act 1~3).

## Dependencies

- before: `feat-033`
- after: `qa-004`

## Acceptance Criteria

- [ ] "ECHO 시스템 업데이트 필요" proposal is present in the work mission list.
- [ ] Clicking [업데이트 승인] is the exclusive transition trigger that initiates ECHO chat reboot sequence.
- [ ] Reboot sequence displays CSS / SVG visual glitch, rebooting animation, and sound cue.
- [ ] Re-opened ECHO misinterprets player as threat and issues lockdown declaration.
- [ ] Emergency oxygen/power HUD appears and 60-minute countdown timer starts running upon lockdown declaration.
- [ ] Gameplay transitions to Category A main puzzle loop (Act 1~3).
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Source References

- `project/changes/change-001.md`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/pm_questions.md#Q17`
- `project/pm_questions.md#Q18`
- `project/pm_questions.md#Q19`

