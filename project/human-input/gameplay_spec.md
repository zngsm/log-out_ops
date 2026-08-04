# Gameplay Spec Template

## Core Loop

1. 플레이어는 파일 탐색기에서 로그, 이메일, 설정 파일 등을 읽고 AI ECHO의 오판 증거와 키워드를 찾는다.
2. 시스템은 플레이어가 제출한 파일과 텍스트를 파싱(파일 검증, 키워드 추출)하여 정답 여부를 판정하며, 오답 제출 시 예비 전력을 차감하고 산소 감소 속도를 가속한다.
3. 플레이어는 AI의 3단계 논리 방어선(Act 1 ➔ Act 2 ➔ Act 3)을 차례로 무너뜨려 통제실 문을 열고 탈출한다.

## Win / Lose

- 승리 조건: Act 3에서 AI ECHO의 최종 거부 논리 충돌을 유발하여 통제실 격리 문을 최종 해제하고 탈출에 성공한다.
- 실패 조건: 산소 농도가 0%에 도달하거나 전력 고갈 상태에서 산소가 모두 소모되어 사망한다.

## Resources

| resource | default | changes when | effect |
| --- | --- | --- | --- |
| oxygen | 100% | 시간이 지남에 따라 일방향 감소 (기본 60분 = 100%), 전력 감소 시 소모 배율 가속 (1.0x ~ 3.0x) | 0% 도달 시 게임 오버 (사망) |
| power | 100% | ECHO에게 오답/무관한 파일 제출 시 회당 15% 차감 | 구간별 산소 감소 속도 가속 및 UI 글리치/시스템 지연 발생 |

## Interaction Rules

| interaction | allowed when | blocked when | result |
| --- | --- | --- | --- |
| open file | 파일 탐색기 내 접근 가능한 폴더/파일 클릭 시 | 보안 폴더 암호 미입력 또는 복구 툴 미실행 시 | 파일 내용(로그, 설정, 이메일) 확인 |
| submit evidence | AI 대화창에 파일 첨부 및 텍스트 입력 시 | N/A | AI 파싱 실행 (성공 시 Act 진행 / 실패 시 전력 -15%) |
| run utility (Log_Fixer.exe) | /Utilities/ 폴더 진입 및 매뉴얼 수칙 확인 후 | 미해금 상태 또는 필수 조건 미충족 시 | 깨진 파일(quarantine_rules.conf 등) 정상 복구 |

## Progression Rules

| stage | player goal | required proof | success result | failure result |
| --- | --- | --- | --- | --- |
| act 1 | AI의 초기 오판(센서 오차) 입증 | sensor_calib.log 첨부 + (오차 OR 보정) 키워드 | 1단계 수칙 철회, Act 2 진입 | 전력 -15% 차감, 산소 소모 가속 |
| act 2 | 격리 규정 시한 만료 입증 | 복구된 quarantine_rules.conf 첨부 + (오프셋 OR 만료) 키워드 | 2단계 수칙 철회, Act 3 진입 | 전력 -15% 차감, 산소 소모 가속 |
| act 3 | AI의 최종 거부 논리 파괴 | Act 3 대응 증거 2개 동시 첨부 (예: auxiliary_capacitor.log + emergency_grid_switch.conf) | 통제실 문 최종 해제 및 승리 | 전력 -15% 차감, 산소 소모 가속 |

## Penalty Rules

| wrong action | penalty | stack behavior | feedback |
| --- | --- | --- | --- |
| 잘못된 파일 또는 무관한 텍스트 제출 | 예비 전력 15% 차감 | 전력 구간 하강에 따라 산소 소모 배율 중첩 가속 (1.0x ➔ 1.25x ➔ 1.5x ➔ 2.0x ➔ 3.0x) | 경고음, 전원 서지, 조명 색상 변경, ECHO 경고 대사 출력 |
| 전력 0% 달성 (블랙아웃) | 10초간 OS 모니터 강제 재부팅 | 재부팅 후 전력 10% 임시 복구, 산소 소모 2.0x 유지 | 화면 암전, 10초간 입력 불가 (시간은 계속 흘러감) |

## System States

| state | trigger | effect | exit condition |
| --- | --- | --- | --- |
| Normal | 전력 100% ~ 85% | 산소 소모 1.0x, OS 터미널 정상 작동, 쿨 블루 조명 | 전력 84% 이하 하강 시 |
| Caution | 전력 84% ~ 60% | 산소 소모 1.25x, 주황색 비상등 전환, 파일 열기 0.5초 지연 | 전력 59% 이하 하강 시 |
| Warning | 전력 59% ~ 30% | 산소 소모 1.5x, 붉은색 조명, 복구 툴 실행 시간 2배, 전자 노이즈 글리치 | 전력 29% 이하 하강 시 |
| Critical | 전력 29% ~ 1% | 산소 소모 2.0x, 화면 비네팅 암전, 마우스 커서 떨림, 주변 장비 전력 차단 | 전력 0% 도달 시 |
| Blackout | 전력 0% 도달 시 | 10초간 OS 모니터 강제 재부팅 (시간은 소모됨), 산소 소모 3.0x | 10초 경과 후 (전력 10% 임시 복구) |

## Open Gameplay Questions

- 아직 미정인 규칙: 10대 격리 카테고리의 회차별 시드(Seed) 동적 난수 생성 알고리즘 세부 설계
- 아직 미정인 규칙: 연속 3회 이상 실패 시 ECHO가 제공하는 역힌트 대사의 출력 타이밍 및 힌트 강도 밸런싱
- 아직 미정인 규칙: 다중 엔딩(Ending B: 전 승무원 구출, Ending C: 시스템 동귀어진)의 구체적 달성 조건 및 세부 텍스트 스크립트 작성
