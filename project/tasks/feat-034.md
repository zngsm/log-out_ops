# feat-034 Implement ECHO update proposal, approval trigger, extended 5s->9s CSS/SVG reboot sequence, and lockdown HUD/timer transition

## Status

- status: done
- type: feat
- priority: 49
- owner agent: dev-agent
- branch: `feat-034-implement-echo-update-approval-and-reboot-lockdown`
- commit message: `feat-034 implement echo update approval trigger css svg reboot sequence and lockdown hud timer transition`

## Goal

Apply Change-001 transition requirements and Q17~Q19, Q24~Q26, Q31 answers: embed "ECHO 시스템 업데이트 필요" proposal in the work mission list (completely removing developer warning meta text "⚠️ [ECHO 시스템 업데이트 승인] 버튼 클릭 시 ECHO 패치가 적용되고 시스템 재부팅 후 본 비상 봉쇄 시퀀스로 진입합니다." - Q24), trigger ECHO reboot upon approval click (exclusive transition trigger), present reboot using CSS / SVG in-game effects with an adjusted cutscene timeline (shortening rebooting state duration by 2s and extending lockdown emergency state duration by 2s - Q19, Q26, Q31 user feedback), hide colleague messenger speech-bubble icon completely during reboot (`rebootState !== 'idle'`), transition into emergency lockdown state with oxygen/power HUD display and 60-minute timer activation, and completely remove `ECHO STATE / monitoring` card from top title-bar status HUD (Q25).

## Scope

- Embed "ECHO 시스템 업데이트 필요" (ECHO System Update Required) proposal task within the left work desktop UI, completely removing developer warning meta text (`"⚠️ [ECHO 시스템 업데이트 승인] 버튼 클릭 시 ECHO 패치가 적용되고 시스템 재부팅 후 본 비상 봉쇄 시퀀스로 진입합니다."`) (Q24).
- Completely remove the `ECHO STATE / monitoring` card from top title-bar status HUD (Q25).
- On player clicking [업데이트 승인] (Approve Update) — the exclusive transition trigger (Q17):
  - Trigger ECHO chat window reboot sequence (CSS / SVG visual glitch, rebooting animation, sound cue) with an **adjusted cutscene timeline** (rebooting state duration shortened by 2s, lockdown emergency state duration extended by 2s) (Q19, Q26, Q31).
  - Hide colleague messenger speech-bubble icon completely during the reboot sequence (`rebootState !== 'idle'`).
- Post-reboot lockdown transition:
  - ECHO returns online after the cutscene, misidentifies player/ship environment as bio-hazard threat, and declares emergency quarantine lockdown.
  - Reveal oxygen/power emergency HUD (100% O2 / 100% Power) and START 60-minute countdown timer at lockdown onset (Q18).
  - Open Hermes OS file explorer and enable main puzzle evidence submission loop (Act 1~3).

## Dependencies

- before: `feat-033`
- after: `qa-004`

## Acceptance Criteria

- [x] "ECHO 시스템 업데이트 필요" proposal is present in the work mission list with developer warning meta text (`"⚠️ [ECHO 시스템 업데이트 승인] 버튼 클릭 시..."`) completely removed.
- [x] `ECHO STATE / monitoring` card is completely removed from the top title-bar status HUD.
- [x] Clicking [업데이트 승인] is the exclusive transition trigger that initiates ECHO chat reboot sequence.
- [x] Reboot sequence displays CSS / SVG visual glitch, rebooting animation, system error warning, emergency siren, and decompression across an adjusted cutscene timeline (rebooting state shortened by 2s, lockdown emergency state extended by 2s - Q31).
- [x] Colleague messenger speech-bubble icon is completely hidden (unrendered) from the screen while reboot is active (`rebootState !== 'idle'`).
- [x] Re-opened ECHO misinterprets player as threat and issues lockdown declaration upon completion of the cutscene.
- [x] Emergency oxygen/power HUD appears and 60-minute countdown timer starts running upon lockdown declaration.
- [x] Gameplay transitions to Category A main puzzle loop (Act 1~3).
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Review History

- 2026-08-09: `review_agent` approved implementation.
  - Exclusive transition trigger on [업데이트 승인] verified.
  - ECHO update proposal meta warning text removal verified.
  - Title-bar `ECHO STATE / monitoring` HUD card removal verified.
  - CSS / SVG visual glitch & reboot sequence (`RebootGlitchPresentation`) verified with audio cues (`comm-glitch`, `reboot`, `warning-siren`, `door-lock`, `decompression`) and adjusted cutscene timeline (rebooting -2s, lockdown +2s).
  - ECHO lockdown declaration and emergency HUD / 60-minute timer transition verified.
  - `npm run build` and `git diff --check` verified clean.

## Source References

- `project/changes/change-001.md`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/pm_questions.md#Q17`
- `project/pm_questions.md#Q18`
- `project/pm_questions.md#Q19`
- `project/pm_questions.md#Q24`
- `project/pm_questions.md#Q25`
- `project/pm_questions.md#Q31`

