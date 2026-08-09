# feat-032 Implement diegetic company intranet landing screen with pre-filled login form and clock-in button

## Status

- status: done
- type: feat
- priority: 47
- owner agent: dev-agent
- branch: `feat-032-implement-company-intranet-opening-screen`
- commit message: `feat-032 implement company intranet opening screen with masked login form and clock-in button`

## Goal

Apply Change-001 opening requirement and user feedback: render a company intranet landing screen immediately after terminal zoom-in, presenting a natural pre-filled login form (Username: `woojoo.kim`, Password: `**********`) with all developer/system meta text completely removed (`🔒 READ-ONLY` mark text, "시스템 자동 인증이 완료되었습니다. 계정 정보는 보안 정책에 의해 수정 불가능한 읽기 전용 상태입니다." text, and [출근] button sub-label "Clock-in :: 2분할 업무 화면 진입"). Convey character profile ('김우주') and place a simple diegetic [출근] button to transition into the workstation interface.

## Scope

- Render Hermes Company Intranet landing page upon terminal zoom transition.
- Implement pre-filled login form with zero developer/meta text:
  - Remove `🔒 READ-ONLY` mark text on login form.
  - Remove "시스템 자동 인증이 완료되었습니다. 계정 정보는 보안 정책에 의해 수정 불가능한 읽기 전용 상태입니다." text.
  - Remove [출근] button bottom sub-label "Clock-in :: 2분할 업무 화면 진입".
  - Render as a clean, natural intranet login form.
  - Username: `woojoo.kim`
  - Password: `**********` (10-character masking)
- Convey character information subtly within diegetic intranet UI:
  - Name: '김우주' (Kim Wooju)
  - Role: '우주 자원 채굴선 헤르메스호 승무원 및 관리 AI ECHO 담당자'
- Place prominent [출근] button using purely diegetic text (no "Clock-in :: 2분할 업무 화면 진입" meta text).
- On [출근] click, trigger state transition to the diegetic Workstation interface (Desktop + ECHO chat).

## Dependencies

- before: `feat-031`
- after: `feat-033`, `feat-034`

## Acceptance Criteria

- [x] Intranet landing page renders immediately after 100% full screen terminal transition.
- [x] Login form displays pre-filled Username `woojoo.kim` and Password `**********` with zero meta text (`🔒 READ-ONLY` mark, "시스템 자동 인증이 완료되었습니다..." removed).
- [x] Character profile ('김우주', AI ECHO 담당자) is subtly visible on the intranet screen.
- [x] [출근] button uses purely diegetic copy without meta sub-label ("Clock-in :: 2분할 업무 화면 진입" removed).
- [x] Clicking [출근] transitions the UI into the diegetic workstation UI.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Review History

- Date: 2026-08-09
- Reviewer: review_agent
- Result: APPROVED
- Summary: All acceptance criteria met. Company Intranet landing page rendered immediately after terminal zoom-in transition with read-only masked login form (Username: woojoo.kim, Password: **********), character profile ('김우주', AI ECHO 담당자), and interactive [출근] (Clock-in) button transitioning to the 2-split work interface (Desktop Workstation + ECHO chat). Build and git diff check passed cleanly.

## Source References

- `project/changes/change-001.md`
- `project/mvp_scope.md`
- `project/pm_analysis.md`
- `project/pm_questions.md#Q20`

