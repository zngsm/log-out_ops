# feat-036 Refine file explorer/viewer width ratio, translate all buttons to Korean, remove password hint text, expand and center-align emergency HUD, and remove ACT-1 ACTIVE label

## Status

- status: done
- type: feat
- priority: 53
- owner agent: dev-agent
- branch: `feat-036-refine-ui-ux`
- commit message: `feat-036 refine file explorer viewer ratio, translate buttons to Korean, remove password hints, expand center emergency HUD`

## Goal

Apply 5 UI/UX refinements based on Change-001 v3.0 specs:
1. Adjust file explorer panel width to ~190px (`flex: 0 0 190px`) and expand file viewer area (`flex: 1 1 0`).
2. Translate major button labels to Korean (`ATTACH TO ECHO` -> `ECHO에 증거 첨부`, `COPY PATH` -> `경로 복사`, `OPEN WITH LOG_FIXER` -> `LOG_FIXER로 데이터 복구`, `UNLOCK`/`OPEN` -> `해제`/`열기`, `CANCEL` -> `취소`, `SUBMIT` -> `증거 제출`, `START INVESTIGATION` -> `조사 시작`).
3. Completely remove locked file password hint text (`승무원 메일에서 발견된 직인 암호를 입력하십시오.`).
4. Expand emergency HUD size (`O₂ LEVEL`, `POWER GRID`, `REMAINING TIME`) and center-align it in the top header (`header-center-hud`).
5. Remove `ACT-1 ACTIVE` label from the left panel header (`<span className="panel-tag">{getActLabel(stage)} ACTIVE</span>`).

## Scope

- **File Explorer & Viewer Ratio Refinement**:
  - Set `.explorer-panel` width to ~190px (`flex: 0 0 190px`) and expand `.file-viewer` width (`flex: 1 1 0`) to maximize readability of log body text.
- **Complete Korean Button Translation**:
  - `ATTACH TO ECHO` -> `ECHO에 증거 첨부`
  - `COPY PATH` / `PATH COPIED` -> `경로 복사` / `경로 복사 완료`
  - `OPEN WITH LOG_FIXER` -> `LOG_FIXER로 데이터 복구`
  - `UNLOCK` / `OPEN` -> `해제` / `열기`
  - `CANCEL` -> `취소`
  - `SUBMIT` -> `증거 제출`
  - `START INVESTIGATION` -> `조사 시작`
- **Locked File Hint Text Removal**:
  - Remove `승무원 메일에서 발견된 직인 암호를 입력하십시오.` from password unlock modal.
- **Emergency HUD Expansion & Center Alignment**:
  - Expand font/badge sizes for `O₂ LEVEL`, `POWER GRID`, and `REMAINING TIME` HUD items and center-align them in top header (`header-center-hud`).
- **ACT-1 ACTIVE Label Removal**:
  - Remove `<span className="panel-tag">{getActLabel(stage)} ACTIVE</span>` from the left panel header.

## Dependencies

- before: `feat-035`
- after: human visual review / QA

## Acceptance Criteria

- [ ] `.explorer-panel` width is reduced to ~190px (`flex: 0 0 190px`) and `.file-viewer` width is expanded (`flex: 1 1 0`).
- [ ] All 7 target buttons and associated inline text are translated to Korean (`ECHO에 증거 첨부`, `경로 복사`/`경로 복사 완료`, `LOG_FIXER로 데이터 복구`, `해제`/`열기`, `취소`, `증거 제출`, `조사 시작`).
- [ ] Password hint text `승무원 메일에서 발견된 직인 암호를 입력하십시오.` is removed from the unlock modal.
- [ ] Emergency HUD badges and fonts are expanded and centered in header using `.header-center-hud`.
- [ ] `<span className="panel-tag">{getActLabel(stage)} ACTIVE</span>` label is removed from the left panel header.
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Review History

- 2026-08-10: Created task specification feat-036 for 5 UI/UX refinement requirements.

## Source References

- `project/changes/change-001.md#14`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/task_board.md`
