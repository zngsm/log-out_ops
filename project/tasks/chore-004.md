# chore-004 Define final asset drop contract from DOCX references

## Status

- status: done
- type: chore
- priority: 38
- owner agent: pm-agent
- branch: `main`
- commit message: `chore-004 define final asset drop contract from docx references`

## Goal

Create a clear human-facing asset checklist so final art/audio can be dropped into the code repo without dev agents guessing filenames, specs, or usage timing.

## Scope

- Define required asset paths under `log-out/public/assets`.
- Cover 3D models, audio, UI icons, glitch overlays, and document-art references.
- For each asset, specify:
  - exact filename/path
  - format
  - recommended dimensions or technical spec
  - used scene/trigger
  - placeholder fallback behavior
- Keep specs compatible with Vite + React + R3F.

## Dependencies

- before: `feat-021`, `feat-024`
- after: `qa-003`, human asset production

## Acceptance Criteria

- [x] Asset checklist is understandable from a human/art-team perspective.
- [x] Every required visual/audio asset has a target path and fallback behavior.
- [x] Control-room GLB node naming expectations are documented.
- [x] Audio naming and trigger expectations are documented.
- [x] No final asset is treated as mandatory for dev build success.

## Output

- Created `project/final_asset_drop_contract.md`.

## Implementation Notes

- Documented exact `public/assets` drop paths for 3D models, UI/images, FX overlays, and audio.
- Added control-room GLB node expectations and player-hands animation clip expectations.
- Added scene trigger map so asset timing matches the DOCX opening/gameplay/ending flow.
- Documented placeholder fallback behavior for every required asset class.

## Validation

- `git diff --check` passed.

## Delivery

- ops repo commit: `chore-004 define final asset drop contract from docx references`
- ops repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-08 | pm-agent | todo -> in_progress | Started final asset contract after feat-024 |
| 2026-08-08 | pm-agent | in_progress -> done | Published final asset drop contract with paths, specs, triggers, and fallbacks |

## Source References

- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/human-input/asset_plan.md`
- `project/docx_content_conversion_plan.md`
