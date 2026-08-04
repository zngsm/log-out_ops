# Asset Plan Specification (Vite + React + TypeScript)

## Technical Stack & Architecture Context
* **Core Framework:** Vite + React + TypeScript
* **3D & Graphics Engine:** Three.js / React Three Fiber (R3F)
* **Audio Engine:** Howler.js / Web Audio API
* **UI Engine:** React Vanilla CSS / CSS Modules / Canvas Overlay

---

## Asset List

| asset id | type | used in scene | trigger | purpose | required | spec | format | placeholder allowed | notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| mod-control-room-3d | background | SCENE_000 ~ SCENE_006 | Scene start | 통제실 3D 공간 메쉬 및 조명 연출 | yes | GLTF/GLB (Draco Mesh) | .glb | yes | R3F 3D Canvas 공간 렌더링 |
| mod-player-hands-3d | cutscene | SCENE_000_OPENING | 00:00 ~ 00:52 | 컷씬 캐릭터 손 3D 메쉬 및 애니메이션 | yes | Rigged Skeletal Anim | .glb | yes | 00:52 줌인 시 화면 제외(비표시) |
| ui-main-menu-overlay | ui | SCENE_000_OPENING | Main Menu load | LOGOUT 로고 및 Play/Quit 2D 버튼 | yes | 1920x1080 Responsive | React Component / .svg | yes | 가우시안 블러 8px 오버레이 |
| ui-terminal-window | ui | SCENE_001 ~ SCENE_003 | In-game focus | Hermes OS 메인 터미널 듀얼 화면 | yes | 1920x1080 (90% View) | React Component / .svg | yes | 좌측 탐색기 + 우측 대화창 |
| ui-hud-bar | ui | SCENE_000 ~ SCENE_006 | 00:52 줌인 완료 | 상단 O₂ Level 및 Power Grid 게이지 | yes | 1920x60 Header UI | React Component / .svg | yes | 자원 소모 배율 붉은색 강조 |
| ui-attachment-chip | ui | SCENE_001 ~ SCENE_003 | File select | 대화창 첨부 파일 선택 칩 UI | yes | Vector / CSS Chip | React Component | yes | 클릭 시 ECHO 대화창 연동 |
| icon-explorer-set | icon | SCENE_001 ~ SCENE_003 | File Explorer | LOG, CONF, TXT, EXE, RAW 및 폴더 아이콘 | yes | 64x64 Vector | .svg / .png | yes | Hermes OS 쿨블루 스타일 |
| fx-glitch-overlay | fx | SCENE_000 ~ SCENE_003 | Caution/Warning | 화면 수평 전자 노이즈 글리치 VFX | yes | WebGL / GLSL Shader | Shader / .png | yes | 전력 59%~30% 주기적 점등 |
| fx-vignette-red | fx | SCENE_001 ~ SCENE_003 | Critical (29%~1%) | 화면 외곽 붉은 비네팅 암전 연출 | yes | 1920x1080 Overlay | .png / .webp | yes | 커서 떨림 연출 동반 |
| fx-power-particle | fx | SCENE_001 ~ SCENE_003 | Incorrect submission | 전력 차감 시 게이지 붉은 파티클 | yes | Canvas Particle | React Canvas Component | yes | 전력 -15% 차감 시 발동 |
| sfx-ambience-ship-hum | bgm | SCENE_000 ~ SCENE_003 | In-game active | 함선 공조 Hum 소리 서스펜스 앰비언스 | yes | 44.1kHz 192kbps Loop | .mp3 / .ogg | yes | Howler.js 루프 재생 |
| sfx-warning-siren | sfx | SCENE_000_OPENING | 00:10 Alarm | 비상 경보 Low Heavy Warning Siren | yes | 44.1kHz SFX | .mp3 / .ogg | yes | 전력 감소 시 주조음 변환 |
| sfx-door-lockdown | sfx | SCENE_000_OPENING | 00:20 Lockdown | 출입문 감압 및 봉쇄 Heavy Clunk | yes | 44.1kHz SFX | .mp3 / .ogg | yes | 2-Door 슬라이딩 소리 포함 |
| sfx-keyboard-typing | sfx | SCENE_000_OPENING | 00:00 Typing | 리드미컬 키보드 타핑 및 마우스 클릭 | yes | 44.1kHz SFX | .mp3 / .ogg | yes |  |
| sfx-notification-pop | sfx | SCENE_000_OPENING | 00:30 Message pop | 동료 메시지 수신 알림음 (3회) | yes | 44.1kHz SFX | .mp3 / .ogg | yes |  |
| sfx-echo-ping | sfx | SCENE_000 ~ SCENE_003 | ECHO typing | ECHO 신디사이저 핑 및 대사 타핑음 | yes | 44.1kHz SFX | .mp3 / .ogg | yes |  |
| sfx-power-surge | sfx | SCENE_001 ~ SCENE_003 | Incorrect submission | 전원 서지(Surge) 및 암전 효과음 | yes | 44.1kHz SFX | .mp3 / .ogg | yes | 전력 -15% 차감 오답 패널티 |
| sfx-success-chime | sfx | SCENE_001 ~ SCENE_003 | Success submission | 논리 입증 성공 긍정 SFX | yes | 44.1kHz SFX | .mp3 / .ogg | yes | Green Glow 연출 동반 |
| sfx-blackout-clunk | sfx | SCENE_001 ~ SCENE_003 | Power 0% reach | 전원 차단 Clunk 및 10초 무음 후 재부팅 | yes | 44.1kHz SFX | .mp3 / .ogg | yes | 10초 무음 타이머 포함 |

---

## Asset Type Guide

- `background`: 3D 통제실 메쉬 모델 (`mod-control-room-3d.glb`), 2D 배경 오버레이
- `ui`: Hermes OS 터미널, 파일 탐색기, 미리보기 뷰어, ECHO 대화창, 상단 HUD 바, 첨부 칩
- `icon`: 확장자별 파일 아이콘(LOG, CONF, TXT, EXE, RAW), 폴더 아이콘, 비상 경보 아이콘
- `portrait`: ECHO 시스템 로고 및 승무원 프로필 아바타
- `cutscene`: 오프닝 컷씬 3D 플레이어 손 메쉬 및 애니메이션 (`mod-player-hands-3d.glb`)
- `sfx`: 비상 경보, 출입문 봉쇄, 타핑음, 오답 서지, 성공 긍정음, 블랙아웃 sound
- `bgm`: 함선 공조 Hum 소리 및 전력 상태별 Low-frequency 서스펜스 앰비언스 루프
- `fx`: 수평 글리치 셰이더, 붉은 비네팅 오버레이, 전력 파티클 연출
- `document-art`: 미리보기 뷰어 내 파일 스크립트/로그/수칙 문서 뷰 템플릿

---

## Spec Notes

- **이미지 규격**:
  * 해상도: 1920x1080 (16:9 반응형 디스플레이 기준)
  * 포맷: WebP (배경/오버레이), SVG (UI 아이콘 및 레이아웃), PNG (알파 투명도 필요 요소)
- **오디오 규격**:
  * 포맷: MP3 (192kbps / CBR), OGG (Vorbis 44.1kHz - 웹 브라우저 이중 호환성 확보)
  * 재생 제어: Howler.js 또는 Web Audio API (Tone.js / AudioContext)
- **애니메이션 및 3D 규격**:
  * 3D 메쉬 포맷: `.glb` / `.gltf` (Draco Mesh Compression으로 패키징 용량 최소화)
  * 프레임레이트: 60 FPS (React Three Fiber Canvas 최적화)
- **파일명 규칙**:
  * 소문자 케밥 케이스(`kebab-case`) 및 카테고리 접두사 지정
  * 예시: `mod-control-room-3d.glb`, `ui-terminal-window.tsx`, `icon-file-log.svg`, `sfx-power-surge.mp3`

---

## Missing Assets (MVP Placeholder Policy)

- **개발 초기 Placeholder 허용 정책 (초기 MVP 실행 단계)**:
  1. `mod-player-hands-3d.glb`: 3D 손 리깅 모델 준비 전까지 카메라 줌인 이동 및 2D UI 줌인 연출로 Placeholder 대체
  2. `mod-control-room-3d.glb`: 3D 통제실 GLB 모델 준비 전까지 CSS 3D Transform / 2D WebP 배경으로 대체
  3. `sfx-*.mp3` / `sfx-*.ogg`: 음원 파일 준비 전까지 Web Audio API Synthesizer (AudioContext bleep)로 시뮬레이션 허용
