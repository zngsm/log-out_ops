# feat-035 Unify post-cutscene main puzzle terminal UI with pre-cutscene workstation UI layout, header, color theme, and 2-split body structure

## Status

- status: done
- type: feat
- priority: 52
- owner agent: dev-agent
- branch: `feat-035-unify-post-cutscene-terminal-ui`
- commit message: `feat-035 unify post cutscene main puzzle terminal ui with pre cutscene workstation layout and header`

## Goal

Apply Change-001 user feedback requirements and Q55 answer: unify the layout, header, color theme, and 2-split body structure of the post-cutscene in-game main puzzle terminal UI (`App.tsx`: `terminal-frame`) with the pre-cutscene workstation UI (`WorkInterface.tsx`: `work-split-container`, `work-header`, `work-split-body`, `work-left-panel`, `work-right-panel`) to guarantee 100% visual continuity and prevent immersion breaks.

## Scope

- **Layout, Header, Color Theme & 2-Split Structure Unification**:
  - Align post-cutscene main puzzle terminal UI (`App.tsx`: `terminal-frame`) with pre-cutscene workstation UI (`WorkInterface.tsx`: `work-split-container`, `work-header`, `work-split-body`, `work-left-panel`, `work-right-panel`).
- **Header (`work-header` Style Unification)**:
  - Left side: Render `HERMES WORKSTATION` badge and `HERMES SHIP SYSTEM COMMAND` title.
  - Right side: Render `근무자: 김우주 (AI 관리 담당자)` (Worker: Woo-joo Kim), `● EMERGENCY LOCKDOWN ACTIVE` status indicator, and compact emergency HUD (`[O₂ Level]`, `[Power Grid]`, `[REMAINING TIME]`).
- **2-Split Panel Body (`work-split-body` 1.6fr 1fr Structure Unification)**:
  - Left Panel (`work-left-panel`): Integrate File Explorer and File Viewer within the left viewport to provide a unified terminal workspace.
  - Right Panel (`work-right-panel` / `echo-chat-panel`): Render ECHO conversation and Evidence Submission composer panel using identical view presentation and styling as pre-cutscene workstation.
- **100% Visual Continuity Guarantee**:
  - Connect terminal screen frame, panel header style, scrollbar styling, border gradients, and font size seamlessly across the cutscene transition so players experience zero visual disconnect or jarring shift.

## Dependencies

- before: `feat-034`, `bug-011`
- after: human visual review / QA

## Acceptance Criteria

- [x] Post-cutscene terminal UI layout, header, color theme, and 2-split body structure (`App.tsx`: `terminal-frame`) match pre-cutscene workstation UI (`WorkInterface.tsx`: `work-split-container`, `work-header`, `work-split-body`, `work-left-panel`, `work-right-panel`) 100%.
- [x] Header (`work-header`) displays `HERMES WORKSTATION` badge and `HERMES SHIP SYSTEM COMMAND` on the left, and worker info (`근무자: 김우주 (AI 관리 담당자)`), `● EMERGENCY LOCKDOWN ACTIVE` status, and compact emergency HUD (`[O₂ Level]`, `[Power Grid]`, `[REMAINING TIME]`) on the right.
- [x] Body (`work-split-body`) maintains a 1.6fr : 1fr split layout with File Explorer & File Viewer on the left panel (`work-left-panel`) and ECHO chat & Evidence Submission composer on the right panel (`work-right-panel` / `echo-chat-panel`).
- [x] Terminal screen frame, panel header styling, scrollbars, border gradients, and font sizes are 100% identical before and after the emergency cutscene transition.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Review History

- 2026-08-10: Task specification created and ops documentation updated per user feedback.

## Source References

- `project/changes/change-001.md#13`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/pm_questions.md#Q55`
