# feat-025 Replace guide-like copy with playable in-world content

## Status

- status: done
- type: feat
- priority: 40
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-025 replace guide like copy with playable in world content`

## Goal

Move the current build away from guide/spec language and toward playable game content using the DOCX source documents as the content authority.

## Scope

- Add more in-world logs, crew messages, system audits, life-support records, and Act 3 clue documents.
- Remove or hide player-facing production/QA wording from the file explorer and viewer.
- Completely remove developer meta text like `Available for act-2 evidence` upon Log Fixer completion (Q42).
- Completely remove `DIAGNOSTIC NOTE` button from file viewer (Q47).
- Make opening beat copy read like an unfolding scene rather than implementation direction.
- Keep Category A Act 1~3 deterministic clear path intact.

## Dependencies

- before: `qa-003`
- after: human play review

## Acceptance Criteria

- [x] Player-facing file rows no longer expose evidence role labels by default.
- [x] Source reference metadata and developer meta text (`Available for act-2 evidence`) are completely removed (Q42).
- [x] `DIAGNOSTIC NOTE` button in file viewer is completely removed (Q47).
- [x] Password and recovery hints are presented as in-world security/diagnostic messages.
- [x] Additional DOCX-derived files exist for lockdown audit, crew comms, O2 pressure, Act 3 rule hierarchy, and recycle-bin discovery.
- [x] Opening beat copy no longer says `placeholder`.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Implementation Notes

- Added:
  - `/Logs/LifeSupport/o2_low_power_budget.log`
  - `/Logs/Events/lockdown_audit.log`
  - `/Logs/Events/crew_comms_buffer.log`
  - `/Personnel/Engineer_Park/power_grid_maint.note`
  - `/System/Security/protocol_101.txt`
  - `/Recycle_Bin/recovery_manifest.log`
- Expanded existing sensor, email, and priority matrix content with stronger clue links.
- Reworded opening cutscene beats into in-world scene descriptions.
- Changed QA/debug labels to Hermes diagnostic labels.

## Validation

- `npm run build` passed.
- `git diff --check` passed.

## Delivery

- code repo commit: `feat-025 replace guide like copy with playable in world content`
- code repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-09 | dev-agent | todo -> in_progress | Started urgent content pass to remove guide-like copy |
| 2026-08-09 | dev-agent | in_progress -> done | Added in-world documents and hid production metadata from player-facing UI |

