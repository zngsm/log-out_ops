# feat-008 Add opening, ending, visual, and audio feedback

## Status

- status: blocked
- blocked by: Q2, Q3, and Q7 in `project/pm_questions.md`
- type: feat
- priority: 9
- owner agent: dev-agent
- branch: `feat-008-add-opening-ending-visual-and-audio-feedback`
- commit message: `feat-008 add opening ending visual and audio feedback`

## Goal

Add MVP-level atmosphere and feedback for opening, resource danger states, blackout, and ending.

## Scope

- Add lightweight opening presentation.
- Add visual feedback for Normal, Caution, Warning, Critical, and Blackout.
- Add ending presentation after successful Act 3.
- Add placeholder sound or WebAudio feedback if approved.

## Dependencies

- before: `feat-002`, `feat-003`, Q2, Q3, Q7
- after: `qa-001`

## Acceptance Criteria

- Scope matches human-confirmed visual direction.
- MVP does not accidentally require final 3D GLB or rigged hand assets unless explicitly approved.
- Ending implementation matches confirmed MVP ending scope.
- Visual/audio feedback improves readability and tension without blocking gameplay.
