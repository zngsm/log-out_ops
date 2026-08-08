# chore-004 Define final asset drop contract from DOCX references

## Status

- status: todo
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

- [ ] Asset checklist is understandable from a human/art-team perspective.
- [ ] Every required visual/audio asset has a target path and fallback behavior.
- [ ] Control-room GLB node naming expectations are documented.
- [ ] Audio naming and trigger expectations are documented.
- [ ] No final asset is treated as mandatory for dev build success.

## Source References

- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/human-input/asset_plan.md`
- `project/docx_content_conversion_plan.md`

