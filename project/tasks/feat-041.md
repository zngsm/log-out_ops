# feat-041 Implement 4 detail refinements (coworker lunch copy refinement, Power Surge Korean popup & 2s duration, pause button in HUD, and pause modal with 8px blur & timer freeze)

## Status

- status: done
- type: feat
- priority: 58
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-041 implement 4 detail refinements for coworker lunch copy, power surge korean popup, pause button and pause modal with 8px blur and timer freeze`

## Goal

Implement the four user-requested detail refinements across gameplay copy, power surge warning feedback, terminal HUD control, and game pause functionality.

## Scope

- 1. **Colleague Messenger Lunch Copy Refinement**: Refine the first question copy in the coworker messenger popup/app UI from `"오늘 점심 메뉴 뭐먹을래?"` to `"우주씨, 오늘 점심 뭐 드실래요?"`.
- 2. **Power Surge Warning Popup Korean Translation & 2-Second Duration Increase**: Increase the duration of the Power Surge alert popup triggered on wrong submission to 2 seconds (2000ms), and translate the title to `"전력 서지 경고"` and message to `"ECHO 경고: 잘못된 절차 주장은 헤르메스 전력 라인을 불안정하게 만듭니다."`.
- 3. **Terminal HUD Pause Button**: Add a pause (`⏸️`) button inside the main terminal HUD header status area.
- 4. **Pause Modal & Timer/Oxygen Freeze**: Clicking the pause (`⏸️`) button freezes the O₂ decay and remaining time countdown timers, applies an 8px block blur (`backdrop-filter: blur(8px)`) across the screen, displays a large `[PAUSED]` text at center with a slightly smaller `[RESUME]` button beneath it, and clicking `[RESUME]` unblurs the screen and resumes gameplay timers.

## Dependencies

- before: `feat-039`, `feat-040`
- after: human visual review

## Acceptance Criteria

- [x] Colleague messenger first question copy is updated to `"우주씨, 오늘 점심 뭐 드실래요?"`.
- [x] Wrong submission Power Surge popup stays visible for 2 seconds (2000ms) with Korean title `"전력 서지 경고"` and message `"ECHO 경고: 잘못된 절차 주장은 헤르메스 전력 라인을 불안정하게 만듭니다."`.
- [x] Pause button (`⏸️`) is rendered in the terminal HUD header area.
- [x] Clicking pause (`⏸️`) stops O₂ and time countdown timers, applies `backdrop-filter: blur(8px)`, renders centered `[PAUSED]` text and `[RESUME]` button, and clicking `[RESUME]` resumes gameplay and removes blur.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-10 | pm-agent | todo -> in_progress | Defined task for 4 detail refinements |
| 2026-08-10 | pm-agent | in_progress -> done | Updated specifications across PM operational docs and created feat-041.md |
| 2026-08-10 | dev-agent | in_progress -> done | Implemented 4 detail refinements, verified build & diff, obtained review_agent approval |

