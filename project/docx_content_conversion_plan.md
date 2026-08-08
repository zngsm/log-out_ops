# DOCX Content Conversion Plan

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-08
- status: ready for task execution
- purpose: Convert the `project/human-input` DOCX source documents into actual playable LOG_OUT game content rather than placeholder/example content.

## PM Judgment

The DOCX files are sufficient as the primary content source for the next implementation phase.

The current issue is not that the documents lack content. The issue is that prior tasks converted the documents into systems and simplified fixtures, but did not fully convert them into playable clue density, staged ECHO argumentation, and scene-level game flow.

## Source Documents

| source | role in implementation |
| --- | --- |
| `project/human-input/우주선 탈출게임 개요.docx` | world premise, 1-hour Act structure, ECHO logic, resource rules, Category A baseline |
| `project/human-input/우주선 탈출게임 로그 예시.docx` | concrete Category A file tree and exact file contents |
| `project/human-input/우주선 탈출 게임 로그 파일 구조.docx` | long-term file-system architecture, interaction rules, randomization model |
| `project/human-input/우주선 탈출 게임 AI 프롬프트 예시.docx` | ECHO persona, parser behavior, response format, prompt-injection handling |
| `project/human-input/LOG_OUT visual 복사본.docx` | menu/opening/terminal/resource UI/UX and visual sequence reference |

## Conversion Rule

Developers must not paste the DOCX prose directly into the UI as exposition.

Instead, convert each source into one of the following game objects:

- `file content`: readable in-world logs, emails, configs, JSON, manuals, corrupted files, recovered files
- `puzzle rule`: required evidence files, keyword groups, partial success rules, old evidence rules, failed attempt hints
- `scene beat`: opening timing, ECHO claim, Act transition, review lock, blackout, ending review
- `resource feedback`: delay, glitch, lighting, sound, blackout/reboot, O2 multiplier
- `asset contract`: path, filename, format, expected dimensions, placeholder fallback behavior

## Required Next Phase Outcome

The player should no longer feel like they are testing a file-submission UI.

The player should feel like they are:

- trapped in the Hermes control room
- reading believable ship records
- finding contradictions through deduction
- arguing against ECHO's procedural logic
- losing oxygen and power while making decisions
- reaching a directed Act 3 confrontation and door-release ending

## Next Task Set

| task id | type | title | source focus | expected result |
| --- | --- | --- | --- | --- |
| feat-021 | feat | Convert DOCX Category A logs into production game content | `로그 예시.docx`, `개요.docx` | Replace placeholder-like file copy with the concrete Category A tree and diegetic content from DOCX |
| feat-022 | feat | Implement DOCX-based ECHO argument flow | `AI 프롬프트 예시.docx`, `개요.docx` | ECHO behaves like a staged procedural opponent, not a static validator |
| feat-023 | feat | Add DOCX resource pressure feedback as gameplay feel | `개요.docx`, `visual 복사본.docx` | Power/O2 thresholds visibly and audibly affect play |
| feat-024 | feat | Rebuild opening-to-terminal flow from visual DOCX | `visual 복사본.docx` | Start scene, lockdown, monitor click, zoom, and terminal handoff match intended structure |
| chore-004 | chore | Define final asset drop contract from DOCX references | all DOCX sources | Human-facing asset checklist with paths, specs, placeholder fallbacks |
| qa-003 | chore | Run DOCX-content vertical slice QA | feat-021 through feat-024, chore-004 | Verify the result against DOCX sources rather than existing task assumptions |

## Implementation Priority

1. Run `feat-021` first because real game content depends on the concrete file tree and log text.
2. Run `feat-022` after `feat-021` so ECHO responses can reference the actual evidence files.
3. Run `feat-024` in parallel with `feat-022` if needed because it is mostly visual/scene-flow work.
4. Run `feat-023` after the main content loop is stable so pressure feedback is tuned around actual play.
5. Run `chore-004` before final art/audio requests to humans.
6. Run `qa-003` after all phase tasks are pushed to `main`.

## Non-Goals

- Do not implement all 10 categories in this phase.
- Do not implement external AI/API in this phase unless the human explicitly resumes `feat-007`.
- Do not require final-quality GLB/audio assets before the content loop works.
- Do not expose debug hints as production-facing file content.

