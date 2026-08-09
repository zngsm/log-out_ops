# feat-033 Build dual-panel work interface and 5-mission ECHO rapport phase flow

## Status

- status: todo
- type: feat
- priority: 48
- owner agent: dev-agent
- branch: `feat-033-build-dual-panel-work-interface-and-rapport-phase`
- commit message: `feat-033 build dual-panel work interface and 5-mission echo rapport phase flow`

## Goal

Apply Change-001 rapport phase requirements and Q16, Q18 answers: build a split-screen work interface (Left: Desktop UI, Right: ECHO Chat Window), keep oxygen/power HUD and 60-min timer hidden/inactive during rapport phase, and implement the 5 daily work missions driven by player action.

## Scope

- Create 2-split layout upon [출근] click:
  - Left Panel: Desktop UI for AI manager daily work tasks.
  - Right Panel: ECHO AI Chat Window.
- Keep emergency HUD (oxygen/power) and 60-minute session timer **HIDDEN and INACTIVE** during the entire Rapport Phase.
- Implement 5 interactive work missions on the left Desktop UI (driven by player interaction, duration flexible):
  1) **자원 채굴 현황 보고서** (Resource Mining Status Report: trend graph, statistical data UI).
  2) **함선 전력/산소 현황 보고서** (Ship Power & Oxygen Status Report: ship resource telemetry data).
  3) **동료 메시지 답장** (Colleague Message Reply e.g. "오늘 점심 메뉴 뭐먹을래?" ➔ colleague reaction response received).
  4) **김우주 동료 포지션 지원자 이력서 검토** (Resume Review for applicant applying for Kim Wooju's colleague role).
  5) **ECHO 시스템 업데이트 기안 승인** (ECHO System Update Proposal Approval - triggers transition to feat-034).
- Implement ECHO assistant interactions on the right panel:
  - ECHO assistant notifications (e.g. "간밤에 지구로부터 보고서가 도착했습니다", outputting report on work screen).
  - ECHO morning greeting ("좋은 아침입니다"), daily status briefing, and casual small talk.

## Dependencies

- before: `feat-032`
- after: `feat-034`

## Acceptance Criteria

- [ ] Split layout is activated upon clicking [출근].
- [ ] Left side displays work desktop UI; Right side displays ECHO chat window.
- [ ] Emergency oxygen/power HUD and 60-minute timer are HIDDEN and INACTIVE during the rapport phase.
- [ ] Left work UI renders 5 interactive work missions (resource mining graph/stats report, ship power/oxygen report, colleague message reply & reaction, applicant resume review, ECHO update approval proposal).
- [ ] Replying to colleague message triggers reception of colleague reaction message.
- [ ] ECHO initiates assistant dialogs (morning greeting, Earth report alert, briefing, small talk).
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Source References

- `project/changes/change-001.md`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/pm_questions.md#Q16`
- `project/pm_questions.md#Q18`

