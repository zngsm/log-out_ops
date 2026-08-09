# feat-033 Build diegetic workstation layout, [확인 완료] button task flow, colleague messenger popup (top-right)/app UI with notification bubble (bottom-right), and candidate resume narrative evaluation

## Status

- status: done
- type: feat
- priority: 48
- owner agent: dev-agent
- branch: `feat-033-build-dual-panel-work-interface-and-rapport-phase`
- commit message: `feat-033 build dual-panel work interface and 5-mission echo rapport phase flow`

## Goal

Apply Change-001 requirements and Q21~Q23 user feedback answers: build a diegetic workstation layout (completely removing developer terms like "HERMES 2-SPLIT DUAL PANEL WORK INTERFACE" and "라포 Phase"), implement ECHO task briefing with natural diegetic introductory dialogues (replacing developer guide-style copy such as "좌측 보고서 하단의 [확인 완료] 버튼을 눌러 다음 업무로 진행하세요" with in-world dialogue) and left document bottom simple **[확인 완료]** button transition mechanism (completely removing "(다음 업무로 이동)" bracket sub-text; Q22: clicking button prints ECHO prompt "다음 업무는 [다음 업무명]입니다. 보여드릴게요." in right chat and transitions left document screen), output real-time ECHO reaction dialogues (max 2 per report), handle random colleague messenger popup notifications at top-right with dedicated messenger app UI window, minimized speech-bubble icon with red badge `1` at bottom-right of 2-split workstation screen, lunch menu question ("오늘 점심 메뉴 뭐먹을래?"), free-text reply and 1-time positive reaction ("그 메뉴 좋다!"), maintaining subsequent player messages as `Unread(1)` (Q23), and implement applicant resume review with candidate evaluation ('적격'/'부적격' decision with zero gameplay/puzzle/ending impact - narrative choice) & ECHO suitability Q&A (Q21).

## Scope

- **Diegetic Workstation UI**:
  - Remove all developer terms from UI header: "HERMES 2-SPLIT DUAL PANEL WORK INTERFACE", "라포 Phase" etc.
  - Render authentic Hermes Workstation interface.
- **ECHO Task Briefing & Simple [확인 완료] Button Document Transition (Remove Left Tabs & Meta Sub-texts)** (Q22):
  - Remove tab-based free selection menu on left panel.
  - ECHO briefs daily tasks on right chat panel using natural diegetic dialogues (removing guide-style text such as "좌측 보고서 하단의 [확인 완료] 버튼을 눌러 다음 업무로 진행하세요").
  - Place prominent **[확인 완료]** button at the bottom of left document/report screen, completely removing "(다음 업무로 이동)" bracket sub-text (rendered solely as `[확인 완료]`).
  - On player clicking **[확인 완료]**:
    1. Right ECHO chat outputs: `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."`
    2. Left panel transitions to the next work document/report.
- **Live ECHO Reactions & Sequential Progression**:
  - **Resource Mining Status Report**: Pushed by ECHO ➔ Left panel renders trend graph & statistics ➔ Real-time ECHO reaction dialogues (up to 2) while player reads report (e.g., positive reaction on high mining) ➔ Left bottom [확인 완료] button click transitions to Document 2.
  - **Ship Power/Oxygen Status Report**: Left panel renders telemetry ➔ Real-time ECHO reaction dialogues (up to 2) ➔ Left bottom [확인 완료] button click transitions to Document 3.
- **Colleague Messenger Popup Event, Separate App UI, & Minimized Bubble Badge `1`** (Q23):
  - Triggers randomly during Power/Oxygen report review or Resume review stage.
  - **Notification Popup**: Top-right (오른쪽 상단) popup notification with SFX appears on 2-split workstation screen.
  - **Separate Messenger App UI**: Clicking popup opens a dedicated messenger/chat app window interface inside workstation screen.
  - **Minimized / Unanswered UX & New Message Bubble**: Player can minimize or close popup/chat window to answer later. Minimized state displays a speech-bubble chat app icon + red notification badge/bubble (`1`) at bottom-right (오른쪽 하단) of 2-split workstation screen. Clicking icon re-opens messenger app window.
  - **Question Copy**: Always asks for lunch menu (e.g., `"오늘 점심 메뉴 뭐먹을래?"`).
  - **Reply & Reaction**: Player inputs free-text reply ➔ Colleague sends 1 positive reaction message (`"그 메뉴 좋다!"`).
  - **Infinite Conversation Prevention**: Subsequent player messages after 1-time reaction maintain `Unread` (`읽지 않음(1)`) status.
- **Applicant Resume Review Stage & Narrative Choice** (Q21):
  - ECHO dialogue prompt ("지원자 적합성에 대해 제게 질문하셔도 좋습니다").
  - Present multiple applicant candidate profiles on left screen.
  - Provide candidate-by-candidate 'Qualified' (적격) / 'Unqualified' (부적격) decision buttons.
  - **Zero Gameplay Impact**: Explicitly enforce that decision results have zero impact on game progression, puzzles, or endings (narrative immersive choice element).
  - Enable player to ask ECHO suitability questions via right chat window.
  - Left bottom [확인 완료] button click transitions to ECHO Update Proposal.
- **Keep Emergency HUD & Timer Inactive**:
  - Emergency HUD (oxygen/power) and 60-minute session timer remain **HIDDEN and INACTIVE** during the entire rapport phase.

## Dependencies

- before: `feat-032`
- after: `feat-034`

## Acceptance Criteria

- [x] Workstation header contains zero developer terms ("HERMES 2-SPLIT DUAL PANEL", "라포 Phase" removed).
- [x] Tab-based selection on left panel is removed; ECHO briefs tasks on right chat panel with natural diegetic dialogues (developer guide-style copy removed) and document transition is triggered via left bottom simple **[확인 완료]** button (without "(다음 업무로 이동)" sub-label).
- [x] Clicking [확인 완료] outputs ECHO prompt `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` in right chat and transitions left panel to next document.
- [x] ECHO outputs real-time reaction dialogues (max 2) while player reads reports.
- [x] Colleague messenger popup event triggers randomly during Power/O2 report or resume review stage with notification SFX and top-right (오른쪽 상단) popup window.
- [x] Clicking popup opens dedicated messenger app window displaying lunch menu question (`"오늘 점심 메뉴 뭐먹을래?"`).
- [x] Minimizing/closing messenger displays a speech-bubble chat icon + red notification bubble (`1`) at bottom-right (오른쪽 하단) of 2-split workstation screen, and clicking it re-opens messenger app window.
- [x] Player can reply with free text in colleague messenger; colleague sends 1 positive reaction message (`"그 메뉴 좋다!"`), and subsequent player messages maintain 'Unread(1)' (`읽지 않음(1)`) state.
- [x] Applicant resume review displays multiple candidate profiles with 'Qualified' / 'Unqualified' decision buttons (with 0 impact on gameplay/ending) and ECHO suitability Q&A capability.
- [x] Emergency oxygen/power HUD and 60-minute timer are HIDDEN and INACTIVE during the rapport phase.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Review History

- 2026-08-09: APPROVED by review_agent.
  - Diegetic Workstation UI verified (meta terms "HERMES 2-SPLIT DUAL PANEL", "라포 Phase" removed).
  - Sequential document transition via left bottom [확인 완료] button & ECHO prompt ("다음 업무는 [다음 업무명]입니다. 보여드릴게요.") verified (left tabs removed).
  - Real-time ECHO reaction dialogues (max 2 per report) verified.
  - Colleague messenger popup (top-right), dedicated messenger app UI window, minimized bubble badge 1 (bottom-right), free-text reply + 1-time positive reaction ("그 메뉴 좋다!"), and subsequent Unread(1) status verified.
  - Applicant resume review with 3 candidate profiles, 'Qualified'/'Unqualified' decision buttons (0 impact on gameplay/ending), and ECHO suitability Q&A verified.
  - Emergency HUD and 60-minute timer hidden & inactive during rapport phase verified.
  - `npm run build` and `git diff --check` passed cleanly.

## Source References

- `project/changes/change-001.md`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/pm_questions.md#Q16`
- `project/pm_questions.md#Q18`
- `project/pm_questions.md#Q21`
- `project/pm_questions.md#Q22`
- `project/pm_questions.md#Q23`


