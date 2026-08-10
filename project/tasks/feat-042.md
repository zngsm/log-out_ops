# feat-042 Implement 4 UI/UX and input submission refinements (ECHO 186-day guide copy deletion, ECHO textarea Enter key submission handler, SCENE LOCK popup deletion, and Power Surge popup 4-second duration increase)

## Status

- status: done
- type: feat
- priority: 59
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-042 remove 186-day guide copy, add enter key submission to echo textarea, remove scene lock popup, and extend power surge popup to 4s`

## Goal

Implement the four user-requested UI/UX and input submission refinements across ECHO chat guide copy, keyboard input handling, scene locking feedback, and power surge warning duration.

## Scope

- 1. **ECHO Input 186-Day Guide Copy Deletion**: Completely delete the guide text `오른쪽 ECHO 입력창에 '186일 미보정'과 '센서 보정 오차'를 짧게 적고 증거 제출을 하세요.` from the ECHO chat input panel / guidance UI.
- 2. **ECHO Textarea Enter Key Submission Handler**: Bind an `onKeyDown` key handler to the ECHO input textarea so that pressing Enter (excluding Shift+Enter) immediately triggers evidence submission (`[증거 제출]`). Shift+Enter retains default newline behavior.
- 3. **SCENE LOCK Popup Deletion**: Completely remove the `[SCENE LOCK]` guidance feedback popup rendered during evidence review and scene transitions. (Retain only the unique Center Modal alert card during 0% power blackout).
- 4. **Power Surge Warning Popup 4-Second Duration Increase**: Increase the display duration of the wrong submission `[전력 서지 경고]` warning popup from 2 seconds (2000ms) to 4 seconds (4000ms).

## Dependencies

- before: `feat-039`, `feat-040`, `feat-041`
- after: human visual review

## Acceptance Criteria

- [x] ECHO input guide text `오른쪽 ECHO 입력창에 '186일 미보정'과 '센서 보정 오차'를 짧게 적고 증거 제출을 하세요.` is completely deleted.
- [x] Pressing Enter (without Shift) in the ECHO input textarea immediately triggers `[증거 제출]`, while Shift+Enter inserts a newline.
- [x] The `[SCENE LOCK]` feedback popup is completely removed during submission review and scene transitions.
- [x] The wrong submission `[전력 서지 경고]` popup remains visible for 4 seconds (4000ms).
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-10 | pm-agent | todo -> in_progress | Defined task for 4 UI/UX and input submission refinements |
| 2026-08-10 | dev-agent | todo -> in_progress | Started implementation for 4 UI/UX and input submission refinements |
| 2026-08-10 | dev-agent | in_progress -> done | Implemented 4 UI/UX and input submission refinements, verified build & diff, obtained review_agent approval |

