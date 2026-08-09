# feat-033 Build diegetic workstation layout, [확인 완료] button task flow, colleague messenger popup (left panel top-right)/draggable app UI with notification bubble (left panel bottom-right), and candidate resume narrative evaluation

## Status

- status: done
- type: feat
- priority: 48
- owner agent: dev-agent
- branch: `feat-033-build-dual-panel-work-interface-and-rapport-phase`
- commit message: `feat-033 build dual-panel work interface and 5-mission echo rapport phase flow`

## Goal

Apply Change-001 requirements and Q21~Q23, Q26~Q27 user feedback answers: build a diegetic workstation layout (completely removing developer terms like "HERMES 2-SPLIT DUAL PANEL WORK INTERFACE" and "라포 Phase"), implement ECHO task briefing with natural diegetic introductory dialogues (replacing developer guide-style copy such as "좌측 보고서 하단의 [확인 완료] 버튼을 눌러 다음 업무로 진행하세요" with in-world dialogue) and left document bottom simple fixed **`✓ [확인 완료]`** button transition mechanism (completely removing "(다음 업무로 이동)" bracket sub-text; Q22: clicking button prints ECHO prompt "다음 업무는 [다음 업무명]입니다. 보여드릴게요." in right chat and transitions left document screen), output real-time ECHO reaction dialogues (max 2 per report), handle random colleague messenger popup notifications bounded within the left workspace panel top-right (좌측 업무 화면 오른쪽 상단) with dedicated draggable messenger app UI window within left workspace panel boundary (좌측 업무 화면 경계 내 위치 자유 이동), minimized speech-bubble icon with red badge `1` bounded within the left workspace panel bottom-right (좌측 업무 화면 오른쪽 하단) before reply, hidden after reply completion, and completely hidden/unrendered during reboot presentation (`rebootState !== 'idle'`) (Q23, Q26), lunch menu question ("오늘 점심 메뉴 뭐먹을래?"), free-text reply and 1-time positive reaction ("그 메뉴 좋다!"), completely removing reply input box meta text ("※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다.") and maintaining natural diegetic UX while keeping subsequent player messages as `Unread(1)` (Q23), and implement applicant resume review with candidate evaluation ('적격'/'부적격' decision with zero gameplay/puzzle/ending impact - narrative choice) while completely removing meta notice banner (`※ 안내: 본 이력서 적합성 판정은...`) and `서사적 판정 선택:` label, enforcing fixed **`✓ [확인 완료]`** button text with grey disabled styling (`disabled={isResumeIncomplete}`) when any unselected candidates exist to require complete evaluation of all 3 applicants (Q27), and completely disabling the right ECHO chat window and Q&A dialogue input during the resume review stage (ECHO 대화 비활성화) (Q21).

## Scope

- **Diegetic Workstation UI**:
  - Remove all developer terms from UI header: "HERMES 2-SPLIT DUAL PANEL WORK INTERFACE", "라포 Phase" etc.
  - Render authentic Hermes Workstation interface.
- **ECHO Task Briefing & Simple Fixed `✓ [확인 완료]` Button Document Transition (Remove Left Tabs & Meta Sub-texts)** (Q22, Q27):
  - Remove tab-based free selection menu on left panel.
  - ECHO briefs daily tasks on right chat panel using natural diegetic dialogues (removing guide-style text such as "좌측 보고서 하단의 [확인 완료] 버튼을 눌러 다음 업무로 진행하세요").
  - Place prominent **`✓ [확인 완료]`** button at the bottom of left document/report screen, completely removing "(다음 업무로 이동)" bracket sub-text (rendered solely as fixed `✓ [확인 완료]`).
  - On player clicking **`✓ [확인 완료]`**:
    1. Right ECHO chat outputs: `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."`
    2. Left panel transitions to the next work document/report.
- **Live ECHO Reactions & Sequential Progression**:
  - **Resource Mining Status Report**: Pushed by ECHO ➔ Left panel renders trend graph & statistics ➔ Real-time ECHO reaction dialogues (up to 2) while player reads report (e.g., positive reaction on high mining) ➔ Left bottom `✓ [확인 완료]` button click transitions to Document 2.
  - **Ship Power/Oxygen Status Report**: Left panel renders telemetry ➔ Real-time ECHO reaction dialogues (up to 2) ➔ Left bottom `✓ [확인 완료]` button click transitions to Document 3.
- **Colleague Messenger Popup Event, Separate Draggable App UI, Minimized Bubble Badge `1`, & Reboot Hide UX** (Q23, Q26):
  - Triggers randomly during Power/Oxygen report review or Resume review stage.
  - **Notification Popup (Left Panel Top-Right)**: Bounded strictly inside the left workspace panel (Desktop Workspace Panel / Left Panel, not full viewport or right ECHO panel) at top-right (오른쪽 상단) with notification SFX.
  - **Separate Draggable Messenger App UI (Left Panel Bound)**: Clicking popup opens a dedicated messenger/chat app window interface inside the left workspace panel, which the player can freely drag and reposition within the left panel boundary (Draggable UI).
  - **Minimized / Unanswered UX & New Message Bubble (Left Panel Bottom-Right)**: Player can minimize or close popup/chat window to answer later. Before player reply, minimizing displays a speech-bubble chat app icon + red notification badge/bubble (`1`) bounded strictly inside the left workspace panel at bottom-right (오른쪽 하단) (clicking icon re-opens messenger app window). When player minimizes/closes the chat window **after completing a reply**, the red notification bubble (숫자 `1`) is **no longer displayed** on the minimized speech-bubble icon (Q23 user feedback).
  - **Complete Messenger Bubble Hide During Reboot**: During ECHO reboot presentation (`rebootState !== 'idle'`), the bottom-right colleague messenger speech-bubble icon is completely hidden (unrendered) from the screen (Q26 user feedback).
  - **Question Copy**: Always asks for lunch menu (e.g., `"오늘 점심 메뉴 뭐먹을래?"`).
  - **Reply & Reaction**: Player inputs free-text reply ➔ Colleague sends 1 positive reaction message (`"그 메뉴 좋다!"`).
  - **Input Box Placeholder Refinement (Q52)**: Completely remove `(자유 텍스트)` sub-label from input box placeholder, displaying purely `답장을 입력하세요...`.
  - **Korean IME Composition & Post-Send Input Bug Fix (Q53)**: Intercept `isComposing` state and apply synthetic clear upon sending so that the last composed Korean word does not auto-persist or re-input after submission, guaranteeing an empty input box.
  - **Remove Meta Guidance Text & Maintain Diegetic UX**: Completely remove immersion-breaking meta notice text under reply input box (`"※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다."`). Maintain natural diegetic UI/UX after player reply without exposing any system meta guidance text.
  - **Infinite Conversation Prevention**: Subsequent player messages after 1-time reaction maintain `Unread` (`읽지 않음(1)`) status naturally without system meta guidance text.
- **Applicant Resume Review Stage & Narrative Choice (Meta Text Removal, Fixed Label & Grey Disabled Styling)** (Q21, Q27):
  - Present 3 applicant candidate profiles on left screen.
  - Provide candidate-by-candidate 'Qualified' (적격) / 'Unqualified' (부적격) decision buttons.
  - **Remove Meta Notice Banner**: Completely remove `※ 안내: 본 이력서 적합성 판정은 서사적 몰입을 위한 인사 평가 선택 항목으로, 게임 퍼즐/엔딩에는 영향을 주지 않습니다.` meta text banner.
  - **Remove "서사적 판정 선택" Label**: Completely remove `서사적 판정 선택:` label text in front of decision buttons for each candidate.
  - **Fixed Button Label & Enforce Required Evaluation via Grey Disabled Styling**: In the resume review stage (`activeStep === 'resume'`), keep the button label fixed as `✓ [확인 완료]` without changing text. If any of the 3 candidates has an unselected ('none') evaluation status, apply grey disabled styling (`disabled={isResumeIncomplete}`) to the left bottom **`✓ [확인 완료]`** button to compel complete evaluation of all 3 candidates before proceeding (Q27 user feedback).
  - **Zero Gameplay Impact**: Explicitly enforce that decision results have zero impact on game progression, puzzles, or endings (narrative immersive choice element).
  - **Disable ECHO Dialogue / Q&A**: Completely remove and disable right ECHO chat window interaction and Q&A dialogue input functionality during the applicant resume review stage (ECHO 대화 불가능 처리).
  - Left bottom `✓ [확인 완료]` button click (enabled once all 3 candidates are evaluated) transitions to ECHO Update Proposal.
- **Keep Emergency HUD & Timer Inactive**:
  - Emergency HUD (oxygen/power) and 60-minute session timer remain **HIDDEN and INACTIVE** during the entire rapport phase.

## Dependencies

- before: `feat-032`
- after: `feat-034`

## Acceptance Criteria

- [x] Workstation header contains zero developer terms ("HERMES 2-SPLIT DUAL PANEL", "라포 Phase" removed).
- [x] Tab-based selection on left panel is removed; ECHO briefs tasks on right chat panel with natural diegetic dialogues (developer guide-style copy removed) and document transition is triggered via left bottom simple fixed **`✓ [확인 완료]`** button (without "(다음 업무로 이동)" sub-label).
- [x] Clicking [확인 완료] outputs ECHO prompt `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` in right chat and transitions left panel to next document.
- [x] ECHO outputs real-time reaction dialogues (max 2) while player reads reports.
- [x] Colleague messenger popup event triggers randomly during Power/O2 report or resume review stage with notification SFX, strictly bounded within left workspace panel top-right (좌측 업무 화면 내 오른쪽 상단).
- [x] Clicking popup opens dedicated messenger app window displaying lunch menu question (`"오늘 점심 메뉴 뭐먹을래?"`), which allows player to freely drag and reposition within the left workspace panel boundary (Draggable UI).
- [x] Minimizing/closing messenger displays a speech-bubble chat icon + red notification bubble (`1`) before reply strictly bounded within left workspace panel bottom-right (좌측 업무 화면 내 오른쪽 하단), and after reply completion, minimizing/closing removes the red notification bubble (`1`) from the icon.
- [x] During ECHO reboot presentation (`rebootState !== 'idle'`), the bottom-right colleague messenger speech-bubble icon is completely hidden (unrendered) from the screen.
- [x] Player can reply with free text in colleague messenger; colleague sends 1 positive reaction message (`"그 메뉴 좋다!"`), reply input box meta text (`"※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다."`) and placeholder sub-label `(자유 텍스트)` (Q52) are completely removed, Korean IME composition and post-send input residual bug is fixed to ensure a clean empty input box (Q53), and subsequent player messages maintain 'Unread(1)' (`읽지 않음(1)`) state with natural diegetic UX.
- [x] Applicant resume review displays 3 candidate profiles with 'Qualified' / 'Unqualified' decision buttons (with 0 impact on gameplay/ending).
- [x] Applicant resume review meta notice banner (`※ 안내: 본 이력서 적합성 판정은...`) is completely removed from the screen.
- [x] Label text `서사적 판정 선택:` in front of decision buttons is completely removed.
- [x] Button text is fixed as `✓ [확인 완료]` without text alterations, and when any candidate has an unselected evaluation state, grey disabled styling (`disabled={isResumeIncomplete}`) is applied, enforcing complete evaluation of all 3 applicants before progressing to the update proposal.
- [x] Right ECHO chat window and Q&A dialogue input are completely disabled during the resume review stage (ECHO 대화 비활성화).
- [x] Emergency oxygen/power HUD and 60-minute timer are HIDDEN and INACTIVE during the rapport phase.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Review History

- 2026-08-09: APPROVED by review_agent.
  - Diegetic Workstation UI verified (meta terms "HERMES 2-SPLIT DUAL PANEL", "라포 Phase" removed).
  - Sequential document transition via left bottom [확인 완료] button & ECHO prompt ("다음 업무는 [다음 업무명]입니다. 보여드릴게요.") verified (left tabs removed).
  - Real-time ECHO reaction dialogues (max 2 per report) verified.
  - Colleague messenger popup (left panel top-right), dedicated draggable messenger app UI window within left panel, minimized bubble badge 1 (left panel bottom-right before reply / hidden after reply completion), free-text reply + 1-time positive reaction ("그 메뉴 좋다!"), meta notice text removal ("※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다."), and subsequent diegetic Unread(1) status verified.
  - Applicant resume review with 3 candidate profiles, 'Qualified'/'Unqualified' decision buttons (0 impact on gameplay/ending), meta notice banner removal, '서사적 판정 선택:' label removal, disabled [확인 완료] button for unselected candidates, and ECHO dialogue/Q&A disabled verified.
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


