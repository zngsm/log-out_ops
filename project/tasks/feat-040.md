# feat-040 Refine 4 log file texts (sensor_diagram, crew_comms_buffer, email_chain_july, tool_manual)

## Status

- status: done
- type: feat
- priority: 57
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-040 refine 4 log file texts for sensor_diagram, crew_comms_buffer, email_chain_july, and tool_manual`

## Goal

Refine the text contents of four Category A log files (`sensor_diagram.png`/`sensor_diagram.txt`, `crew_comms_buffer.log`, `email_chain_july.txt`, and `tool_manual.txt`) according to explicit user requirements to remove non-diegetic notes, outdated drag-and-drop instructions, and generic speaker labels.

## Scope

- 1. `sensor_diagram.png` (sensor_diagram.txt): Completely remove the bottom note `※ 이 도면은 SENSOR-BIO-04가 ECHO_SEC201_AUTO에 직접 연결된 유일한 열 감지 헤드임을 나타냅니다.`
- 2. `crew_comms_buffer.log`: Completely change speaker labels from generic letters (A, B, C) to diegetic crew names (`박진수 (엔지니어)`, `이민아 (통신관)`, `최성현 (보안관)`).
- 3. `email_chain_july.txt`: Completely remove the bottom note `--- 이전 답장 / 김 박사 --- 이 문제가 근무 중 발생하면 김우주가 모듈 #04에 가장 먼저 갇힐 겁니다. 운영 인력이 찾을 수 있을 만큼은 눈에 띄되, 터미널 배너에는 보이지 않는 곳에 코드를 남겨 주세요.`
- 4. `tool_manual.txt`: Change the tool guidance text from `...해당 파일을 드래그하여 드롭하세요.` to match actual gameplay interaction: `텍스트 파일 열람 시 #404_CORRUPTED 표시가 뜨면 파일 뷰어 상단의 [LOG_FIXER로 데이터 복구] 버튼을 클릭하세요.`

## Dependencies

- before: `feat-039`
- after: human visual review

## Acceptance Criteria

- [x] `sensor_diagram.png` / `sensor_diagram.txt` bottom note `※ 이 도면은 SENSOR-BIO-04가 ECHO_SEC201_AUTO에 직접 연결된 유일한 열 감지 헤드임을 나타냅니다.` is completely deleted.
- [x] `crew_comms_buffer.log` speakers are completely converted from A, B, C to `박진수 (엔지니어)`, `이민아 (통신관)`, `최성현 (보안관)`.
- [x] `email_chain_july.txt` bottom previous reply note `--- 이전 답장 / 김 박사 --- 이 문제가 근무 중 발생하면 김우주가 모듈 #04에 가장 먼저 갇힐 겁니다. 운영 인력이 찾을 수 있을 만큼은 눈에 띄되, 터미널 배너에는 보이지 않는 곳에 코드를 남겨 주세요.` is completely deleted.
- [x] `tool_manual.txt` drag-and-drop text is replaced with `텍스트 파일 열람 시 #404_CORRUPTED 표시가 뜨면 파일 뷰어 상단의 [LOG_FIXER로 데이터 복구] 버튼을 클릭하세요.`
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-10 | pm-agent | todo -> in_progress | Defined task for refining 4 log file texts |
| 2026-08-10 | pm-agent | in_progress -> done | Updated specifications across PM operational docs |
| 2026-08-10 | dev-agent | in_progress -> done | Completed log-out code changes and review_agent approval |
