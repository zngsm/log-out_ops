# chore-005 Setup GitHub Pages Deployment

## Document Meta

- type: chore
- status: done
- owner: dev-agent
- priority: 64
- created: 2026-08-10
- completed: 2026-08-10

## User Request

GitHub Pages로 실제 배포할 수 있도록 설정한다.

## Scope

- Configure Vite `base` for repository Pages path `/log-out/`.
- Add GitHub Actions workflow for automatic build and GitHub Pages deployment from `main`.
- Use Node 20 and `npm ci`.
- Upload `dist/` as the Pages artifact.

## Acceptance Criteria

- `npm run build` succeeds with GitHub Pages base path.
- `.github/workflows/deploy.yml` deploys on `main` push.
- GitHub repo can use `Settings -> Pages -> Source -> GitHub Actions`.
- Production URL target is `https://zngsm.github.io/log-out/`.

## Dependencies

- Previous: `feat-001`
- Next: GitHub repository Pages setting must be set to GitHub Actions by human.

## Implementation Notes

- Code commit: `chore-005 setup github pages deployment`
- Verification: `npm run build`, `git diff --check`

## Status Log

- todo: user requested GitHub Pages deployment setup.
- in_progress: Vite base and GitHub Actions workflow added.
- done: build passed and ops tracking updated.
