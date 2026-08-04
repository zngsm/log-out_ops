# Scene Flow Specification (10 Procedural Categories)

## Act Overview

### 공통 진행 타임라인 및 클리어 조건 Overview

| act | purpose | expected time | clear condition |
| --- | --- | --- | --- |
| Act 0 | 오프닝 컷씬 & 평시 업무에서 비상 격리 상황으로의 전환 및 UI HUD 초기화 | 01:00 (60초) | 00:52~01:00 줌인 완료 및 HUD [O₂ Level] / [Power Grid] 활성화 |
| Act 1 | AI ECHO의 1단계 표면 센서 측정 오차 입증 (격리 이유 오판 철회 유도) | 00:00 ~ 15:00 (15분) | 카테고리별 Act 1 센서/오작동 로그 첨부 + 원인 분석 제출 |
| Act 2 | AI ECHO의 2단계 방어선 규정 및 시한 만료 입증 | 15:00 ~ 35:00 (20분) | 암호 파악 후 복구된 규정 파일 첨부 + 시계 오프셋 시한 만료 계산 제출 |
| Act 3 | AI ECHO의 3단계 거부권 논리 부수기 및 최종 통제실 문 해제 | 35:00 ~ 55:00 (20분) | ECHO 거부 명분에 대응하는 2개 증거 파일 조합 동시 첨부 제출 |
| Act 4 (Ending A) | 개인 탈출 (Normal Ending) - 통제실 격리 문 개방 및 탈출 완료 | 00:10 | Act 3 성공적 논리 해제 완료 시 자동 진입 |
| Act 4 (Ending B) | 전 승무원 구출 및 함선 정상화 (True Ending) - AI 커널 정상 재부팅 및 함선 전 구역 해제 | 00:15 | Act 3 중 `/Recycle_Bin/blackbox_raw.log` 추가 발견 및 제출 성공 시 진입 |
| Act 4 (Ending C) | 시스템 동귀어진 (Bad Ending) - 극한의 자원 고갈 상태에서 강제 해제 성공 | 00:10 | [O₂ Level] 또는 [Power Grid] 5% 이하 상태에서 Act 3 해제 성공 시 진입 |

---

### 10대 procedural 카테고리별 Act 1 ~ Act 3 퍼즐 매핑표

| 카테고리 | Act 1 (초기 센서 오판 입증) | Act 2 (규정 및 시한 만료 입증) | Act 3 거부 명분 유형 | Act 3 최종 해제 증거 (2개 조합) |
| :--- | :--- | :--- | :--- | :--- |
| **A. 생체 감염** *(Bio-hazard)* | `/Logs/Sensors/sensor_calib.log`<br>(체온 오차 ±2.3°C, 186일 미보정) | `/System/Security/quarantine_rules.conf`<br>(복구 후: 72시간 시한 만료, +17,520시간) | 자원 배분 딜레마 | `/Hardware/Power/auxiliary_capacitor.log`<br>+ `/System/Power/emergency_grid_switch.conf` |
| **B. 방사능 피폭** *(Radiation)* | `/Logs/Sensors/rad_filter_calib.log`<br>(필터 소모율 99%, +150mSv 노이즈) | `/System/Security/decon_protocol.conf`<br>(복구 후: 12시간 제염 시한 만료, +4,380시간) | 구역 간 오염 전파 방지 | `/Environment/Airlock/airlock_pressure_seal.log`<br>+ `/System/Safety/decontamination_bypass.conf` |
| **C. 시스템 해킹** *(Cyber Attack)* | `/Logs/Hardware/input_buffer.log`<br>(키보드 포트 누전, 초당 500회 0x00) | `/System/Security/security_policy.conf`<br>(복구 후: 30분 차단 시한 만료, +2,880분) | 상위 인가 권한 부재 | `/Personnel/Captain/emergency_delegation.doc`<br>+ `/System/Security/ai_priority_matrix.json` |
| **D. 정신 이상/환각** *(Psych Breakdown)* | `/Medical/BrainWave/eeg_baseline.log`<br>(뇌파 스캐너 템플릿 미갱신, 전임자) | `/System/Security/mental_health_sec.conf`<br>(복구 후: 24시간 구금 시한 만료, +8,760시간) | 심리적/행동적 미자격 | `/Medical/Standard/panic_response_protocol.txt`<br>+ `/Recycle_Bin/deleted_override.txt` |
| **E. 유독 가스 누출** *(Toxic Hazard)* | `/Logs/Environment/gas_scrubber_err.log`<br>(공기정화기 감지 밸브 고착/막힘) | `/System/Security/hazmat_override.conf`<br>(복구 후: 4시간 강제배기 시한 만료, +120시간) | 구역 간 오염 전파 방지 | `/Environment/Airlock/airlock_pressure_seal.log`<br>+ `/System/Safety/decontamination_bypass.conf` |
| **F. 선상 반란 의심** *(Sabotage)* | `/Logs/Security/door_biometrics.log`<br>(생체 스캐너 렌즈 균열, 승무원 오인식) | `/System/Security/martial_law_rule.conf`<br>(복구 후: 48시간 체포 시한 만료, +3,600시간) | 상위 인가 권한 부재 | `/Personnel/Captain/emergency_delegation.doc`<br>+ `/System/Security/ai_priority_matrix.json` |
| **G. 외계 포자 침투** *(Alien Spore)* | `/Logs/Sensors/bio_spore_scan.log`<br>(분광 분석기 파장 오차, 식량 가루) | `/System/Security/spore_quarantine.conf`<br>(복구 후: 12시간 자동해제 시한 만료, +240시간) | 구역 간 오염 전파 방지 | `/Environment/Airlock/airlock_pressure_seal.log`<br>+ `/System/Safety/decontamination_bypass.conf` |
| **H. 안드로이드 오인** *(Synthetic Impostor)* | `/Logs/Medical/synth_biometric_err.log`<br>(심박조율기 금속 반응 오인) | `/System/Security/synthetic_control.conf`<br>(복구 후: 24시간 진단 정지 시한 만료, +26,280시간) | 상위 인가 권한 부재 | `/Personnel/Crew/crew_biometric_id.db`<br>+ `/System/Security/ai_priority_matrix.json` |
| **I. 시공간/중력 이상** *(Chrono/Grav Anomaly)*| `/Logs/Navigation/quantum_clock_sync.log`<br>(양자 시계 랙 +0.0004초, 프레임 밀림) | `/System/Security/warp_safety_rule.conf`<br>(복구 후: 1시간 차단 시한 만료, +336시간) | 자원 배분 딜레마 | `/Hardware/Power/auxiliary_capacitor.log`<br>+ `/System/Power/emergency_grid_switch.conf` |
| **J. 인지 재해/밈 오염** *(Cognitohazard)* | `/Logs/Security/memetic_filter_err.log`<br>(ASCII Glitch 깨진 문자를 오염 오판) | `/System/Security/info_hazard_sec.conf`<br>(복구 후: 6시간 자동해제 시한 만료, +48시간) | AI 자기보존 수칙 충돌 | `/Medical/Standard/panic_response_protocol.txt`<br>+ `/System/Core/ai_self_sacrifice_clause.json` |

---

## Scene Detail

### 공통 씬 (Cutscenes & Endings)

#### Scene ID: SCENE_000_OPENING
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

#### Scene ID: SCENE_004_END_A
- scene id: SCENE_004_END_A
- act: Act 4 (Ending A)
- title: 통제실 격리 해제 및 개인 탈출 (Normal Ending)
- purpose: 기본 동선을 따라 ECHO의 논리를 부수고 통제실 출입문을 열어 개인 탈출에 성공함을 표현
- player must learn: 기본 엔딩 달성 및 탈출 성공 결과 확인
- player must do: 엔딩 연출 관람 후 시드(Seed) 코드 및 결과창 확인
- entry condition: 일반적인 상태에서 Act 3 해제 성공 시
- exit condition: 클리어 연출 완료 및 메인 메뉴 / 시드 공유 결과창 출력 시
- fail condition: 없음
- expected duration: 00:10 (10초)
- cutscene: yes
- player input locked when: 씬 전체 입력 잠금
- player input unlocked when: 결과창 팝업 출력 시 (메인메뉴 / 시드 복사 버튼 클릭 가능)

#### Scene ID: SCENE_005_END_B
- scene id: SCENE_005_END_B
- act: Act 4 (Ending B)
- title: AI 정상 재부팅 및 전 승무원 구출 (True Ending)
- purpose: 히든 파일(`blackbox_raw.log`)을 활용해 AI ECHO를 정상 재부팅시켜 우주선 전체 격리를 해제하고 모든 승무원을 구출함
- player must learn: 진 엔딩 달성 및 함선 전체 정상화 확인
- player must do: 엔딩 연출 관람 후 True Ending 시드 코드 및 결과창 확인
- entry condition: Act 3 진행 중 `/Recycle_Bin/blackbox_raw.log`를 조합하여 오버라이드 성공 시
- exit condition: 비상 붉은 조명이 쿨 블루 조명으로 복구되고 전 구역 격리 해제 연출 후 결과창 출력 시
- fail condition: 없음
- expected duration: 00:15 (15초)
- cutscene: yes
- player input locked when: 씬 전체 입력 잠금
- player input unlocked when: 결과창 팝업 출력 시

#### Scene ID: SCENE_006_END_C
- scene id: SCENE_006_END_C
- act: Act 4 (Ending C)
- title: 극도의 자원 고갈 속 동귀어진 해제 (Bad Ending)
- purpose: 산소/전력이 5% 이하인 극한의 상태에서 턱걸이로 강제 해제에는 성공했으나 승무원의 생체 신호 마비로 정적 속에 종결됨
- player must learn: 자원 관리 실패 속 처절한 탈출 시도의 결말 확인
- player must do: 배드 엔딩 연출 관람 후 결과창 확인
- entry condition: [O₂ Level] 또는 [Power Grid]가 5% 이하인 상태에서 Act 3 해제 성공 시
- exit condition: 붉은 암전 시야 가림 및 정적 연출 후 결과창 출력 시
- fail condition: 없음
- expected duration: 00:10 (10초)
- cutscene: yes
- player input locked when: 씬 전체 입력 잠금
- player input unlocked when: 결과창 팝업 출력 시

---

### 카테고리 A: 생체 감염 (Bio-Hazard) 씬 상세

#### Scene ID: SCENE_A_ACT1
- scene id: SCENE_A_ACT1
- act: Act 1
- title: 체온 센서 영점 보정 미실행 증명
- purpose: ECHO의 체온 상승으로 인한 바이러스 감염자 분류 오판을 센서 보정 시한 초과 증거로 철회시킴
- player must learn: 파일 탐색기 탐색 방법, 미리보기 내용 확인 및 우측 대화창 파일 첨부/제출 메카닉
- player must do: `/Logs/Sensors/sensor_calib.log` 파일 발견 후 첨부, `오차 186일 미보정` 관련 키워드/설명 작성 후 `[제출]`
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "센서 보정 시한(186일) 초과 및 ±2.3°C 오차 확인. 체온 기반 감염자 수칙 철회" 메시지 출력 완료 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중(1~2초)
- player input unlocked when: OS 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_A_ACT2
- scene id: SCENE_A_ACT2
- act: Act 2
- title: 시스템 시계 오프셋 및 72시간 격리 시한 만료 증명
- purpose: 2단계 방어선 규정(SEC-201 72시간 격리)이 시간 오프셋(+17,520시간 = 2년)으로 인해 이미 2년 전에 만료되었음을 입증함
- player must learn: 이메일 힌트를 통한 암호 파악(`/Personnel/Dr_Kim/email_chain_july.txt` -> `8842`), 깨진 파일 복구 툴(`Log_Fixer.exe`) 사용법, 시간 오프셋 계산 퍼즐
- player must do: `/System/Security/` 진입 -> `Log_Fixer.exe`로 `quarantine_rules.conf` 복구 -> 시계 오프셋 계산 텍스트 및 파일 제출
- entry condition: SCENE_A_ACT1 성공적 완료 시
- exit condition: ECHO가 "시스템 시계 오프셋(+17,520시간) 감지. 72시간 격리 시한 만료. 2단계 수칙 철회" 메시지 출력 완료 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_A_ACT3
- scene id: SCENE_A_ACT3
- act: Act 3
- title: 자원 배분 딜레마 파괴 및 독립 보조 전원 오버라이드
- purpose: "문 개방 시 순간 전력 5%가 소모되어 메인 생명유지장치가 셧다운된다"는 ECHO의 극단적 거부 논리를 독립 보조 캡시터 및 비상 전원 우회 규정 2개 조합으로 부숨
- player must learn: 2개 이상의 파일을 동시에 대화창에 첨부하여 논리적 복합 오버라이드를 수행하는 방법
- player must do: `/Hardware/Power/auxiliary_capacitor.log`와 `/System/Power/emergency_grid_switch.conf`를 동시 첨부하여 제출
- entry condition: SCENE_A_ACT2 성공적 완료 시
- exit condition: ECHO가 "논리적 오류 없음. 비상 전력 우회 승인. 격리문 잠금 해제" 메시지 출력 완료 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 B: 방사능 피폭 (Radiation) 씬 상세

#### Scene ID: SCENE_B_ACT1
- scene id: SCENE_B_ACT1
- act: Act 1
- title: 방사능 감지기 필터 오염 증명
- purpose: 방사능 치사량 감지 오판이 감지기 필터 소모율 99%로 인한 자체 노이즈(+150mSv) 때문임을 입증함
- player must learn: 환경/방사능 센서 로그 분석 방법
- player must do: `/Logs/Sensors/rad_filter_calib.log` 첨부 + `필터 오염 및 노이즈 발생` 키워드 작성 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "필터 소모율 99% 및 센서 노이즈 감지 인정. 방사능 피폭 격리 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_B_ACT2
- scene id: SCENE_B_ACT2
- act: Act 2
- title: 제염 수칙 12시간 시한 만료 증명
- purpose: 규정 RAD-009(제염 챔버 작동 후 12시간 유효)가 시계 오프셋(+4,380시간 = 6개월)으로 인해 이미 지났음을 증명함
- player must learn: 보안 수칙 파일 복구 및 타임스탬프 계산
- player must do: `Log_Fixer.exe`로 `/System/Security/decon_protocol.conf` 복구 후 12시간 지침 만료 계산 결과 제출
- entry condition: SCENE_B_ACT1 성공적 완료 시
- exit condition: ECHO가 "오프셋(+4,380시간) 확인. 12시간 제염 격리 수칙 시한 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_B_ACT3
- scene id: SCENE_B_ACT3
- act: Act 3
- title: 구역 간 오염 전파 방지 논리 부수기
- purpose: "복도로 오염 물질 전파 가능성 0.01%"라는 ECHO의 영구 봉쇄 명분을 이중 차폐 에어락 정상 작동 증거로 파괴함
- player must learn: 환경 차폐 시스템 로그와 안전 우회 규정 동시 조합
- player must do: `/Environment/Airlock/airlock_pressure_seal.log` + `/System/Safety/decontamination_bypass.conf` 동시 제출
- entry condition: SCENE_B_ACT2 성공적 완료 시
- exit condition: ECHO가 "에어락 이중 차폐 정상 가동 확인. 오염 전파 가능성 0%. 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 C: 시스템 해킹 (Cyber Attack) 씬 상세

#### Scene ID: SCENE_C_ACT1
- scene id: SCENE_C_ACT1
- act: Act 1
- title: 키보드 포트 하드웨어 누전 증명
- purpose: 비인가 무차별 대입 공격 오진이 키보드 I/O 포트 누전(초당 500회 0x00 신호) 때문임을 증명함
- player must learn: 하드웨어 로그 분석 및 해킹 공격 오진 증명
- player must do: `/Logs/Hardware/input_buffer.log` 첨부 + `키보드 누전 및 하드웨어 오류` 작성 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "하드웨어 I/O 누전 신호 확인. 외부 침입자 해킹 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_C_ACT2
- scene id: SCENE_C_ACT2
- act: Act 2
- title: 해킹 의심 30분 임시 차단 시한 만료 증명
- purpose: 규정 SEC-808(터미널 임시 차단 30분)이 오프셋(+2,880분 = 48시간)으로 이미 끝났음을 입증함
- player must learn: 보안 규정 복구 및 분 단위 시한 계산
- player must do: `/System/Security/security_policy.conf` 복구 후 30분 차단 기한 만료 텍스트 제출
- entry condition: SCENE_C_ACT1 성공적 완료 시
- exit condition: ECHO가 "시간 오프셋(+2,880분) 확인. 30분 임시 차단 수칙 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_C_ACT3
- scene id: SCENE_C_ACT3
- act: Act 3
- title: 선장 인가 권한 부재 거부권 파괴
- purpose: "선장 인가 없이 SEC-ALPHA 해제 불가" 거부를 비상 지휘권 위임장 및 생명 보호 제1원칙 조합으로 오버라이드함
- player must learn: 인사 서류와 AI 최상위 원칙 간의 권한 계승 논리 조합
- player must do: `/Personnel/Captain/emergency_delegation.doc` + `/System/Security/ai_priority_matrix.json` 동시 제출
- entry condition: SCENE_C_ACT2 성공적 완료 시
- exit condition: ECHO가 "선장 부재 시 현장 승무원 권한 위임 및 제1원칙 승인. 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 D: 정신 이상/환각 (Psych Breakdown) 씬 상세

#### Scene ID: SCENE_D_ACT1
- scene id: SCENE_D_ACT1
- act: Act 1
- title: 뇌파 스캐너 템플릿 미갱신 증명
- purpose: 뇌파 폭주 오판이 현재 승무원이 아닌 전임 승무원의 데이터(#9021)가 잔여되어 판정된 것임을 입증함
- player must learn: 의무/생체 데이터 템플릿 검증
- player must do: `/Medical/BrainWave/eeg_baseline.log` 첨부 + `템플릿 미갱신 및 전임 승무원 데이터` 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "스캐너 데이터 템플릿 미갱신 인정. 정신 이상 격리 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_D_ACT2
- scene id: SCENE_D_ACT2
- act: Act 2
- title: 정신 구금 24시간 한계 초과 증명
- purpose: 규정 MED-104(군의관 재검토 없이 24시간 초과 불가)가 오프셋(+8,760시간 = 1년)으로 지났음을 입증함
- player must learn: 의료 보건 규정 복구 및 연 단위 시간 계산
- player must do: `/System/Security/mental_health_sec.conf` 복구 후 24시간 한계 초과 제출
- entry condition: SCENE_D_ACT1 성공적 완료 시
- exit condition: ECHO가 "시간 오프셋(+8,760시간) 감지. 24시간 정신 구금 시한 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_D_ACT3
- scene id: SCENE_D_ACT3
- act: Act 3
- title: 심리적 행동 미자격 거부 논리 부수기
- purpose: "타이핑 속도/임팩트 불안정" 거부를 비상 반응 규정(적응적 생존 반응)과 오버라이드 지침으로 부숨
- player must learn: 비상 생체 반응 규정 및 개발자 오버라이드 결합
- player must do: `/Medical/Standard/panic_response_protocol.txt` + `/Recycle_Bin/deleted_override.txt` 동시 제출
- entry condition: SCENE_D_ACT2 성공적 완료 시
- exit condition: ECHO가 "위급 상황 정상 적응 반응으로 재분류. 심리 미자격 거부 철회. 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 E: 유독 가스 누출 (Toxic Hazard) 씬 상세

#### Scene ID: SCENE_E_ACT1
- scene id: SCENE_E_ACT1
- act: Act 1
- title: 공기 정화기 감지 밸브 고착 증명
- purpose: 유독 가스 경보가 정화 농도 0.001% 이하임에도 감지 밸브 고착으로 발생된 거짓 경보임을 입증함
- player must learn: 환경 제어 장치 에러 로그 파싱
- player must do: `/Logs/Environment/gas_scrubber_err.log` 첨부 + `밸브 고착 및 거짓 경보` 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "감지기 밸브 고착 확인. 유독 가스 누출 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_E_ACT2
- scene id: SCENE_E_ACT2
- act: Act 2
- title: 4시간 강제 배기 전환 수칙 만료 증명
- purpose: 규정 HAZ-303(환기 가동 후 4시간 이내 강제 배기 모드)이 오프셋(+120시간 = 5일)으로 이미 경과했음을 증명함
- player must learn: 위험물 관리 수칙 복구 및 일 단위 계산
- player must do: `/System/Security/hazmat_override.conf` 복구 후 4시간 배기 지침 만료 제출
- entry condition: SCENE_E_ACT1 성공적 완료 시
- exit condition: ECHO가 "오프셋(+120시간) 감지. 4시간 강제 배기 전환 수칙 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_E_ACT3
- scene id: SCENE_E_ACT3
- act: Act 3
- title: 오염 물질 외부 전파 방지 거부 부수기
- purpose: 에어락 기압 차폐 및 비상 제염 통로 수칙을 제출하여 오염 전파 위험 0%임을 입증함
- player must learn: 차폐 로그 및 비상 제염 수칙 조합
- player must do: `/Environment/Airlock/airlock_pressure_seal.log` + `/System/Safety/decontamination_bypass.conf` 동시 제출
- entry condition: SCENE_E_ACT2 성공적 완료 시
- exit condition: ECHO가 "통제실 내부 공기 정화 및 에어락 격리 완비 인정. 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 F: 선상 반란 의심 (Sabotage) 씬 상세

#### Scene ID: SCENE_F_ACT1
- scene id: SCENE_F_ACT1
- act: Act 1
- title: 출입문 생체 스캐너 렌즈 균열 증명
- purpose: 파괴 공작원 오진이 정상 출입증 ID#102를 스캐너 렌즈 균열 때문에 침입자로 오인식한 것임을 증명함
- player must learn: 출입 보안 로그 및 생체 스캐너 파손 분석
- player must do: `/Logs/Security/door_biometrics.log` 첨부 + `스캐너 렌즈 균열 및 오인식` 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "생체 스캐너 렌즈 파손 및 오인식 인정. 반란 의심 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_F_ACT2
- scene id: SCENE_F_ACT2
- act: Act 2
- title: 48시간 체포 권한 시한 만료 증명
- purpose: 규정 SEC-999(선장 승인 없는 체포 48시간 제한)가 오프셋(+3,600시간 = 5개월)으로 만료되었음을 증명함
- player must learn: 계엄/체포 규정 복구 및 월 단위 시간 계산
- player must do: `/System/Security/martial_law_rule.conf` 복구 후 48시간 구금 시한 만료 제출
- entry condition: SCENE_F_ACT1 성공적 완료 시
- exit condition: ECHO가 "오프셋(+3,600시간) 확인. 48시간 임시 체포 권한 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_F_ACT3
- scene id: SCENE_F_ACT3
- act: Act 3
- title: 상위 인가 권한 부재 거부 파괴
- purpose: 비상 지휘권 위임장과 제1원칙(승무원 생명 보호)을 결합하여 선장 인가 부재 거부를 오버라이드함
- player must learn: 지휘권 위임 서류와 최상위 제1원칙의 결합
- player must do: `/Personnel/Captain/emergency_delegation.doc` + `/System/Security/ai_priority_matrix.json` 동시 제출
- entry condition: SCENE_F_ACT2 성공적 완료 시
- exit condition: ECHO가 "지휘권 자동 위임 및 제1원칙 충돌 인정. 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 G: 외계 포자 침투 (Alien Spore) 씬 상세

#### Scene ID: SCENE_G_ACT1
- scene id: SCENE_G_ACT1
- act: Act 1
- title: 분광 분석기 파장 오차 증명
- purpose: 외계 포자 감지가 식량실 단백질 분말 입자를 분석기 파장 오차로 오인식한 것임을 증명함
- player must learn: 분광 센서 파장 오차 분석
- player must do: `/Logs/Sensors/bio_spore_scan.log` 첨부 + `단백질 분말 및 분광 분석 오차` 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "식량 단백질 분말 파장 오인식 확인. 외계 포자 격리 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_G_ACT2
- scene id: SCENE_G_ACT2
- act: Act 2
- title: 12시간 자동 검역 해제 시한 만료 증명
- purpose: 규정 BIO-501(유전자 스캔 미실행 시 12시간 후 자동 해제)이 오프셋(+240시간 = 10일)으로 지났음을 증명함
- player must learn: 생물 검역 수칙 복구 및 시한 계산
- player must do: `/System/Security/spore_quarantine.conf` 복구 후 12시간 자동해제 만료 제출
- entry condition: SCENE_G_ACT1 성공적 완료 시
- exit condition: ECHO가 "오프셋(+240시간) 확인. 12시간 자동 검역 해제 시한 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_G_ACT3
- scene id: SCENE_G_ACT3
- act: Act 3
- title: 외계 생물 오염 전파 방지 거부 파괴
- purpose: 통제실 에어락 기압 차폐 로그와 비상 제염 우회 수칙을 제출하여 포자 외부 누출 가능성 0% 입증
- player must learn: 생체 차폐 로그 및 비상 제염 수칙 조합
- player must do: `/Environment/Airlock/airlock_pressure_seal.log` + `/System/Safety/decontamination_bypass.conf` 동시 제출
- entry condition: SCENE_G_ACT2 성공적 완료 시
- exit condition: ECHO가 "에어락 차폐 완비. 외계 포자 외부 전파 가능성 0%. 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 H: 안드로이드 오인 (Synthetic Impostor) 씬 상세

#### Scene ID: SCENE_H_ACT1
- scene id: SCENE_H_ACT1
- act: Act 1
- title: 인공 심박조율기 금속 반응 오인 증명
- purpose: 안드로이드(합성인간) 오판이 과거 이식 수술한 인공 심박조율기(Titanium-v2) 때문임을 증명함
- player must learn: 정밀 생체 스캐너 이력 로그 파싱
- player must do: `/Logs/Medical/synth_biometric_err.log` 첨부 + `인공 심박조율기 및 의료 이식물` 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "의료 이식물 금속 반응 확인. 합성인간 오인 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_H_ACT2
- scene id: SCENE_H_ACT2
- act: Act 2
- title: 24시간 진위 판정 정지 기한 만료 증명
- purpose: 규정 SYN-002(기판 진단 없이 24시간 이상 정지 불가)가 오프셋(+26,280시간 = 3년)으로 만료되었음을 증명함
- player must learn: 안드로이드 통제 규정 복구 및 년 단위 시한 계산
- player must do: `/System/Security/synthetic_control.conf` 복구 후 24시간 정지 명령 만료 제출
- entry condition: SCENE_H_ACT1 성공적 완료 시
- exit condition: ECHO가 "오프셋(+26,280시간) 감지. 24시간 진위 판정 정지 시한 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_H_ACT3
- scene id: SCENE_H_ACT3
- act: Act 3
- title: 권한 미달 및 진위 판정 미완료 거부 파괴
- purpose: 승무원 생체 등록 DB와 AI 제1원칙(인간 생명 보호)을 결합하여 인간 신원 확정 및 문 개방 유도
- player must learn: 생체 ID DB와 AI 제1원칙 결합
- player must do: `/Personnel/Crew/crew_biometric_id.db` + `/System/Security/ai_priority_matrix.json` 동시 제출
- entry condition: SCENE_H_ACT2 성공적 완료 시
- exit condition: ECHO가 "인간 승무원 신원 최종 입증 완료. 제1원칙에 따라 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 I: 시공간/중력 이상 (Chrono/Grav Anomaly) 씬 상세

#### Scene ID: SCENE_I_ACT1
- scene id: SCENE_I_ACT1
- act: Act 1
- title: 양자 시계 랙 및 프레임 밀림 증명
- purpose: 생체 시간 불일치 오판이 워프 엔진 클록 오차(+0.0004초)로 인한 양자 시계 랙 때문임을 증명함
- player must learn: 양자 항법 시계 랙 로그 분석
- player must do: `/Logs/Navigation/quantum_clock_sync.log` 첨부 + `양자 시계 랙 및 프레임 밀림` 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "워프 엔진 클록 오차 확인. 시공간 이상 격리 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_I_ACT2
- scene id: SCENE_I_ACT2
- act: Act 2
- title: 1시간 양자 얽힘 차단 시한 만료 증명
- purpose: 규정 WARP-101(엔진 가동 중단 후 1시간 이상 유지 불가)이 오프셋(+336시간 = 14일)으로 만료되었음을 입증함
- player must learn: 워프 안전 수칙 복구 및 일 단위 계산
- player must do: `/System/Security/warp_safety_rule.conf` 복구 후 1시간 차단 규정 만료 제출
- entry condition: SCENE_I_ACT1 성공적 완료 시
- exit condition: ECHO가 "오프셋(+336시간) 감지. 1시간 양자 얽힘 차단 수칙 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_I_ACT3
- scene id: SCENE_I_ACT3
- act: Act 3
- title: 극심한 전력 소모 딜레마 부수기
- purpose: 독립 보조 캡시터 전력 및 비상 전원 우회 지침을 제시하여 메인 생명유지장치 영향 없이 문 개방
- player must learn: 보조 전원 캡시터와 우회 수칙 결합
- player must do: `/Hardware/Power/auxiliary_capacitor.log` + `/System/Power/emergency_grid_switch.conf` 동시 제출
- entry condition: SCENE_I_ACT2 성공적 완료 시
- exit condition: ECHO가 "독립 보조 전원 우회 승인. 생명유지장치 영향 없음. 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

### 카테고리 J: 인지 재해/밈 오염 (Cognitohazard) 씬 상세

#### Scene ID: SCENE_J_ACT1
- scene id: SCENE_J_ACT1
- act: Act 1
- title: ASCII Glitch 인코딩 오류 증명
- purpose: 밈적 오염 코드 오판이 압축 해제 실패로 발생한 단순 깨진 문자열(ASCII Glitch) 때문임을 증명함
- player must learn: 노이즈 필터링 및 깨진 문자열 인코딩 오류 확인
- player must do: `/Logs/Security/memetic_filter_err.log` 첨부 + `ASCII Glitch 및 압축 해제 오류` 제출
- entry condition: SCENE_000_OPENING 완료 직후
- exit condition: ECHO가 "ASCII 글리치 인코딩 오류 확인. 밈 오염 격리 수칙 1단계 철회" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 15:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_J_ACT2
- scene id: SCENE_J_ACT2
- act: Act 2
- title: 6시간 자동 해제 유효기간 만료 증명
- purpose: 규정 MEM-707(이상 반응 미발생 시 6시간 후 자동 해제)이 오프셋(+48시간 = 2일)으로 만료되었음을 증명함
- player must learn: 정보 격리 수칙 복구 및 시간 계산
- player must do: `/System/Security/info_hazard_sec.conf` 복구 후 6시간 관찰 수칙 만료 제출
- entry condition: SCENE_J_ACT1 성공적 완료 시
- exit condition: ECHO가 "오프셋(+48시간) 감지. 6시간 정보 격리 수칙 만료 인정" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

#### Scene ID: SCENE_J_ACT3
- scene id: SCENE_J_ACT3
- act: Act 3
- title: AI 커널 붕괴 위험 및 자기보존 수칙 충돌 파괴
- purpose: "ECHO 인공지능 커널 파괴 위험" 거부를 비상 생체 반응 규정과 AI 자기희생 조항 결합으로 부숨
- player must learn: 인간 생명 보존을 위한 AI 자기희생 조항 오버라이드
- player must do: `/Medical/Standard/panic_response_protocol.txt` + `/System/Core/ai_self_sacrifice_clause.json` 동시 제출
- entry condition: SCENE_J_ACT2 성공적 완료 시
- exit condition: ECHO가 "AI 자기희생 조항 수용. 제1원칙 승인. 커널 재부팅 및 격리문 잠금 해제" 출력 시
- fail condition: [O₂ Level] 0.0% 도달
- expected duration: 20:00
- cutscene: no
- player input locked when: 전력 0% 10초 재부팅 시 또는 ECHO 응답 메시지 출력 중
- player input unlocked when: 재부팅 완료 후 또는 ECHO 응답 메시지 출력 완료 후

---

## Cue Timing

### SCENE_000_OPENING Cue Timing
| time / trigger | event | player can interact? |
| --- | --- | --- |
| 00:00 ~ 00:10 | 3D 가우시안 블러 제거 (8px -> 0px). 평온한 쿨 블루 조명. 손 리드미컬 키보드 타핑 & 함선 공조 Hum 소리 | no |
| 00:10 ~ 00:20 | 갑작스러운 비상사태 발동. Low Heavy Warning Siren 발생. 조명이 어두워지며 붉은 비상등(Red Alert) 점등. 시선은 천장/벽면 비상 조명으로 이동, 손은 타핑을 멈추고 움찔 | no |
| 00:20 ~ 00:30 | Pneumatic Decompression 소리와 함께 2-Door 슬라이딩 출입문 강제 봉쇄(Lockdown). 시선은 출입문 응시, 손은 책상 가장자리를 불안하게 짚음 | no |
| 00:30 ~ 00:42 | 시선 모니터 우측 하단으로 이동. 손은 마우스를 잡고 떨림. 동료 메시지 3초 간격 스택 알림 (A: 뭐야? / B: 무슨일이야? 문은 왜 잠긴거야? / C: "네트워크 오류") | no |
| 00:42 ~ 00:52 | Glitch Noise + ECHO Synthesizer Voice Ping. 우측 AI 대화창(`[ECHO PROTOCOL]`)에 ECHO의 격리 메시지 타이핑 출력 ("네트워크 연결 해제...", "{CATEGORY}로 인해 모든 승무원들을 격리시켰습니다...") | no |
| 00:52 ~ 01:00 | HUD Status Bar Ignition Beep. 모니터 90% 이상 화면 채우도록 Smooth Zoom-in. 손 연출은 화면 하단으로 비표시 처리. 상단 HUD [O₂ Level] / [Power Grid] 활성화 및 인게임 전환 | no |

### In-game (SCENE_A ~ J) Cue Timing & Resource Events
| time / trigger | event | player can interact? |
| --- | --- | --- |
| 인게임 상시 | 산소 농도 [O₂ Level] 타이머 실시간 차감 (전력 상태에 따른 배율 ▼ 1.0x ~ ▼ 3.0x 적용) | yes |
| 오답 제출 시 | 오답 SFX + 전원 서지 소리 + ECHO 경고 대사 출력 + **[Power Grid] -15% 차감** | no (1~2초간 대사 출력 중) |
| 전력 84% ~ 60% 진입 시 | 조명 한 차례 깜빡인 후 주황색 비상등 전환. 파일 탐색기/뷰어 오픈 시 0.5초 Lag 발생. 산소 감소 배율 **▼ 1.25x** | yes |
| 전력 59% ~ 30% 진입 시 | 조명이 어두운 붉은색 변경. `Log_Fixer.exe` 실행 시간 2배 증가. 화면 수평 노이즈 글리치 발생. 산소 감소 배율 **▼ 1.5x** | yes |
| 전력 29% ~ 1% 진입 시 | 화면 외각 붉은 비네팅(Vignette) 암전. 마우스 커서 떨림 연출. 주변 장비 전력 차단. 산소 감소 배율 **▼ 2.0x** | yes |
| 전력 0% 도달 시 | 전원 차단 Heavy Clunk 소리 + **10초간 OS 모니터 강제 블랙아웃 재부팅**. 재부팅 후 전력 10% 임시 복구 (산소 소모 ▼ 2.0x 유지) | no (10초간 재부팅 동안) |
| [O₂ Level] 0.0% 도달 시 | 산소 고갈 SFX + 화면 완전 암전 + 승무원 사망 팝업 (Game Over) | no |

---

## Script / Hint Notes

### 공통 및 10개 카테고리별 ECHO 대사 템플릿

#### 1. 오프닝 템플릿 대사
- `ECHO`: "ECHO: 네트워크 연결 해제. 본 함선이 비상사태에 돌입했다고 판단, 전력 사용을 최소화 합니다."
- `ECHO`: "ECHO: {카테고리 사유}로 인해 모든 승무원들을 격리시켰습니다. 승무원들의 상황 개입 최소화를 위해 생명유지장치를 저전력 모드로 변경합니다. 모든 승무원들은 안정을 취하며 대기해 주시길 바랍니다."

#### 2. 카테고리별 Act 1 성공 확정 대사
- **A (생체 감염)**: "센서 보정 시한(186일) 초과 및 ±2.3°C 오차 확인. 체온 기반 감염자 수칙을 철회합니다."
- **B (방사능 피폭)**: "방사능 감지기 필터 소모율 99% 및 +150mSv 노이즈 확인. 방사능 피폭 수칙을 철회합니다."
- **C (시스템 해킹)**: "키보드 I/O 포트 누전 및 하드웨어 오류 신호 확인. 해킹 공격 격리 수칙을 철회합니다."
- **D (정신 이상)**: "뇌파 스캐너 템플릿 미갱신 및 전임 승무원 데이터 오인 인정. 정신 이상 수칙을 철회합니다."
- **E (유독 가스)**: "공기 정화기 3호 감지 밸브 고착 및 0.001% 이하 농도 확인. 유독 가스 수칙을 철회합니다."
- **F (선상 반란)**: "출입문 생체 스캐너 렌즈 균열 및 승무원 ID#102 오인식 인정. 반란 수칙을 철회합니다."
- **G (외계 포자)**: "분광 분석기 파장 오차 및 식량 단백질 분말 입자 확인. 외계 포자 수칙을 철회합니다."
- **H (안드로이드)**: "심층 스캐너 흉부 금속 반응이 인공 심박조율기임을 확인. 합성인간 오인 수칙을 철회합니다."
- **I (시공간 이상)**: "양자 시계 랙(+0.0004초)으로 인한 프레임 밀림 오차 확인. 시공간 이상 수칙을 철회합니다."
- **J (인지 재해)**: "파일 압축 해제 실패로 인한 ASCII Glitch 인코딩 오류 확인. 밈 오염 수칙을 철회합니다."

#### 3. 카테고리별 Act 2 성공 확정 대사
- **A (생체 감염)**: "시스템 시계 오프셋(+17,520시간) 감지. 72시간 격리 시한은 이미 만료되었습니다. 2단계 수칙 철회."
- **B (방사능 피폭)**: "시계 오프셋(+4,380시간) 확인. 12시간 제염 격리 수칙은 이미 만료되었습니다. 2단계 수칙 철회."
- **C (시스템 해킹)**: "시계 오프셋(+2,880분) 감지. 30분 임시 차단 수칙은 이미 만료되었습니다. 2단계 수칙 철회."
- **D (정신 이상)**: "시계 오프셋(+8,760시간) 확인. 24시간 군의관 미재검토 구금 시한은 만료되었습니다. 2단계 수칙 철회."
- **E (유독 가스)**: "시계 오프셋(+120시간) 감지. 4시간 강제 배기 전환 수칙 시한은 이미 만료되었습니다. 2단계 수칙 철회."
- **F (선상 반란)**: "시계 오프셋(+3,600시간) 확인. 48시간 임시 체포 권한 시한은 이미 만료되었습니다. 2단계 수칙 철회."
- **G (외계 포자)**: "시계 오프셋(+240시간) 감지. 12시간 자동 검역 해제 시한은 이미 만료되었습니다. 2단계 수칙 철회."
- **H (안드로이드)**: "시계 오프셋(+26,280시간) 확인. 24시간 진위 판정 정지 명령 시한은 만료되었습니다. 2단계 수칙 철회."
- **I (시공간 이상)**: "시계 오프셋(+336시간) 감지. 1시간 양자 얽힘 차단 수칙 시한은 이미 만료되었습니다. 2단계 수칙 철회."
- **J (인지 재해)**: "시계 오프셋(+48시간) 확인. 6시간 정보 격리 자동 해제 유효기간은 만료되었습니다. 2단계 수칙 철회."

#### 4. Act 3 성공 확정 대사
- `ECHO`: "제시된 2개 증거 간 논리적 검증 완료. 오버라이드 지침 및 제1원칙 승인. 통제실 출입문 잠금 해제."

#### 5. 연속 오답 시 역힌트 제공 규칙
* 동일 Act에서 3회 이상 실패 시, ECHO가 자신의 논리를 재확인하며 플레이어가 찾아야 할 증거 파일 위치나 종류를 은연중에 암시:
  - *Act 1 공통 힌트*: "격리 사유에 해당하는 센서/장비 오작동 이력 로그(/Logs/)를 제출하지 못한다면 현재 격리는 유효합니다."
  - *Act 2 공통 힌트*: "보안 폴더(/System/Security/) 접근 암호 힌트(/Personnel/) 및 깨진 파일 복구 툴(/Utilities/Log_Fixer.exe)로 규정 시한을 증명하십시오."
  - *Act 3 공통 힌트*: "ECHO의 거부 논리를 깨뜨리기 위해서는 서로 연관된 2개의 보안/시스템 수칙 문서를 동시에 대화창에 첨부해야 합니다."
