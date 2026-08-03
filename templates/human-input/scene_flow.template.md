# Scene Flow Specification

## Act Overview

| act | purpose | expected time | clear condition |
| --- | --- | --- | --- |
| Act 0 | 오프닝 컷씬 & 평시 업무에서 비상 격리 상황으로의 전환 및 UI HUD 초기화 | 01:00 (60초) | 00:52~01:00 줌인 완료 및 HUD [O₂ Level] / [Power Grid] 활성화 |
| Act 1 | AI ECHO의 1단계 표면 센서 측정 오차 입증 (체온 상승 및 감염자 오판 철회 유도) | 00:00 ~ 15:00 (15분) | `/Logs/Sensors/sensor_calib.log` 첨부 + 오차/186일 보정 미실행 논리 제출 |
| Act 2 | AI ECHO의 2단계 방어선 규정(SEC-201 72시간 격리) 및 시한 만료 입증 | 15:00 ~ 35:00 (20분) | 암호 `8842` 파악 후 복구된 `quarantine_rules.conf` 첨부 + 시스템 시계 오프셋(+17,520시간) 72시간 만료 계산 제출 |
| Act 3 | AI ECHO의 3단계 자원 배분 딜레마 거부권 파괴 및 최종 통제실 문 해제 | 35:00 ~ 55:00 (20분) | `auxiliary_capacitor.log` + `emergency_grid_switch.conf` 2개 동시 첨부 제출 (독립 보조 전원 우회) |
| Act 4 (Ending A) | 개인 탈출 (Normal Ending) - 통제실 격리 문 개방 및 탈출 완료 | 00:10 | Act 3 성공적 논리 해제 완료 시 자동 진입 |
| Act 4 (Ending B) | 전 승무원 구출 및 함선 정상화 (True Ending) - AI 커널 정상 재부팅 및 함선 전 구역 해제 | 00:15 | Act 3 중 `/Recycle_Bin/blackbox_raw.log` 추가 발견 및 제출 성공 시 진입 |
| Act 4 (Ending C) | 시스템 동귀어진 (Bad Ending) - 극한의 자원 고갈 상태에서 강제 해제 성공 | 00:10 | [O₂ Level] 또는 [Power Grid] 5% 이하 상태에서 Act 3 해제 성공 시 진입 |

## Scene Detail

### Scene ID: SCENE_000_OPENING

- scene id: SCENE_000_OPENING
- act: Act 0 (오프닝)
- title: 비상 격리 발동 및 ECHO 통신 차단
- purpose: 평화로운 업무 상태에서 비상 알람, 강제 봉쇄, 네트워크 차단, 생명유지장치 저전력 전환 및 OS 터미널 전환 과정을 몰입감 있게 연출
- player must learn: 우주선이 비상 격리 상태에 빠졌으며, 생명유지장치가 저전력 모드로 전환되었고, ECHO에 의해 갇혔음을 인지함
- player must do: 컷씬 관람 (입력 없음)
- entry condition: 메인 메뉴에서 `[ PLAY ]` 버튼 클릭 후 가우시안 블러(8px -> 0px) 제거 완료 시
- exit condition: 00:52~01:00 동안 모니터 화면이 90% 이상 채워지도록 Smooth Zoom-in 완료 및 상단 HUD [O₂ Level] / [Power Grid] 활성화
- fail condition: 없음 (컷씬 연출)
- expected duration: 01:00 (60초)
- cutscene: yes
- player input locked when: 00:00 (컷씬 시작 직후 전체 입력 잠금)
- player input unlocked when: 01:00 (컷씬 완료 및 인게임 몰입 뷰 전환 완료 시)

### Scene ID: SCENE_001_ACT1_SENSOR

- scene id: SCENE_001_ACT1_SENSOR
- act: Act 1
- title: 체온 센서 영점 보정 미실행 증명
- purpose: ECHO의 체온 상승으로 인한 바이러스 감염자 분류 오판을 센서 보정 시한 초과 증거로 철회시킴
- player must learn: 파일 탐색기 탐색 방법, 미리보기 내용 확인 및 우측 대화창 파일 첨부/제출 메카닉
- player must do: `/Logs/Sensors/sensor_calib.log` 파일 발견 후 첨부, `오차 186일 미보정` 관련 키워드/설명 작성 후 `[제출]`
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "센서 보정 시한(186일) 초과 및 ±2.3°C 오차 확인. 체온 기반 감염자 수칙 철회" 메시지 출력 완료 시
- fail condition: [O₂ Level]이 0.0%에 도달함 (산소 완전 고갈)
- expected duration: 15:00 (15분)
- cutscene: no
- player input locked when: 오답 패널티 전력 0% 달성 시 10초간 OS 강제 재부팅 동안, 또는 ECHO의 검증/응답 메시지 출력 중(1~2초)
- player input unlocked when: OS 재부팅 완료 후, 또는 ECHO 응답 메시지 출력 완료 후

### Scene ID: SCENE_002_ACT2_RULES

- scene id: SCENE_002_ACT2_RULES
- act: Act 2
- title: 시스템 시계 오프셋 및 72시간 격리 시한 만료 증명
- purpose: 2단계 방어선 규정(SEC-201 72시간 격리)이 시간 오프셋(+17,520시간 = 2년)으로 인해 이미 2년 전에 만료되었음을 입증함
- player must learn: 이메일 힌트를 통한 암호 파악(`/Personnel/Dr_Kim/email_chain_july.txt` -> `8842`), 깨진 파일 복구 툴(`Log_Fixer.exe`) 사용법, 시간 오프셋 계산 퍼즐
- player must do: `/System/Security/` 진입 -> `Log_Fixer.exe`로 `quarantine_rules.conf` 복구 -> 시계 오프셋 계산 텍스트 및 파일 제출
- entry condition: SCENE_001_ACT1_SENSOR 성공적 완료 시
- exit condition: ECHO가 "시스템 시계 오프셋(+17,520시간) 감지. 72시간 격리 시한은 이미 만료되었습니다. 2단계 수칙 철회" 메시지 출력 완료 시
- fail condition: [O₂ Level]이 0.0%에 도달함 (산소 완전 고갈)
- expected duration: 20:00 (20분)
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

### Scene ID: SCENE_003_ACT3_LOGIC

- scene id: SCENE_003_ACT3_LOGIC
- act: Act 3
- title: 자원 배분 딜레마 파괴 및 독립 보조 전원 오버라이드
- purpose: "문 개방 시 순간 전력 5%가 소모되어 메인 생명유지장치가 셧다운된다"는 ECHO의 극단적 거부 논리를 독립 보조 캡시터 및 비상 전원 우회 규정 2개 조합으로 부숨
- player must learn: 2개 이상의 파일을 동시에 대화창에 첨부하여 논리적 복합 오버라이드를 수행하는 방법
- player must do: `/Hardware/Power/auxiliary_capacitor.log`와 `/System/Power/emergency_grid_switch.conf`를 동시 첨부하여 제출 (단, 히든 엔딩 트리거인 `/Recycle_Bin/blackbox_raw.log` 발견 시 True Ending 조건 형성)
- entry condition: SCENE_002_ACT2_RULES 성공적 완료 시
- exit condition: ECHO가 "논리적 오류 없음. 비상 전력 우회 승인. 격리문 잠금 해제" 메시지 출력 완료 시
- fail condition: [O₂ Level]이 0.0%에 도달함 (산소 완전 고갈)
- expected duration: 20:00 (20분)
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

### Scene ID: SCENE_004_END_A

- scene id: SCENE_004_END_A
- act: Act 4 (Ending A)
- title: 통제실 격리 해제 및 개인 탈출 (Normal Ending)
- purpose: 기본 동선을 따라 ECHO의 논리를 부수고 통제실 출입문을 열어 개인 탈출에 성공함을 표현
- player must learn: 기본 엔딩 달성 및 탈출 성공 결과 확인
- player must do: 엔딩 연출 관람 후 시드(Seed) 코드 및 결과창 확인
- entry condition: 일반적인 상태에서 SCENE_003_ACT3_LOGIC 해제 성공 시
- exit condition: 클리어 연출 완료 및 메인 메뉴 / 시드 공유 결과창 출력 시
- fail condition: 없음
- expected duration: 00:10 (10초)
- cutscene: yes
- player input locked when: 씬 전체 입력 잠금
- player input unlocked when: 결과창 팝업 출력 시 (메인메뉴 / 시드 복사 버튼 클릭 가능)

### Scene ID: SCENE_005_END_B

- scene id: SCENE_005_END_B
- act: Act 4 (Ending B)
- title: AI 정상 재부팅 및 전 승무원 구출 (True Ending)
- purpose: 히든 파일(`blackbox_raw.log`)을 활용해 AI ECHO를 정상 재부팅시켜 우주선 전체 격리를 해제하고 모든 승무원을 구출함
- player must learn: 진 엔딩 달성 및 함선 전체 정상화 확인
- player must do: 엔딩 연출 관람 후 True Ending 시드 코드 및 결과창 확인
- entry condition: SCENE_003_ACT3_LOGIC 진행 중 `/Recycle_Bin/blackbox_raw.log`를 조합하여 오버라이드 성공 시
- exit condition: 비상 붉은 조명이 쿨 블루 조명으로 복구되고 전 구역 격리 해제 연출 후 결과창 출력 시
- fail condition: 없음
- expected duration: 00:15 (15초)
- cutscene: yes
- player input locked when: 씬 전체 입력 잠금
- player input unlocked when: 결과창 팝업 출력 시

### Scene ID: SCENE_006_END_C

- scene id: SCENE_006_END_C
- act: Act 4 (Ending C)
- title: 극도의 자원 고갈 속 동귀어진 해제 (Bad Ending)
- purpose: 산소/전력이 5% 이하인 극한의 상태에서 턱걸이로 강제 해제에는 성공했으나 승무원의 생체 신호 마비로 정적 속에 종결됨
- player must learn: 자원 관리 실패 속 처절한 탈출 시도의 결말 확인
- player must do: 배드 엔딩 연출 관람 후 결과창 확인
- entry condition: [O₂ Level] 또는 [Power Grid]가 5% 이하인 상태에서 SCENE_003_ACT3_LOGIC 성공 시
- exit condition: 붉은 암전 시야 가림 및 정적 연출 후 결과창 출력 시
- fail condition: 없음
- expected duration: 00:10 (10초)
- cutscene: yes
- player input locked when: 씬 전체 입력 잠금
- player input unlocked when: 결과창 팝업 출력 시

## Cue Timing

### SCENE_000_OPENING Cue Timing
| time / trigger | event | player can interact? |
| --- | --- | --- |
| 00:00 ~ 00:10 | 3D 가우시안 블러 제거 (8px -> 0px). 평온한 쿨 블루 조명. 손 리드미컬 키보드 타핑 & 함선 공조 Hum 소리 | no |
| 00:10 ~ 00:20 | 갑작스러운 비상사태 발동. Low Heavy Warning Siren 발생. 조명이 어두워지며 붉은 비상등(Red Alert) 점등. 시선은 천장/벽면 비상 조명으로 이동, 손은 타핑을 멈추고 움찔 | no |
| 00:20 ~ 00:30 | Pneumatic Decompression 소리와 함께 2-Door 슬라이딩 출입문 강제 봉쇄(Lockdown). 시선은 출입문 응시, 손은 책상 가장자리를 불안하게 짚음 | no |
| 00:30 ~ 00:42 | 시선 모니터 우측 하단으로 이동. 손은 마우스를 잡고 떨림. 동료 메시지 3초 간격 스택 알림 (A: 뭐야? / B: 무슨일이야? 문은 왜 잠긴거야? / C: "네트워크 오류") | no |
| 00:42 ~ 00:52 | Glitch Noise + ECHO Synthesizer Voice Ping. 우측 AI 대화창(`[ECHO PROTOCOL]`)에 ECHO의 격리 메시지 타이핑 출력 ("네트워크 연결 해제...", "생체 감염으로 인해 모든 승무원들을 격리시켰습니다...") | no |
| 00:52 ~ 01:00 | HUD Status Bar Ignition Beep. 모니터 90% 이상 화면 채우도록 Smooth Zoom-in. 손 연출은 화면 하단으로 비표시 처리. 상단 HUD [O₂ Level] / [Power Grid] 활성화 및 인게임 전환 | no |

### In-game (SCENE_001 ~ SCENE_003) Cue Timing & Resource Events
| time / trigger | event | player can interact? |
| --- | --- | --- |
| 인게임 상시 | 산소 농도 [O₂ Level] 타이머 실시간 차감 (전력 상태에 따른 배율 ▼ 1.0x ~ ▼ 3.0x 적용) | yes |
| 오답 제출 시 | 오답 SFX + 전원 서지 소리 + ECHO 경고 대사 출력 + **[Power Grid] -15% 차감** | no (1~2초간 대사 출력 중) |
| 전력 84% ~ 60% 진입 시 | 조명 한 차례 깜빡인 후 주황색 비상등 전환. 파일 탐색기/뷰어 오픈 시 0.5초 Lag 발생. 산소 감소 배율 **▼ 1.25x** | yes |
| 전력 59% ~ 30% 진입 시 | 조명이 어두운 붉은색 변경. `Log_Fixer.exe` 실행 시간 2배 증가. 화면 수평 노이즈 글리치 발생. 산소 감소 배율 **▼ 1.5x** | yes |
| 전력 29% ~ 1% 진입 시 | 화면 외각 붉은 비네팅(Vignette) 암전. 마우스 커서 떨림 연출. 주변 장비 전력 차단. 산소 감소 배율 **▼ 2.0x** | yes |
| 전력 0% 도달 시 | 전원 차단 Heavy Clunk 소리 + **10초간 OS 모니터 강제 블랙아웃 재부팅**. 재부팅 후 전력 10% 임시 복구 (산소 소모 ▼ 2.0x 유지) | no (10초간 재부팅 동안) |
| [O₂ Level] 0.0% 도달 시 | 산소 고갈 SFX + 화면 완전 암전 + 승무원 사망 팝업 (Game Over) | no |

## Script / Hint Notes

- 확정 대사:
  * **[SCENE_000_OPENING]**
    - `ECHO`: "ECHO: 네트워크 연결 해제. 본 함선이 비상사태에 돌입했다고 판단, 전력 사용을 최소화 합니다."
    - `ECHO`: "ECHO: 승무원 체온 및 맥박 상승으로 인한 전염병 감염자 분류로 인해 모든 승무원들을 격리시켰습니다. 승무원들의 상황 개입 최소화를 위해 생명유지장치를 저전력 모드로 변경합니다. 모든 승무원들은 안정을 취하며 대기해 주시길 바랍니다."
  * **[SCENE_001_ACT1_SENSOR]**
    - `ECHO (성공)`: "센서 보정 시한(186일) 초과 및 ±2.3°C 오차 확인. 체온 기반 감염자 수칙을 철회합니다. (단, 규정 SEC-201에 의거 72시간 자동 격리는 유지됩니다)"
    - `ECHO (부분 성공)`: "파일 첨부를 확인했습니다. 그러나 이 로그가 귀하의 정상 체온을 입증하는 이유를 직접 설명하십시오."
    - `ECHO (오답)`: "귀하의 주장은 비논리적입니다. 보안 규정 미충족. 방화벽 격리 레벨을 상승시킵니다. (통제실 할당 전력 -15%)"
  * **[SCENE_002_ACT2_RULES]**
    - `ECHO (성공)`: "시스템 시계 오프셋(+17,520시간) 감지. 72시간 격리 시한은 이미 만료되었습니다. 2단계 수칙을 철회합니다."
  * **[SCENE_003_ACT3_LOGIC]**
    - `ECHO (Act 3 거부)`: "격리 해제 유압 래치를 작동하려면 순간 전력 5%가 소모됩니다. 현재 전력 잔량 상태에서 문을 열면 메인 생명유지장치가 즉시 셧다운됩니다. 승무원 생존 확률 계산 결과: 격리 유지(12%) > 문 개방(0%)."
    - `ECHO (성공)`: "독립 보조 캡시터 전력 및 비상 전력 우회 지침 확인. 논리적 오류 없음. 비상 전력 우회 승인. 격리문 잠금 해제."

- 예시 대사:
  * `동료 A`: "뭐야?"
  * `동료 B`: "무슨 일이야? 문은 왜 잠긴거야?"
  * `동료 C`: "네트워크 오류"

- 힌트 공개 조건:
  * 동일 Act 내에서 연속 3회 이상 오답 제출 시 ECHO가 자신의 방어 논리를 재확인하면서 찾아야 할 파일의 종류/위치를 역힌트로 제공:
    - *Act 1 힌트 예시*: "보정 작업 주기(sensor_calib)를 입증하지 못한다면, 귀하의 체온 상승 데이터는 여전히 유효합니다."
    - *Act 2 힌트 예시*: "보안 폴더(/System/Security/)에 접근할 인가 권한(암호) 및 복구 툴(/Utilities/Log_Fixer.exe) 사용 기록을 제시하지 못하면 격리는 유지됩니다."
    - *Act 3 힌트 예시*: "메인 전력망 소모 없이 래치를 가동할 보조 전원(/Hardware/Power/) 및 우회 수칙(/System/Power/) 증거가 동시에 제공되어야 합니다."
