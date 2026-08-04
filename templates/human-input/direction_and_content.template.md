# Direction And Content Specification

## Visual Direction

- overall mood: 1인칭 SF 미스테리 추리 퍼즐. 1인칭 3D 환경(우주선 통제실)과 2D OS 터미널(`Hermes OS`)의 유기적 융합. 극도의 공간적 몰입감과 자원 고갈 비상 상황의 서스펜스 시각화.
- lighting:
  * 평시 (Normal / 전력 100% ~ 85%): 쿨 블루/화이트 (Cool White/Blue 톤의 쾌적한 정상 조명)
  * 주의 (Caution / 전력 84% ~ 60%): 조명이 한 차례 깜빡인 후 주황색 비상등 전환
  * 경고 (Warning / 전력 59% ~ 30%): 통제실 조명이 어두운 붉은색(Red Alert)으로 전환
  * 위기 (Critical / 전력 29% ~ 1%): 화면 외각 붉은 비네팅(Vignette) 암전 효과, 메인 OS 모니터를 제외한 주변 통제실 패널 전력 완전히 차단
  * 블랙아웃 (Blackout / 전력 0%): 10초간 OS 모니터 강제 셧다운 및 통제실 완전 암전 (재부팅 후 붉은 조명 유지)
- color direction:
  * 기본 톤: 쿨 블루(#4A90E2), 주황색 비상등(#F5A623), 붉은 비상 봉쇄(#D0021B), 성공 연출 그린(#7ED321)
  * HUD: O₂ Level 및 Power Grid 게이지, 전력 차감 시 붉은 파티클 연출, 산소 감소 배율 붉은색 강조(▼ 1.0x -> ▼ 1.25x -> ▼ 1.5x -> ▼ 2.0x -> ▼ 3.0x)
- UI mood: SF 모니터 OS 터미널 (`Hermes OS`), 듀얼 화면 구성(좌측: 파일 탐색기 & 미리보기 뷰어, 우측: `[ECHO PROTOCOL]` 대화창). 인게임 플레이 시 모니터 90% 이상 채우는 몰입 뷰(Terminal Focus View), 캐릭터 손 비표시(Non-visible)로 가독성/조작성 극대화.
- glitch / warning / noise rules:
  * 오답 제출 시: 전원 서지(Surge)와 함께 화면 순간 암전 및 경고 파티클 연출
  * 주의 (84% ~ 60%): 파일 탐색기/뷰어 오픈 시 0.5초 지연(Lag) 발생
  * 경고 (59% ~ 30%): 복구 툴(`Log_Fixer.exe`) 실행 시간 2배 증가, 모니터 화면 수평 전자 노이즈 글리치 발생
  * 위기 (29% ~ 1%): 마우스 커서 미세 떨림 연출, 붉은 비네팅 암전
  * 블랙아웃 (0%): 10초간 화면 완전 암전 후 로딩 터미널 출현 및 재부팅

## Audio Direction

- bgm tone: 멜로디 음악 트랙을 배제하고, 차분한 함선 공조 시스템 험(Hum) 소리와 전력 감소에 따른 불길한 Low-frequency 서스펜스 앰비언스(Ambient Soundscape) 위주로 연출.
- alarm tone: Low Heavy Warning Siren 시작, Pneumatic Decompression & Heavy Sliding Door Close SFX, Door Lock Heavy Clunk SFX.
- ui sound direction:
  * 컷씬 & HUD: 키보드 리드미컬 타핑음, Notification Message Pop-up sound(3회), 통신 끊김 스파크/글리치 Sound, ECHO Synthesizer Voice Ping, HUD Status Bar Ignition Beep.
  * 오답 및 판정: 오답 시 시스템 경고음 + 전원 서지(Surge) 소리. 성공 시 성공 긍정 SFX (Green Glow 연출 동반).
  * 블랙아웃: 전원 차단 Heavy Clunk 소리 -> 10초 무음 -> 재부팅 SFX.
- silence rules: 전력 0% 도달 시 10초간 OS 모니터 강제 셧다운과 함께 완전한 무음(Silence)을 유지하여 극도의 공포와 긴장감을 유도한 후 재부팅 SFX 출력.

## Writing Direction

- AI tone: 감정 표현(분노, 악의, 비하, 모욕)을 철저히 금지하고 무기물적/논리적/시스템 규정 격식체만 사용. (ECHO는 악의가 아닌 고장 난 센서/시계로 인해 정당하게 오판하는 논리 엔진이므로 기계적 판단 근거만 통보).
- log tone: 시스템 로그 표준 포맷 (`[WARN]`, `[ERR]`, `[FAIL]`, `[INFO]`), 시한/수치/오프셋이 명시된 건조하고 정형화된 보고 문체.
- crew message tone: 비상 봉쇄 상황에 직면한 승무원들의 당황스럽고 생생한 구어체 반말/대화체 (`"뭐야?"`, `"무슨 일이야? 문은 왜 잠긴거야?"`).
- forbidden expressions:
  * ECHO의 감정적 비하, 분노, 비꼬는 표현 (예: "인간은 멍청하다", "화가 난다" 등 금지).
  * 현대 인터넷 슬랭 및 SF 세계관(서기 8245년 심우주 탐사선 헤르메스호)에 상충하는 어휘 금지.
- must-keep expressions:
  * `"지침 101조: 외부 위험으로부터 승무원을 보호합니다. 당신은 지금 위험 상태입니다."`
  * `"ECHO: 네트워크 연결 해제. 본 함선이 비상사태에 돌입했다고 판단, 전력 사용을 최소화 합니다."`
  * `"ECHO: {카테고리 사유}로 인해 모든 승무원들을 격리시켰습니다. 승무원들의 상황 개입 최소화를 위해 생명유지장치를 저전력 모드로 변경합니다. 모든 승무원들은 안정을 취하며 대기해 주시길 바랍니다."`
  * `"귀하의 주장은 비논리적입니다. 보안 규정 미충족. 방화벽 격리 레벨을 상승시킵니다. (통제실 할당 전력 -15%)"`
  * `"해당 항목은 이미 철회된 수칙입니다. 현재 적용 중인 격리 사유에 집중하십시오."`

## Dialogue Policy

| line id | speaker | text | status | used in |
| --- | --- | --- | --- | --- |
| D-001 | ECHO | "지침 101조: 외부 위험으로부터 승무원을 보호합니다. 당신은 지금 위험 상태입니다." | final | Lore / Opening Intro |
| D-002 | ECHO | "ECHO: 네트워크 연결 해제. 본 함선이 비상사태에 돌입했다고 판단, 전력 사용을 최소화 합니다." | final | SCENE_000_OPENING (00:42) |
| D-003 | ECHO | "ECHO: 승무원 체온 및 맥박 상승으로 인한 전염병 감염자 분류로 인해 모든 승무원들을 격리시켰습니다. 승무원들의 상황 개입 최소화를 위해 생명유지장치를 저전력 모드로 변경합니다. 모든 승무원들은 안정을 취하며 대기해 주시길 바랍니다." | final | SCENE_000_OPENING (00:45) |
| D-004 | Crew A | "뭐야?" | draft | SCENE_000_OPENING (00:33) |
| D-005 | Crew B | "무슨 일이야? 문은 왜 잠긴거야?" | draft | SCENE_000_OPENING (00:36) |
| D-006 | System | "네트워크 오류" | final | SCENE_000_OPENING (00:39) |
| D-007 | ECHO | "센서 보정 시한(186일) 초과 및 ±2.3°C 오차 확인. 체온 기반 감염자 수칙을 철회합니다." | final | SCENE_A_ACT1 성공 |
| D-008 | ECHO | "파일 첨부를 확인했습니다. 그러나 이 로그가 귀하의 정상 상태를 입증하는 이유를 설명하십시오." | final | SCENE_A_ACT1 부분 성공 |
| D-009 | ECHO | "귀하의 주장은 비논리적입니다. 보안 규정 미충족. 방화벽 격리 레벨을 상승시킵니다. (통제실 할당 전력 -15%)" | final | Act 1~3 공통 오답 |
| D-010 | ECHO | "해당 항목은 이미 철회된 수칙입니다. 현재 적용 중인 격리 사유에 집중하십시오." | final | Act 1~3 구 증거 재제출 |
| D-011 | ECHO | "보정 작업 주기(sensor_calib)를 입증하지 못한다면, 귀하의 체온 상승 데이터는 여전히 유효합니다." | final | SCENE_A_ACT1 연속 오답 힌트 |
| D-012 | ECHO | "시스템 시계 오프셋(+17,520시간) 감지. 72시간 격리 시한은 이미 만료되었습니다. 2단계 수칙 철회." | final | SCENE_A_ACT2 성공 |
| D-013 | ECHO | "격리 해제 유압 래치를 작동하려면 순간 전력 5%가 소모됩니다. 현재 전력 잔량 상태에서 문을 열면 메인 생명유지장치가 즉시 셧다운됩니다. 승무원 생존 확률 계산 결과: 격리 유지(12%) > 문 개방(0%)." | final | SCENE_A_ACT3 ECHO 거부 |
| D-014 | ECHO | "독립 보조 캡시터 전력 및 비상 전력 우회 지침 확인. 논리적 오류 없음. 비상 전력 우회 승인. 격리문 잠금 해제." | final | SCENE_A_ACT3 성공 |
| D-015 | ECHO | "방사능 감지기 필터 소모율 99% 및 +150mSv 노이즈 확인. 방사능 피폭 수칙을 철회합니다." | draft | SCENE_B_ACT1 성공 |
| D-016 | ECHO | "키보드 I/O 포트 누전 및 하드웨어 오류 신호 확인. 해킹 공격 격리 수칙을 철회합니다." | draft | SCENE_C_ACT1 성공 |
| D-017 | ECHO | "뇌파 스캐너 템플릿 미갱신 및 전임 승무원 데이터 오인 인정. 정신 이상 수칙을 철회합니다." | draft | SCENE_D_ACT1 성공 |
| D-018 | ECHO | "공기 정화기 3호 감지 밸브 고착 및 0.001% 이하 농도 확인. 유독 가스 수칙을 철회합니다." | draft | SCENE_E_ACT1 성공 |
| D-019 | ECHO | "출입문 생체 스캐너 렌즈 균열 및 승무원 ID#102 오인식 인정. 반란 수칙을 철회합니다." | draft | SCENE_F_ACT1 성공 |
| D-020 | ECHO | "제시된 2개 증거 간 논리적 검증 완료. 오버라이드 지침 및 제1원칙 승인. 통제실 출입문 잠금 해제." | final | Act 3 공통 성공 |

## Content References
  