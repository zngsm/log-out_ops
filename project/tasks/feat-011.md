# feat-011 Improve MVP player guidance and UX guardrails

## Status

- status: done
- type: feat
- priority: 11
- owner agent: dev-agent
- branch: `feat-011-improve-mvp-player-guidance-and-ux-guardrails`
- commit message: `feat-011 improve mvp player guidance and ux guardrails`

## Goal

Make the deterministic MVP playable without external AI by guiding the player through file selection, evidence attachment, recovery, and Act progression without revealing full answers.

## Scope

- Add current Act objective copy near the ECHO panel or HUD (diegetic copy only).
- Completely remove `NEXT ACTION` banner/strip (Q40).
- Completely remove Tool manual security notes (Q35).
- Completely remove 'First objective' box and 'Open first file' button from `HOW TO PLAY` window (Q41).
- Show required interaction hints, not exact answers.
- Clarify that clicking a file attaches it as an evidence tag.
- Clarify when evidence is blocked because a file is locked or corrupted.
- Improve feedback after wrong submissions so the player understands whether the issue is file choice, recovery state, or explanation intent.
- Do not implement external AI hint conversation.

## Dependencies

- before: `feat-005`, `feat-006`, `feat-008`
- after: `qa-001`

## Acceptance Criteria

- [x] A first-time player can understand the next interaction without reading ops docs.
- [x] `NEXT ACTION` strip/bar is completely removed (Q40).
- [x] Tool manual security notes are completely removed (Q35).
- [x] 'First objective' box and 'Open first file' button in `HOW TO PLAY` window are completely removed (Q41).
- [x] Wrong submission feedback is actionable but does not reveal the complete solution.
- [x] Recovery and password flow have visible diegetic guidance.
- [x] The UI clearly distinguishes selected file, attached evidence, locked file, corrupted file, and recovered file.
- [x] The implementation remains compatible with future `feat-007` external AI integration.

## Implementation Notes

- Added current Act objective guidance in the HUD and ECHO panel.
- Added evidence attachment instructions and file state legend.
- Added explicit UI states for attached and recovered files while preserving selected/corrupted/locked states.
- Added submission result reason codes so the UI can distinguish wrong file set, unrecovered evidence, missing explanation intent, and accepted submissions.
- Added password/recovery soft-lock prevention hints around `/System/Security` and `Log_Fixer.exe`.

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- review-agent result: approved

## Pull Request Draft

- PR title: `FEAT-011 MVP 플레이어 가이드 및 UX 가드레일 개선`
- branch: `feat-011-improve-mvp-player-guidance-and-ux-guardrails`
- code commit: `c4bc480 feat-011 improve mvp player guidance and ux guardrails`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | MVP player guidance and UX guardrails implementation started from latest main |
| 2026-08-05 | review-agent | in_progress -> approved | Build and diff validation passed; no blocking findings |
| 2026-08-05 | dev-agent | approved -> done | Code branch pushed and ops task updated |
