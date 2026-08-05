# feat-011 Improve MVP player guidance and UX guardrails

## Status

- status: todo
- type: feat
- priority: 11
- owner agent: dev-agent
- branch: `feat-011-improve-mvp-player-guidance-and-ux-guardrails`
- commit message: `feat-011 improve mvp player guidance and ux guardrails`

## Goal

Make the deterministic MVP playable without external AI by guiding the player through file selection, evidence attachment, recovery, and Act progression without revealing full answers.

## Scope

- Add current Act objective copy near the ECHO panel or HUD.
- Show required interaction hints, not exact answers.
- Clarify that clicking a file attaches it as an evidence tag.
- Clarify when evidence is blocked because a file is locked or corrupted.
- Improve feedback after wrong submissions so the player understands whether the issue is file choice, recovery state, or explanation intent.
- Add soft-lock prevention hints for password/recovery flow.
- Do not implement external AI hint conversation.

## Dependencies

- before: `feat-005`, `feat-006`, `feat-008`
- after: `qa-001`

## Acceptance Criteria

- A first-time player can understand the next interaction without reading ops docs.
- Wrong submission feedback is actionable but does not reveal the complete solution.
- Recovery and password flow have visible guidance.
- The UI clearly distinguishes selected file, attached evidence, locked file, corrupted file, and recovered file.
- The implementation remains compatible with future `feat-007` external AI integration.
