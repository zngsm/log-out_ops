# feat-030 Improve ECHO Chat Readability

## Document Meta

- type: feat
- status: done
- owner: dev-agent
- priority: 45
- created: 2026-08-09
- completed: 2026-08-09

## User Request

우측 채팅 화면이 어색하고, 채팅 히스토리와 내가 올린 내용, 그에 대한 ECHO 답변을 정상적으로 확인하기 어렵다.

## Scope

- Rework ECHO message history into chat-style bubbles.
- Align player messages to the right and ECHO/system messages to the left.
- Add message metadata so the newest answer and previous history are easier to scan.
- Add automatic scroll-to-latest behavior when new chat messages arrive.
- Split the composer into response header, evidence tray, text input, and send action.
- Rename submit action to `SEND TO ECHO` for clearer intent.
- Completely remove the log file source text `<dt>출처</dt>` (`project/human-input/...`) item from the bottom of file viewer (Q28 user feedback).
- Unify margin spacing between file title (`h2`) and `[ATTACH TO ECHO]` / `[COPY PATH]` button bar (`.context-action-bar`) (Q28 user feedback).

## Acceptance Criteria

- Player can distinguish submitted messages from ECHO and SYSTEM responses.
- Chat history remains scrollable inside the fixed terminal screen.
- New responses scroll into view automatically.
- Attached evidence is visibly associated with the message composer.
- File viewer bottom `<dt>출처</dt>` source text is completely removed.
- Margin spacing between file title (`h2`) and action buttons bar (`.context-action-bar`) is visually unified.
- Production build passes.

## Dependencies

- Previous: `feat-029`
- Next: human play review or QA follow-up bugs

## Implementation Notes

- Code commit: `feat-030 improve echo chat readability`
- Verification: `npm run build`, `git diff --check`

## Status Log

- todo: user reported right-side chat flow is difficult to read.
- in_progress: message bubble layout, composer structure, and auto-scroll added.
- done: build passed and ops tracking updated.
