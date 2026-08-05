# feat-008 Add opening, ending, visual, and audio feedback

## Status

- status: todo
- type: feat
- priority: 10
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
- Add short blackout failure presentation for oxygen 0% or terminal failure.
- Respect debug mode cutscene skip.

## Dependencies

- before: `feat-002`, `feat-003`, `feat-009`
- after: `qa-001`

## Acceptance Criteria

- Scope matches human-confirmed visual direction: R3F spaceship/computer background, placeholder hands, 2D Hermes OS screen.
- MVP does not require final rigged hand assets.
- Ending implementation is Normal Ending A only.
- Visual/audio feedback improves readability and tension without blocking gameplay.
