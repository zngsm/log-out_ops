# feat-039 Refine initial ECHO intro, compact log viewer header, remove checkpoint hint, reset input and attachments after submit, prevent auto-attach after log fixer, support log fixer for Recycle_Bin files, and enforce strict Act 2 to Act 3 transition

## Status

- status: done
- type: feat
- priority: 56
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-039 refine initial ECHO intro, compact log viewer header, remove checkpoint hint, reset input/attachments after submit, prevent auto-attach after log fixer, support log fixer for Recycle_Bin files, and enforce strict Act 2 to Act 3 transition`

## Goal

Apply 7 core gameplay, UI, and bug fix refinement specifications:
1. **Remove Initial ECHO Dialogue**: Completely remove the initial briefing text ("김우주 담당자님, 출근이 확인되었습니다. 헤르메스호 업무 데스크탑과 관리 AI ECHO 보조 채널이 활성화되었습니다").
2. **Compact Log Viewer Header**: Minimize font size and padding/margin of file viewer title (`h2`), path, and classification box so that file body content (`<pre>`) occupies most of the viewer area.
3. **Remove Checkpoint Hint**: Completely remove the checkpoint hint text ("첨부한 파일 조합이 현재 Act와 맞지 않습니다. 파일 뷰어의 Evidence 항목과 현재 목표를 다시 대조하세요.") and its associated guidance notice block.
4. **Reset Input & Attachments After Submit**: Immediately reset message input (`messageInput = ""`) and attached file tray (`attachedFileIds = []`) to empty states upon submitting a message/evidence, regardless of success or failure.
5. **Prevent Auto-Attach After Log_Fixer**: When file recovery completes via Log_Fixer, perform only file viewer selection (`selectFile`) without automatically attaching the file to ECHO (`attachedFileIds`), requiring manual clicking of `[ECHO에 증거 첨부]`.
6. **Support Log_Fixer for Recycle_Bin Files**: Enable the `[LOG_FIXER로 데이터 복구]` button when selecting corrupted/deleted files inside `/Recycle_Bin/` (`blackbox_raw.log`, `deleted_override.txt`, etc.) and allow recovery (`recoveredFileIds`).
7. **Fix Act 2 to Act 3 Transition & Prevent Early Ending Trigger**: Strictly transition to Act 3 (`act-3`) upon Act 2 success, and enforce strict guardrails preventing transition to `door_unlocked` or `ending-ready` states before Act 3 evidence verification is complete.

## Scope

- **Initial ECHO Dialogue Removal**: Remove pre-briefing welcome/channel activation text from ECHO chat window in workstation phase.
- **Log Viewer Layout Compactness**: Adjust CSS and HTML layout for file viewer title (`h2`), path, and classification box to minimize spacing and maximize `<pre>` body view height.
- **Checkpoint Hint Block Removal**: Delete all instances of checkpoint hint text and guidance blocks when evidence combination mismatches current Act.
- **Input and Attachment Clear Logic**: Update message submission handler to clear `messageInput` to `""` and `attachedFileIds` to `[]` immediately after submission.
- **Log_Fixer Post-Recovery Selection Only**: Modify recovery handler so that completing Log_Fixer calls `selectFile(...)` but does not append to `attachedFileIds`.
- **Recycle_Bin Log_Fixer Enablement**: Allow files in `/Recycle_Bin/` that are damaged or deleted to present the `[LOG_FIXER로 데이터 복구]` action and register as recovered files when clicked.
- **Strict Act 2 to Act 3 Transition Guardrails**: Ensure Act 2 clear logic explicitly sets stage to `act-3` and blocks any transition to `door_unlocked` / ending state until `ai_priority_matrix.json` + `deleted_override.txt` are verified in Act 3.

## Acceptance Criteria

- [x] Initial ECHO briefing dialogue ("김우주 담당자님, 출근이 확인되었습니다...") is completely removed.
- [x] Log viewer header elements (h2, path, classification) are compact with minimal padding/margin, allowing `<pre>` body to fill most of the panel area.
- [x] Checkpoint hint text ("첨부한 파일 조합이 현재 Act와 맞지 않습니다...") and guidance blocks are completely removed.
- [x] Message submission resets `messageInput` to `""` and `attachedFileIds` to `[]` immediately on submit regardless of pass/fail status.
- [x] Log_Fixer recovery selects the recovered file in the viewer without auto-attaching it to ECHO tray.
- [x] Selecting corrupted/deleted files in `/Recycle_Bin/` enables `[LOG_FIXER로 데이터 복구]` and successfully recovers them.
- [x] Act 2 clear strictly transitions to Act 3 (`act-3`) and cannot skip to ending states before Act 3 evidence verification.
- [x] `npm run build` passes cleanly.
- [x] `git diff --check` passes cleanly.

## Review History

- 2026-08-10: Created feat-039 specification and verified implementation. Review agent approved.
