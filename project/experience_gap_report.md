# Experience Gap Report

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-06
- status: analysis complete
- source planning docs:
  - `project/human-input/project_brief.md`
  - `project/human-input/gameplay_spec.md`
  - `project/human-input/scene_flow.md`
  - `project/human-input/direction_and_content.md`
  - `project/human-input/asset_plan.md`
  - `project/pm_questions.md`
  - `project/mvp_scope.md`
- implementation baseline:
  - code repo branch inspected: `bug-002-enforce-blackout-interaction-lock`
  - note: this branch includes latest main after `bug-001`; if `bug-002` is not merged yet, main will be slightly behind this analysis on blackout locking only

## Executive Summary

The current implementation satisfies much of the functional deterministic MVP: Hermes OS panels, Category A files, evidence attachment, Act 1-3 progression, resource state, Log_Fixer recovery, intro overlay, Normal Ending A, and basic guidance.

However, it does not yet satisfy the game experience described by the original planning intent. The implementation behaves like a compact evidence-checking prototype, while the source plan asks for a first-person SF mystery escape game with scene timing, escalating pressure, ECHO's staged logical defense, audiovisual feedback, and a stronger sense that the player is trapped inside the Hermes control room.

The main PM failure was translating the plan into feature tasks too mechanically. The task list captured "what systems exist" but not enough of "how each scene should feel, unfold, sound, pace, and teach the player."

## Current Implementation Snapshot

| area | current implementation | status |
| --- | --- | --- |
| OS layout | Top HUD, file explorer, file viewer, ECHO panel | partially aligned |
| 3D environment | R3F placeholder control room/computer backdrop | partially aligned |
| intro | 4-step skippable text overlay | partially aligned |
| Category A files | Act evidence plus several flavor/context files | partially aligned |
| evidence flow | deterministic file set + keyword validation | functional but shallow |
| Act progression | Act 1 -> Act 2 -> Act 3 -> ending-ready | functional |
| ECHO behavior | static success/failure messages | under-implemented |
| oxygen/power | deterministic model; timer now connected in bug-001 | mostly functional |
| blackout | visual and interaction lock in bug-002 branch | mostly functional |
| ending | Normal Ending A overlay | minimal |
| sound | no meaningful audio system | missing |
| scene timing | no real 60-minute act pacing or scene-level locks except intro/blackout | missing |

## Original Intent vs Current Result

### 1. Core Fantasy Is Under-Delivered

Original intent:
The player should feel like an AI management crew member trapped in the Hermes control room, under oxygen pressure, trying to dismantle ECHO's faulty but formally logical quarantine decision.

Current result:
The player mostly feels like they are operating a themed file explorer and submitting tags to pass deterministic checks.

Gap:
The world state is explained, but it is not sufficiently dramatized. There is limited sense of the ship, crew panic, door lock, ECHO's authority, or the player being physically trapped.

Why this happened:
PM tasks prioritized UI and rules over the embodied scenario: no task explicitly required "make the player feel trapped" or "make ECHO's lockdown feel procedurally authoritative."

### 2. Scene Flow Was Flattened Into UI States

Original intent:
`scene_flow.md` defines `SCENE_000_OPENING`, `SCENE_A_ACT1`, `SCENE_A_ACT2`, `SCENE_A_ACT3`, and `SCENE_004_END_A` with entry/exit conditions, expected durations, player learning goals, input lock moments, and ECHO lines.

Current result:
The app has broad React states: opening overlay, current Act, selected file, recovered file, ending-ready. There is no explicit scene model.

Gap:
Act transitions feel like state changes, not directed scenes. There is no ECHO response timing lock, no Act intro beat, no Act success beat, and no "ECHO defense line" before each puzzle.

Why this matters:
For this game, scene structure is not decorative. It is how the player understands stakes, progression, and escalation.

### 3. ECHO's Logical Defense Is Too Generic

Original intent:
ECHO should speak in a cold, procedural, regulation-driven tone and explain specific logical barriers:

- Act 1: bio-scan sensor validity
- Act 2: quarantine rule and time offset
- Act 3: final refusal based on survival probability/resource allocation or confirmed priority contradiction

Current result:
ECHO mostly returns generic validation messages such as "증거 검증 완료" or "증거 파일 조합이 아닙니다."

Gap:
The player does not experience ECHO as an intelligent, stubborn, rule-bound system. The "논리 파쇄" fantasy is weakened because ECHO's argument is not staged strongly enough before it is defeated.

Specific missing items:

- D-002 and D-003 are not used in the intro as written.
- D-007, D-012, D-013, D-014, D-020 are not faithfully used as Act transition dialogue.
- Partial success, old evidence resubmission, repeated wrong-answer hint behavior are not implemented.
- ECHO response timing is instantaneous and not treated as a scene moment.

### 4. Act 3 Intent Drifted

Original intent conflict:
The structured `scene_flow.md` defines Category A Act 3 as a resource allocation dilemma solved by:

- `/Hardware/Power/auxiliary_capacitor.log`
- `/System/Power/emergency_grid_switch.conf`

The PM questions later resolved Category A MVP Act 3 to the original rough-plan pair:

- `ai_priority_matrix.json`
- `deleted_override.txt`

Current result:
The implementation uses `ai_priority_matrix.json` + `deleted_override.txt`.

Gap:
This is not necessarily wrong because Q4 resolved it, but the experience impact was under-analyzed. The implemented Act 3 became "policy priority contradiction" rather than "door opening consumes power and must be solved with independent emergency power."

Consequence:
The final puzzle loses the concrete physical stakes of opening a door under low power. It becomes abstract policy logic, which feels less like an escape-room climax.

PM correction needed:
Either confirm that Act 3 should remain policy-priority based, or restore the power-route dilemma with new files. This is a human design decision, not something dev agent should infer.

### 5. Resource Pressure Exists Mechanically But Not Dramatically

Original intent:
Oxygen and power should create time pressure, escalating lighting, input delays, glitches, blackout silence, reboot, warning SFX, and failure dread.

Current result:
Resource values are displayed and affect some visual class states. bug-001 connects oxygen drain; bug-002 locks interaction during blackout. But Caution/Warning/Critical do not yet change interaction timing, sound, cursor, or scene behavior in the planned way.

Missing:

- 60-minute normal mode is implemented in model but the app defaults to debug mode with no mode selection.
- No visible elapsed time/session countdown.
- No oxygen drain multiplier display.
- No file-open 0.5s lag in Caution.
- No doubled Log_Fixer execution time in Warning.
- No cursor shake in Critical.
- No blackout shutdown/reboot sequence with 10 seconds of silence.
- No wrong submission surge moment beyond static feedback.

### 6. Audio Direction Is Almost Entirely Missing

Original intent:
The plan gives a strong soundscape direction: ship hum, low-frequency ambient tension, warning siren, door clunk, ECHO ping, typing, success chime, surge, blackout silence, reboot SFX.

Current result:
There is no meaningful audio system or placeholder WebAudio feedback.

Gap:
This is one of the biggest reasons the result does not feel like a finished game. The source plan relies on sound to communicate pressure and physical environment.

### 7. 3D Environment Is Present But Not Integrated Into Gameplay Beats

Original intent:
The 3D control room and computer should support first-person immersion, lighting changes, monitor focus, and emergency state transitions.

Current result:
The R3F scene is a static placeholder backdrop with basic meshes and lights. It does not respond materially to Act changes, power states, blackout, or ending.

Gap:
The scene is technically present but not dramaturgically active. It does not sell "Hermes control room" beyond an atmospheric background.

### 8. File Content Helps, But Discovery Is Too Direct

Original intent:
Core fun includes reading logs, identifying contradictions, solving password/recovery/offest puzzles, and assembling evidence.

Current result:
The files include useful `PLAYER NOTE` hints and the UI objective often tells the player what category of evidence is needed.

Gap:
The current version risks becoming guided checklist play rather than investigation. Several files directly say whether they are useful or not, which helps QA but weakens the puzzle fantasy.

PM correction needed:
Separate debug-friendly hints from production player-facing copy. The current content should be rewritten into:

- diegetic logs only
- optional hint layer
- QA/debug notes hidden behind debug mode

### 9. The AI/Free-Text Design Was Deferred Too Aggressively

Original intent:
The human answer to Q5 says external AI/API integration is expected, and Q8 says the player can use free-text conversation to get hints while evidence is judged through keywords and tags.

Current result:
External AI is deferred to phase 2, and the ECHO panel only handles evidence submission, not actual hint conversation.

Gap:
The MVP can function without AI, but the intended experience of arguing with ECHO is not yet there. This is another reason the game feels thinner than planned.

PM correction needed:
If AI remains deferred, the deterministic MVP needs a richer scripted ECHO conversation system to approximate that design. Otherwise the player is not "debating" ECHO, only submitting forms.

## PM Mistakes In Prior Task Definition

| mistake | impact |
| --- | --- |
| Converted design intent into feature checklist too early | Tasks delivered systems but not game feel |
| Treated "MVP" as "minimum mechanics" instead of "minimum complete experience" | Current build feels like prototype despite many systems |
| Did not create scene-directing tasks before implementation | Intro, Act transitions, ECHO response timing, and ending feel under-directed |
| Did not preserve the Act 3 experience tradeoff when resolving evidence conflict | Final puzzle lost physical resource/door-opening stakes |
| Deferred AI without replacing it with richer scripted interaction | ECHO lacks presence |
| Accepted placeholder assets without requiring placeholder behavior | Visual/audio assets exist as atmosphere, not feedback language |
| Did not distinguish debug copy from player-facing diegetic copy | Some content over-explains rather than invites deduction |

## Priority Gap List

| priority | gap | severity | recommended next step |
| --- | --- | --- | --- |
| P0 | No explicit scene state/directing layer | high | Add scene runtime model and scene transition specs |
| P0 | ECHO dialogue lacks staged logical defense | high | Implement scripted ECHO scene dialogue and response timing |
| P0 | Act 3 climax lacks confirmed intended direction | high | Ask human to choose policy contradiction vs power-route dilemma |
| P1 | Audio/soundscape missing | high | Add placeholder WebAudio ambience/SFX plan and implementation |
| P1 | Resource pressure not dramatized enough | medium-high | Add countdown, multiplier display, surge/reboot/critical feedback |
| P1 | 3D scene does not react to gameplay | medium-high | Tie lights/camera/monitor intensity to power/Act state |
| P1 | Logs over-explain via player notes | medium | Rewrite content into diegetic layer + optional hint layer |
| P2 | External AI/free-text conversation deferred | medium | Either resume feat-007 or build deterministic scripted hint parser |
| P2 | Ending is too minimal | medium | Add 10-second Ending A scene and result panel |

## Required Human Clarifications

### Q12. Act 3 Final Puzzle Direction

Which Act 3 direction should become the canonical MVP experience?

- Option A: keep `ai_priority_matrix.json` + `deleted_override.txt`, focusing on ECHO's priority-rule contradiction.
- Option B: restore `auxiliary_capacitor.log` + `emergency_grid_switch.conf`, focusing on the physical resource/door-opening dilemma.
- Option C: combine both, where ECHO first refuses due to power risk, then the player must prove both emergency power availability and authority/priority override.

PM recommendation: Option C is strongest for the original game fantasy, but it increases content and implementation scope.

### Q13. MVP Experience Bar

Should the next milestone target "mechanically playable MVP" or "first vertical slice that feels like the intended game"?

PM recommendation: switch to "first vertical slice" before adding more features.

### Q14. Hint Exposure

Should `PLAYER NOTE` style direct hints remain visible in files for MVP, or move behind a debug/hint toggle?

PM recommendation: move them behind a hint/debug layer. Keep diegetic logs clean for player deduction.

### Q15. AI Timing

Should external AI be resumed now, or should the team first build a scripted ECHO conversation layer that approximates the intended experience without API dependency?

PM recommendation: build scripted ECHO first, then use AI later to enrich non-critical hint conversation.

## Recommended Re-Planning

Before more feature work, PM should create a new milestone named `M8 Experience Realignment Vertical Slice`.

Recommended tasks:

| task id | type | title | purpose |
| --- | --- | --- | --- |
| feat-012 | feat | Add scene runtime and Act beat orchestration | Represent Act 0-4 as explicit scenes with entry/exit and input lock rules |
| chore-003 | chore | Rewrite Category A content into diegetic clue layer | Remove over-direct player notes from production copy and preserve optional debug hints |
| feat-013 | feat | Implement scripted ECHO defense dialogue | Use planning dialogue IDs and staged logical refusal/partial success responses |
| feat-014 | feat | Add resource pressure presentation | Countdown, multiplier, surge, reboot, critical feedback, and planned delays |
| feat-015 | feat | Add placeholder audio feedback system | Ship hum, ECHO ping, wrong/success SFX, blackout silence/reboot |
| feat-016 | feat | Integrate 3D scene with power and scene state | Lighting/camera/monitor state changes by Act and resource state |
| feat-017 | feat | Rework Ending A into directed scene | 10-second door release sequence and result panel |
| pm-002 | chore | Resolve Act 3 canonical direction | Human answer required for Q12 |

## PM Conclusion

The current build is a useful technical foundation, but it should not be treated as the intended game experience. It is closer to a playable systems prototype.

The next PM cycle should stop adding isolated features and instead realign the vertical slice around scene direction, ECHO presence, resource drama, and diegetic clue discovery.
