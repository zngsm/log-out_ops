# feat-031 Convert cutscene presentation to CSS/SVG 2D and set terminal zoom to 100% full screen

## Status

- status: done
- type: feat
- priority: 46
- owner agent: dev-agent
- branch: `feat-031-convert-cutscene-to-2d-and-full-screen-zoom`
- commit message: `feat-031 convert cutscene presentation to css svg 2d and set terminal zoom to 100% full screen`

## Goal

Apply Change-001 visual requirements and Q19 answer: replace 3D cutscene presentation with CSS / SVG based 2D in-game cutscene presentation (while keeping the R3F 3D main menu background), and set the terminal zoom-in ratio from 90% monitor frame to 100% Full Screen.

## Scope

- Maintain R3F 3D background model for main menu.
- Convert 3D cutscene beats to CSS / SVG based in-game 2D presentation (CSS transitions, SVG animations, 2D visual elements).
- On [게임 시작] (Play) click, perform smooth zoom-in transition to 100% Full Screen terminal monitor view.
- Remove 90% aspect ratio container padding/frame during gameplay terminal state.

## Dependencies

- before: `bug-009`, `feat-024`
- after: `feat-032`, `feat-033`, `feat-034`

## Acceptance Criteria

- [x] Main menu displays 3D spaceship control-room background.
- [x] Clicking [게임 시작] smoothly zooms camera/screen into terminal filling 100% of the viewport (Full Screen).
- [x] Cutscene and transition beats are rendered using CSS / SVG based in-game 2D presentation elements instead of 3D cutscenes.
- [x] Terminal view occupies full screen width and height without 90% margin cutoffs.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | requirements satisfied with no regression | closed |

## Source References

- `project/changes/change-001.md`
- `project/mvp_scope.md`
- `project/pm_questions.md#Q19`

