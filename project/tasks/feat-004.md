# feat-004 Build category A file system data

## Status

- status: todo
- type: feat
- priority: 4
- owner agent: dev-agent
- branch: `feat-004-build-category-a-file-system-data`
- commit message: `feat-004 build category a file system data`

## Goal

Create structured file system data for the Bio-hazard category A MVP scenario.

## Scope

- Define directories and files used by category A.
- Include Act 1 sensor evidence.
- Include Act 2 quarantine rule evidence.
- Include Act 3 candidate evidence as pending-confirmation data.
- Mark corrupted/locked/recoverable files where needed.

## Dependencies

- before: `feat-001`
- after: `chore-001`, `feat-005`, `feat-006`, `feat-007`

## Acceptance Criteria

- File data can be rendered by the explorer and viewer.
- Each file has stable id, path, title, content, and gameplay metadata.
- Content source references are traceable to `project/human-input`.
- Act 3 evidence ambiguity is not silently resolved by dev agent.
