# feat-028 Compact Terminal HUD And Explorer Layout

## Document Meta

- type: feat
- status: done
- owner: dev-agent
- priority: 43
- created: 2026-08-09
- completed: 2026-08-09

## User Request

게임 시작 후 컴퓨터 터미널 화면에서 상단 게임 상태 컴포넌트가 화면을 가리지 않게 하고, 파일 탐색기는 실제 파일 탐색기처럼 제한된 영역에 전체 경로/파일을 촘촘히 보여주며, 잠긴 파일 접근 시 비밀번호 팝업을 띄운다. ECHO 대화 제출 버튼이 하단에서 잘리지 않도록 입력 영역도 정리한다.

## Scope

- Move gameplay HUD from floating overlay behavior into the real terminal title/status bar layout.
- Compact resource/audio/ECHO status cards so they sit beside `LOG_OUT` instead of covering terminal panels.
- Rework file explorer density from large grouped cards into compact directory/file rows.
- Keep locked security files visible as discoverable entries, but open a password prompt when the player tries to access them.
- Replace inline security unlock form with modal-style password prompt.
- Hide player-facing scene-runtime debug card from the ECHO column to recover vertical space.
- Reduce ECHO chat/input padding and textarea height so the submit button remains visible inside the fixed terminal screen.

## Acceptance Criteria

- Desktop gameplay screen does not page-scroll; terminal panels remain internally scrollable.
- HUD cards are no longer `fixed` overlays and do not cover file viewer, explorer, or ECHO chat content.
- File explorer can show many directories/files in a compact explorer-like list.
- Locked `/System/Security` entries prompt for a password on click instead of disappearing or using an inline form.
- ECHO evidence form submit button is visible without relying on page scroll.
- Production build passes.

## Dependencies

- Previous: `feat-026`, `feat-027`
- Next: human visual review or QA follow-up bugs

## Implementation Notes

- Code commit: `feat-028 fix compact terminal layout`
- Verification: `npm run build`, `git diff --check`

## Status Log

- todo: layout issue confirmed from user screenshot.
- in_progress: HUD DOM placement, file explorer interaction, and ECHO form sizing updated.
- done: build passed and ops tracking updated.
