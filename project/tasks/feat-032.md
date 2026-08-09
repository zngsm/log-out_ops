# feat-032 Implement Company Intranet opening screen with masked login form and clock-in button

## Status

- status: todo
- type: feat
- priority: 47
- owner agent: dev-agent
- branch: `feat-032-implement-company-intranet-opening-screen`
- commit message: `feat-032 implement company intranet opening screen with masked login form and clock-in button`

## Goal

Apply Change-001 opening requirement and Q20 answer: render a company intranet landing screen immediately after terminal zoom-in, presenting a pre-filled read-only login form (Username: `woojoo.kim`, Password: `**********`), displaying player character profile, and placing a [출근] (Clock-in) button to transition into the work phase.

## Scope

- Render Hermes Company Intranet landing page upon terminal zoom transition.
- Implement pre-filled read-only login form (player interaction/editing locked):
  - Username: `woojoo.kim`
  - Password: `**********` (10-character masking)
- Convey character information subtly within intranet headers/user card:
  - Name: '김우주' (Kim Wooju)
  - Role: '우주 자원 채굴선 헤르메스호 승무원 및 관리 AI ECHO 담당자' (Crew Member & AI ECHO Administrator)
- Place prominent [출근] (Clock-in) button on the intranet UI alongside/below the login form.
- On [출근] click, trigger state transition to the 2-split work interface (Desktop UI + ECHO chat).

## Dependencies

- before: `feat-031`
- after: `feat-033`, `feat-034`

## Acceptance Criteria

- [ ] Intranet landing page renders immediately after 100% full screen terminal transition.
- [ ] Login form displays pre-filled read-only Username `woojoo.kim` and Password `**********` (read-only / uneditable by player).
- [ ] Character profile ('김우주', AI ECHO 담당자) is subtly visible on the intranet screen.
- [ ] [출근] button is clearly positioned and interactive.
- [ ] Clicking [출근] transitions the UI into the dual-panel work interface.
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Source References

- `project/changes/change-001.md`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/pm_questions.md#Q20`

