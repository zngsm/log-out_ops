# chore-006 Harden GitHub Pages NPM Install Step

## Document Meta

- type: chore
- status: done
- owner: dev-agent
- priority: 65
- created: 2026-08-10
- completed: 2026-08-10

## User Report

GitHub Pages Actions 배포 중 `npm ci` 단계에서 `ECONNRESET` 네트워크 오류가 발생했다.

## Scope

- Add npm registry and fetch retry settings to the GitHub Pages workflow.
- Wrap `npm ci` in a 3-attempt retry loop.
- Use `npm ci --prefer-offline --no-audit` to reduce avoidable network work during CI.
- Preserve the existing build and Pages artifact deployment flow.

## Acceptance Criteria

- Workflow retries transient npm registry/network failures before failing.
- Build command remains `npm run build`.
- Pages artifact remains `dist`.
- Local production build passes.

## Dependencies

- Previous: `chore-005`
- Next: GitHub Actions rerun

## Implementation Notes

- Code commit: `chore-006 harden github pages npm install`
- Verification: `npm run build`, `git diff --check`

## Status Log

- todo: GitHub Actions `npm ci` failed with `ECONNRESET`.
- in_progress: npm retry configuration and install retry loop added.
- done: build passed and ops tracking updated.
