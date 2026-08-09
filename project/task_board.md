# Task Board

## Document Meta

- version: 0.6
- pm agent: codex
- date: 2026-08-06
- status: DOCX source phase 2 vertical slice planned

## Task Index

| priority | task id | type | title | status | owner agent | parallelizable | depends on | blocks | doc path |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | feat-001 | feat | Bootstrap Vite + React game project | done | dev-agent | no | none | feat-002, feat-003, feat-004, feat-009 | project/tasks/feat-001.md |
| 2 | feat-002 | feat | Build Hermes OS terminal shell | done | dev-agent | yes | feat-001 | feat-005, feat-006, feat-008 | project/tasks/feat-002.md |
| 3 | feat-003 | feat | Implement oxygen and power game state | done | dev-agent | yes | feat-001 | feat-005, qa-001, phase 2 feat-007 | project/tasks/feat-003.md |
| 4 | feat-004 | feat | Build category A file system data | done | dev-agent | yes | feat-001 | feat-005, feat-006, phase 2 feat-007 | project/tasks/feat-004.md |
| 5 | chore-001 | chore | Align content fixtures with planning docs | done | dev-agent | yes | feat-004 | feat-005, chore-002, phase 2 feat-007 | project/tasks/chore-001.md |
| 6 | feat-009 | feat | Build R3F spaceship computer scene | done | dev-agent | yes | feat-001 | feat-008 | project/tasks/feat-009.md |
| 7 | feat-005 | feat | Implement evidence attachment and act progression | done | dev-agent | no | feat-002, feat-003, feat-004 | feat-011, qa-001, phase 2 feat-007 | project/tasks/feat-005.md |
| 8 | feat-006 | feat | Implement Log Fixer recovery interaction | done | dev-agent | yes | feat-002, feat-004 | feat-011, qa-001, phase 2 feat-007 | project/tasks/feat-006.md |
| 9 | feat-010 | feat | Implement intro narrative sequence | done | dev-agent | no | feat-008 | qa-001 | project/tasks/feat-010.md |
| 10 | chore-002 | chore | Enrich MVP internal file contents | done | dev-agent | yes | chore-001, feat-005, feat-006 | qa-001 | project/tasks/chore-002.md |
| 11 | feat-011 | feat | Improve MVP player guidance and UX guardrails | done | dev-agent | yes | feat-005, feat-006, feat-008 | qa-001 | project/tasks/feat-011.md |
| 12 | qa-001 | chore | Run MVP scenario QA and create bug tickets | done | qa-agent | no | feat-003, feat-005, feat-006, feat-008, feat-010, chore-002, feat-011 | bug-001, bug-002 | project/tasks/qa-001.md |
| 13 | bug-001 | bug | Connect oxygen timer to active gameplay session | done | dev-agent | no | qa-001, feat-003 | MVP human review | project/tasks/bug-001.md |
| 14 | bug-002 | bug | Enforce blackout interaction lock in gameplay UI | done | dev-agent | no | qa-001, feat-003, feat-008 | MVP human review | project/tasks/bug-002.md |
| 15 | feat-007 | feat | Implement external AI ECHO rules for category A | deferred | dev-agent | no | Q11, pre-AI MVP QA | phase 2 AI work | project/tasks/feat-007.md |
| 16 | feat-012 | feat | Add DOCX-reference main menu and directed opening sequence | done | dev-agent | no | feat-008, feat-009, feat-010 | feat-013, feat-018, feat-019 | project/tasks/feat-012.md |
| 17 | feat-013 | feat | Add scene runtime and Act beat orchestration | done | dev-agent | no | feat-005, feat-010, feat-012 | feat-014, feat-020, qa-002 | project/tasks/feat-013.md |
| 18 | feat-014 | feat | Implement ECHO decision matrix and persona responses | done | dev-agent | yes | feat-005, feat-013 | feat-018, feat-020, qa-002 | project/tasks/feat-014.md |
| 19 | feat-015 | feat | Add resource pressure HUD and threshold effects | done | dev-agent | yes | feat-003, bug-001, bug-002 | feat-018, feat-019, qa-002 | project/tasks/feat-015.md |
| 20 | feat-016 | feat | Improve Hermes file explorer interaction fidelity | done | dev-agent | yes | feat-002, feat-011 | feat-017, qa-002 | project/tasks/feat-016.md |
| 21 | feat-017 | feat | Rework Log_Fixer into mini-program flow | done | dev-agent | yes | feat-006, feat-016 | qa-002 | project/tasks/feat-017.md |
| 22 | chore-003 | chore | Rewrite Category A content into diegetic clue layer | done | dev-agent | yes | feat-004, chore-002 | qa-002 | project/tasks/chore-003.md |
| 23 | feat-018 | feat | Add placeholder audio system and sound cues | done | dev-agent | yes | feat-012, feat-014, feat-015 | feat-020, qa-002 | project/tasks/feat-018.md |
| 24 | feat-019 | feat | Integrate DOCX-reference 3D control room with scene and resource state | done | dev-agent | yes | feat-009, feat-012, feat-015 | feat-020, qa-002 | project/tasks/feat-019.md |
| 25 | feat-020 | feat | Add directed Ending A and result panel | done | dev-agent | no | feat-013, feat-014, feat-018, feat-019 | qa-002 | project/tasks/feat-020.md |
| 26 | qa-002 | chore | Run original-source vertical slice QA | done | qa-agent | no | feat-012, feat-013, feat-014, feat-015, feat-016, feat-017, feat-018, feat-019, feat-020, chore-003 | phase 2 bug tasks | project/tasks/qa-002.md |
| 27 | bug-003 | bug | Fix menu zoom transition layout drift | done | dev-agent | no | qa-002 | human visual review | project/tasks/bug-003.md |
| 28 | bug-004 | bug | Align start scene with control room computer flow | done | dev-agent | no | bug-003 | human visual review | project/tasks/bug-004.md |
| 29 | bug-005 | bug | Hide 3D backdrop after terminal zoom | done | dev-agent | no | bug-004 | human visual review | project/tasks/bug-005.md |
| 30 | bug-006 | bug | Render Hermes OS inside zoomed terminal screen | done | dev-agent | no | bug-005 | human visual review | project/tasks/bug-006.md |
| 31 | bug-007 | bug | Restore compressed opening monitor entry flow | done | dev-agent | no | bug-006 | bug-008 | project/tasks/bug-007.md |
| 32 | bug-008 | bug | Align terminal screen zoom with monitor frame | done | dev-agent | no | bug-007 | bug-009 | project/tasks/bug-008.md |
| 33 | bug-009 | bug | Re-run original-source QA after visual flow fixes | done | qa-agent | no | bug-007, bug-008 | human visual review | project/tasks/bug-009.md |
| 34 | feat-021 | feat | Convert DOCX Category A logs into production game content | done | dev-agent | no | bug-009 | feat-022, feat-023, qa-003 | project/tasks/feat-021.md |
| 35 | feat-022 | feat | Implement DOCX-based ECHO argument flow | done | dev-agent | no | feat-021 | feat-023, qa-003, feat-007 | project/tasks/feat-022.md |
| 36 | feat-023 | feat | Add DOCX resource pressure feedback as gameplay feel | done | dev-agent | no | feat-021, feat-022 | qa-003 | project/tasks/feat-023.md |
| 37 | feat-024 | feat | Rebuild opening-to-terminal flow from visual DOCX | done | dev-agent | yes | bug-009 | qa-003 | project/tasks/feat-024.md |
| 38 | chore-004 | chore | Define final asset drop contract from DOCX references | done | pm-agent | yes | feat-021, feat-024 | qa-003, human asset production | project/tasks/chore-004.md |
| 39 | qa-003 | chore | Run DOCX-content vertical slice QA | done | qa-agent | no | feat-021, feat-022, feat-023, feat-024, chore-004 | human review | project/tasks/qa-003.md |
| 40 | feat-025 | feat | Replace guide-like copy with playable in-world content | done | dev-agent | no | qa-003 | human play review | project/tasks/feat-025.md |

## Parallel Work Notes

- `feat-002`, `feat-003`, `feat-004`, and `feat-009` can start after `feat-001` because they touch different layers: UI shell, game state, content data, and 3D scene.
- `chore-001` can run alongside implementation once `feat-004` defines the file data shape.
- `feat-006` can proceed before final ECHO wording if the recovery interaction contract is stable.
- `feat-007` is deferred to phase 2 because deterministic local ECHO rules are enough to validate the current MVP loop.
- `feat-010`, `chore-002`, and `feat-011` are pre-AI MVP reinforcement tasks that improve comprehension, content density, and playability.
- For phase 2, `project/phase_2_original_source_replan.md` and the original `LOG_OUT **.md` files are the source of truth. PM task docs must not override those documents unless a human answer explicitly says so.
- The DOCX files in `project/human-input` are now the preferred visual source because their embedded images/GIF preserve references that can break in markdown.
- `feat-012` and `feat-013` should run before most experience tasks because they define the menu/opening/scene skeleton.
- `feat-014`, `feat-015`, `feat-016`, and `chore-003` can proceed in parallel after their dependencies because they affect ECHO logic, resource pressure, file interaction, and content copy respectively.
- `feat-018` and `feat-019` should start after scene/resource direction is stable enough to wire audio and 3D state changes.

## Sequencing Notes

- Do not let dev agent decide unresolved planning conflicts independently.
- If a task depends on a question ID, PM must update `pm_questions.md` and this board after the human answer.
- QA can run before `feat-007` as long as it tests deterministic scripted ECHO behavior rather than external AI behavior.
- Phase 2 QA must cite original `LOG_OUT **.md` expectations, not only task acceptance criteria.
- For the next phase, `project/docx_content_conversion_plan.md` is the controlling bridge between the DOCX source documents and playable implementation tasks.
- The DOCX files are considered sufficient content source for Category A; dev agents should convert them into game files, ECHO rules, scene beats, and asset contracts instead of waiting for new prose.
- QA-003 passed the DOCX-content vertical slice with residual risks around final assets, pixel comparison, and browser click automation.
- `feat-025` is the urgent completion-day content pass: player-facing guide/spec language should be treated as a bug unless it is hidden behind diagnostic mode.
- Every dev task must update its task md status from `todo` to `in_progress` to `done`.
- Current dev workflow is latest `main` -> task-scoped implementation -> task-id commit message -> push directly to `main`; PR/branch flow is only used when the human explicitly asks for it.
