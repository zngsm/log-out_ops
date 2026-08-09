# feat-007 Integrate Cloudflare Worker NPC API for ECHO and Coworker Chat

## Status

- status: done
- type: feat
- priority: 9
- owner agent: dev-agent
- branch: `feat-007-integrate-cloudflare-worker-npc-api`
- commit message: `feat-007 integrate cloudflare worker npc api for echo and coworker chat`

## Goal

Cloudflare Worker 기반 Hermes NPC API(`https://royal-firefly-60c3.jwpark971219.workers.dev`)를 연동하여 ECHO 대화/증거 제출 및 동료(Coworker) 메신저에 외부 AI/LLM 기반 응답을 제공한다. 3초 타임아웃(`AbortController`) 및 네트워크 단절/에러 발생 시 100% 로컬 Fallback 안전장치를 가동하여 오프라인/장애 상황에서도 끊김 없는 플레이를 보장한다.

## Scope

- `src/types/npc.ts` 생성: `NpcRequestPayload`, `EchoNpcResponse`, `CoworkerNpcResponse`, `ApiErrorResponse` 타입 정의
- `src/api/npcApiClient.ts` 구현: `fetch` POST `https://royal-firefly-60c3.jwpark971219.workers.dev`, 3초 타임아웃 (`AbortController`), 네트워크 단절/타임아웃/예외 발생 시 100% 로컬 Fallback 반환 기능
- `WorkInterface.tsx` 동료 메신저 API 연동: `npcId: 'coworker'` 호출 및 응답 대기 시 로딩 타이핑 연출 적용
- `evidenceSubmission.ts` 및 `App.tsx` ECHO API 연동: `npcId: 'echo'`, `currentStage`, `history` 전달 및 응답 데이터의 `next_stage`, `door_unlocked`, `ending_b_triggered` 수신하여 스테이지 전이 및 게임 상태 반영
- 로컬 Fallback 데이터 및 예외 처리 안전장치 구현: 네트워크 단절 시 기존 deterministic local 로직으로 Fallback 수행

## Dependencies

- before: `feat-005`, `feat-033`, `feat-034`
- after: QA & production play

## Acceptance Criteria

- `src/types/npc.ts`에 `NpcRequestPayload`, `EchoNpcResponse`, `CoworkerNpcResponse`, `ApiErrorResponse` TypeScript 타입이 명확히 선언되어 있어야 한다.
- `src/api/npcApiClient.ts`는 Cloudflare Worker endpoint (`https://royal-firefly-60c3.jwpark971219.workers.dev`)로 POST 요청을 전달하며, 3초 이내 응답 미수신 시 요청을 중단하고 로컬 Fallback 응답을 반환해야 한다.
- 네트워크 단절, HTTP 에러, JSON 파싱 오류 등 예외 발생 시 100% 로컬 Fallback 대사/응답으로 대체되어 게임이 중단되거나 멈추지 않는다.
- `WorkInterface.tsx`에서 동료 메신저 대화 시 `npcId: 'coworker'`로 API를 호출하며, 응답 처리 중 로딩 타이핑 연출이 표시된다.
- `evidenceSubmission.ts` 및 `App.tsx`에서 ECHO 대화 및 증거 제출 시 `npcId: 'echo'`, `currentStage`, `history`를 전달하고, 수신된 `next_stage`, `door_unlocked`, `ending_b_triggered` 데이터로 스테이지 전환 및 통제실 문 해제/엔딩 상태를 올바르게 업데이트한다.

## PM Decision

2026-08-09부로 Cloudflare Worker Hermes NPC API 명세서 확정에 따라 `feat-007`을 `in_progress` 상태로 활성화. 외부 LLM API 연동과 함께 3초 타임아웃 및 100% 로컬 Fallback 안전장치를 필수로 구현하여 네트워크 연결 및 서버 장애와 무관하게 완전히 안정적인 플레이 루프를 제공하도록 확정.
