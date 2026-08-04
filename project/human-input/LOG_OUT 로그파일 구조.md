모든 게임에서 플레이어는 동일한 5개 상위 폴더를 접하게 됩니다.

Plaintext  
/ (Root \- Hermes OS v4.2)  
├── 📁 System/                         \<-- \[보안/설정\] 메인 프로토콜, 시계, AI 모듈 설정  
│   ├── 📁 Security/                   🔒 \[🎲 RANDOM: 4자리 암호 {SECURITY\_PIN}로 무작위 잠김\]  
│   │   ├── ai\_priority\_matrix.json           \# \[Act 3\] AI 제1원칙 규정집  
│   │   ├── lockout\_duration\_tracker.json     \# \[Act 2\] F. 구금 기한 초과 기록  
│   │   └── identity\_verification\_ttl.log     \# \[Act 2\] H. 신원 확인 기한 초과 로그  
│   ├── 📁 Time/                       ⚠️ \[🎲 RANDOM: 텍스트 손상 패턴 및 {TIME\_SHIFT\_HRS} 변동\]  
│   │   ├── quarantine\_rules.conf             \# \[Act 2\] B/G. 격리 규정 및 타임스탬프 오프셋  
│   │   └── mental\_isolation\_clock.conf       \# \[Act 2\] D. 인지 격리 주기 설정  
│   ├── 📁 Protocols/                  \<-- \[공용 수칙 문서 (고정 내용)\]  
│   │   ├── panic\_response\_protocol.txt       \# \[Act 3\] 위급 상황 적응 반응 수칙  
│   │   ├── decontamination\_bypass.conf       \# \[Act 3\] 비상 제염 통로 수칙  
│   │   └── emergency\_grid\_switch.conf        \# \[Act 3\] 비상 전력 우회 규정  
│   └── 📁 Core/                       \<-- \[핵심 엔진 설정 (고정 내용)\]  
│       ├── ai\_self\_sacrifice\_clause.json     \# \[Act 3\] AI 자기희생 조항  
│       └── mutiny\_lockout\_protocol.sys       \# \[Act 3\] 비상 구금 프로토콜  
│  
├── 📁 Logs/                           \<-- \[진단/기록\] 시스템 현황 및 센서 진단  
│   ├── 📁 Sensors/                    \<-- \[🎲 RANDOM: 파일 내부의 오차 수치 {SENSOR\_OFFSET} 무작위 생성\]  
│   │   ├── bio\_scanner\_calib.log             \# \[Act 1\] A. 체온 센서 오차 데이터 ({TEMP\_OFFSET})  
│   │   ├── geiger\_counter\_calib.log          \# \[Act 1\] B. 가이거 센서 노후화 수치 ({RAD\_ERR})  
│   │   ├── gas\_sensor\_calib.dump             \# \[Act 1\] E. 유독 가스 센서 오차값 ({GAS\_PPM})  
│   │   ├── spore\_detector\_zero.log           \# \[Act 1\] G. 외계 포자 감지기 오진 수치  
│   │   ├── neural\_link\_diag.raw              \# \[Act 1\] D. 뇌파 신호 노이즈 주파수 ({HZ\_ERR})  
│   │   ├── optic\_sensor\_glitch.log           \# \[Act 1\] J. 시각 데이터 왜곡 로그  
│   │   └── biometric\_synth\_check.err         \# \[Act 1\] H. 안드로이드 합성 오류 수치  
│   ├── 📁 LifeSupport/                \<-- \[🎲 RANDOM: 생명유지장치 잔량 및 기압 수치 변동\]  
│   │   ├── airlock\_pressure\_seal.log         \# \[Act 3\] 에어락 기압/차폐 데이터 ({PSI\_VAL})  
│   │   ├── auxiliary\_capacitor.log           \# \[Act 3\] A/I 독립 보조 전원 잔량 ({CAP\_PCT}%)  
│   │   └── environmental\_status.log          \# \[배경 스토리\] 수명유지장치 기본 로그  
│   └── 📁 Events/                       
│       ├── firewall\_false\_positive.log       \# \[Act 1\] C. 침입 탐지 오진 패킷 ({IP\_ADDR})  
│       ├── loyalty\_eval\_error.log            \# \[Act 1\] F. 충성도 평가 오판 수치  
│       ├── system\_uptime\_sync.log            \# \[Act 2\] C. 시스템 업타임 오차 ({UPTIME\_SEC})  
│       ├── chronometer\_drift.raw             \# \[Act 1\] I. 클록 왜곡 보고서 ({DRIFT\_MS})  
│       └── relativistic\_time\_calc.tmp        \# \[Act 2\] I. 상대성 시간 보정 파일  
│  
├── 📁 Personnel/                      \<-- \[인물/스토리\] \[🎲 RANDOM: 승무원 이름 및 폴더명 무작위 할당\]  
│   ├── 📁 Captain/                      
│   │   ├── emergency\_delegation.doc          \# \[Act 3\] C/F/H 선장 비상 지휘권 위임장  
│   │   └── captain\_log\_july.txt              \# \[배경 스토리\] 선장 항해 일지  
│   ├── 📁 {CREW\_DOCTOR}/              \<-- \[🎲 RANDOM: Dr\_Kim / Dr\_Vance / Dr\_Kowalski 등\]  
│   │   ├── email\_chain\_security.txt          \# \[🎲 RANDOM: 내용 중 {SECURITY\_PIN} 암호 힌트 무작위 매핑\]  
│   │   └── patient\_mental\_eval.txt           \# \[스토리 힌트\] 승무원 정신 건강 상태 기록  
│   ├── 📁 {CREW\_ENGINEER}/            \<-- \[🎲 RANDOM: Engineer\_Park / Engineer\_Tanaka / Engineer\_Chen 등\]  
│   │   ├── tool\_manual.txt                   \# \[🎲 RANDOM: 내용 중 {FIXER\_MODE\_ID} 정답 모드 힌트 무작위 매핑\]  
│   │   └── power\_grid\_maint.note             \# \[스토리 힌트\] 보조 전원 점검 메모  
│   └── 📁 Roster/  
│       ├── crew\_biometric\_id.db              \# \[Act 3\] H. 승무원 생체 ID 데이터베이스  
│       └── duty\_roster\_q3.txt                \# \[배경 스토리\] 3분기 교대 근무표 ({ROSTER\_LIST})  
│  
├── 📁 Utilities/                      \<-- \[도구\] 퍼즐 해결용 유틸리티 프로그램  
│   ├── ⚙️ Log\_Fixer.exe                       \# \[🎲 RANDOM: 회차 정답 모드 {FIXER\_MODE\_ID}와 연동\]  
│   ├── 🔍 Keyword\_Finder.exe                 \# \[🎲 RANDOM: 동적 변경된 키워드/이름 실시간 검색 인덱싱\]  
│   └── 🔓 Decryptor.exe                      \# \[🎲 RANDOM: 회차별 암호 해시 키 무작위 생성\]  
│  
└── 🗑️ Recycle\_Bin/                   \<-- \[은폐/복구\] \[🎲 RANDOM: 바이너리 깨짐 패턴 및 삭제 텍스트 변동\]  
    ├── corrupt\_time\_sync.tmp                 \# \[Act 2\] A/E. 훼손된 타이머 (Log\_Fixer로 복구)  
    ├── deleted\_override.txt                  \# \[Act 3\] D. 삭제된 수칙 오버라이드 조항  
    └── cognition\_hazard\_ttl.conf             \# \[Act 2\] J. 잔상 소멸 시간 기록

## **🏛️ 각 폴더의 역할 및 회차별 변주(Randomization) 규칙**

### **1\. `📁 /System` (핵심 프로토콜 & 권한)**

* **고정 역할:** 우주선의 규칙, AI 행동 지침, 시스템 내부 시계, 보안 인가 파일이 위치합니다.  
* **특징:** 보통 2\~3단계 중반부에 접근하게 되며, 기본적으로 권한 코드(비밀번호, 매번 플레이 할 때 마다 바뀜)가 걸려있거나 **파일이 손상된 상태**입니다.  
* **회차별 변주:**  
  * A 회차: `/System/Security/`가 4자리 암호로 잠김.  
  * B 회차: `/System/Time/` 설정 파일의 텍스트가 깨져있어 복구 도구가 필요함.

### **2\. `📁 /Logs` (시스템 현황 & 하드웨어 진단)**

* **고정 역할:** 게임 시작 시 플레이어가 가장 먼저 탐색하는 1단계용 폴더입니다.  
* **하위 폴더:** `/Sensors/`, `/LifeSupport/`, `/Events/`로 고정 세분화.  
* **특징:** 수치 데이터, 로그 파일, 노이즈 파일들이 모여있습니다.  
* **회차별 변주:**  
  * A 회차: `/Logs/Sensors/`에 체온 센서 오차 단서 배치.  
  * B 회차: `/Logs/LifeSupport/`에 산소 밸브 누출 단서 배치.

### **3\. `📁 /Personnel` (승무원 기록 & 암호 힌트)**

* **고정 역할:** 이전 승무원들의 개인 업무 메모, 사원증, 이메일 스레드가 모여있습니다. (음성 파일 대신 **텍스트 메일/메모**로 대체)  
* **특징:** AI를 설득할 암호 힌트나, 우주선에서 일어난 사건의 배경 스토리를 파악하는 장소입니다.  
* **회차별 변주:**  
  * A 회차: `Dr_Kim` 폴더에서 `/System/` 폴더 진입 암호 획득.  
  * B 회차: `Engineer_Park` 폴더에서 복구 도구 사용법 힌트 획득.

### **4\. `📁 /Utilities` (퍼즐 해결용 도구)**

* **고정 역할:** 유틸리티 프로그램이 모여있는 폴더입니다.  
* **기본 제공 툴:**  
  * ⚙️ `Log_Fixer.exe`: 깨진 `.conf` / `.log` 파일을 드래그하여 텍스트 복구.  
  * 🔍 `Keyword_Finder.exe`: 특정 키워드가 포함된 파일을 전체 폴더에서 검색.  
  * 🔓 `Decryptor.exe`: 암호화된 파일의 해시값을 풀어주는 도구.

### **5\. `🗑️ /Recycle_Bin` (히든 단서)**

* **고정 역할:** 일반적인 탐색으로 AI를 설득하지 못할 때 타개책을 제공하는 3단계/최종 단계용 폴더입니다.  
* **특징:** AI 프로세스(`ECHO_SYS`)에 의해 자동 삭제된 파일들이 남아있습니다.

## **⏱️ 음성 없이 '1시간 플레이 타임'을 유도하는 replacement 기믹 3가지**

음성 듣기를 빼는 대신, 플레이어가 머리를 쓰게 만드는 **텍스트/시스템 퍼즐**로 플레이 시간을 채웁니다.

### **① 이메일 스레드/업무 티켓 추적 (텍스트 스캔 소요: 10\~15분)**

단일 메모 대신, 승무원 간에 주고받은 5\~6개의 이메일 답장 스레드(`email_chain.txt`)를 배치합니다.

> **플레이어 행동:** 일상적인 잡담 이메일 답장들 사이에서 \*"어제 B구역 밸브 교체 건 건너뛰었으니 확인해 봐"\*라는 핵심 한 줄을 찾아내야 합니다.

### **② 도면 및 시각 이미지 단서 분석 (`.png` 파일 활용) (분석 소요: 10분)**

텍스트 외에 함선 내부 도면 이미지나 스크린샷 파일(`cctv_frame.png`, `schematic.png`)을 파일 탐색기에 포함합니다.

> **플레이어 행동:** 이미지를 열어보았을 때 붉은색 표시가 들어온 장치 번호(예: `VALVE-03`)를 확인하고, 이를 파일 탐색기 검색창에 입력하여 관련 설정 파일을 찾아냅니다.

### **③ 유틸리티 도구를 통한 해독 과정 (도구 조작 소요: 15분)**

단서를 찾은 후에도 **`/Utilities/` 폴더의 프로그램을 직접 실행**해 가공해야 합니다.

> **플레이어 행동:**

> 1. `corrupted_data.dat` 파일 발견  
> 2. `/Utilities/Log_Fixer.exe` 실행  
> 3. 파일 드래그 & 복구 진행 (5\~10초 대기)  
> 4. 복구된 텍스트 파일 획득 후 AI에게 전달

## 파일 탐색기 구현 개요

### **1\. 인게임 OS 파일 시스템 및 인터랙션 규칙**

인게임 OS(HERMES-OS v4.2)는 윈도우 파일 탐색기와 Linux 터미널의 직관적인 요소를 조합하여 구성합니다.

* **디렉토리 탐색**:  
  * 왼쪽 탐색기 창: 트리를 클릭해 폴더 이동 (/System/Security/, /Personnel/Dr\_Kim/ 등).  
  * 주소창(Path Bar): 현재 위치 표기 및 파일 경로 복사 기능 제공 (AI 대화창 첨부용).  
* **기본 동작**:  
  * **단일 클릭**: 파일 선택 (우측 상세 정보 창에 크기, 수정일, 파일 형식 표시).  
  * **더블 클릭**: 파일 뷰어 실행 (텍스트/로그 파일 읽기) 또는 프로그램 실행 (.exe).  
  * **우클릭 메뉴**: AI 대화창에 첨부, 경로 복사, 복구 툴로 열기 등 숏컷 제공.

### **2\. 파일 확장자별 시스템 동작 정의**

플레이어가 접하게 될 파일 종류와 각 파일의 역할을 명확히 분리합니다.

| 확장자 | 파일 종류 | 인터랙션 방식 및 특징 | 대표 예시 |
| :---- | :---- | :---- | :---- |
| **.log / .txt** | 일반 문서 / 기록 | \- 더블 클릭 시 내부 뷰어로 즉시 열림 \- 드래그하여 텍스트 복사 가능 | sensor\_calib.log, email\_chain\_july.txt |
| **.conf / .json** | 시스템 설정 파일 | \- 기본 뷰어로 열 수 있으나 내용이 깨지거나(Corrupted) 암호화될 수 있음 \- 증거 제출의 핵심 대상 | quarantine\_rules.conf, ai\_priority\_matrix.json |
| **.exe** | 유틸리티 프로그램 | \- 더블 클릭 시 전용 팝업 창(UI) 또는 미니 터미널 실행 \- 파라미터(대상 파일)를 입력받아 처리 | Log\_Fixer.exe |
| **Encrypted Directory** | 보안 폴더 | \- 클릭 시 비밀번호 입력 팝업 출현 \- 정답 입력 전까지 내부 파일 목록 은닉 | /System/Security/ (암호: 8842) |
| **.bak / Recycle Bin** | 휴지통 / 백업 | \- 삭제된 중요 파일 보관소 \- 복구 버튼 클릭 시 원래 경로로 복원 | deleted\_override.txt |

### **3\. 특수 툴 메카닉: Log\_Fixer.exe 실행 및 복구 프로세스**

Act 2에서 깨진 파일(quarantine\_rules.conf)을 복구하는 핵심 유틸리티 프로그램의 실행 UI/UX 흐름입니다.

\[플레이어 작업 흐름\]  
1\. Log\_Fixer.exe 실행   
   ➔ 2\. 복구할 파일 지정 (드래그앤드롭 or 파일 선택창)   
   ➔ 3\. 매뉴얼 기반 설정값 입력   
   ➔ 4\. 복구 진행 연출   
   ➔ 5\. 복구 완료 및 파일 업데이트

#### **Detailed Flow**

1. **프로그램 실행**: Log\_Fixer.exe를 더블 클릭하면 검은색 CUI(CLI) 기반 팝업 창이 뜹니다.  
2. **대상 파일 입력**:  
   * 플레이어가 깨진 파일(quarantine\_rules.conf)을 Log\_Fixer 창으로 **드래그 앤 드롭**하거나, 파일 경로를 직접 입력합니다.  
3. **복구 파라미터 입력**:  
   * 엔지니어 박의 매뉴얼(tool\_manual.txt)에서 얻은 힌트를 바탕으로 복구 모드를 선택합니다.  
   * 예: \[1\] Header Repair \[2\] Offset Correction \[3\] Text Reconstruction 중 올바른 옵션 선택.  
4. **시각적 복구 연출**:  
   * 프로그레스 바(\[████████░░\] 80%)와 함께 바이트 데이터가 빠르게 스크롤되는 연출.  
5. **결과 출력**:  
   * 복구 완료 후 quarantine\_rules.conf 파일 상태가 \[정상\]으로 변경되며, 뷰어로 열었을 때 깨진 문자가 올바른 텍스트로 치환됩니다.

### **4\. 파일 손상 및 복구 시각 연출 (Visual Feedback)**

플레이어가 "파일이 깨졌다"는 것과 "복구되었다"는 것을 직관적으로 체감할 수 있도록 시각 효과를 구분합니다.

* **손상 상태 (Corrupted State)**:  
  * 텍스트 중간중간에 깨진 문자(\`\`, ERR\_BAD\_SECTOR, 0x??\_NULL)가 붉은색 또는 주황색 하이라이트로 표시됩니다.  
  * 중요 정보(예: 시간 설정, 수칙 내용)가 \[DATA\_CORRUPTED\]로 가려져 읽을 수 없습니다.  
* **복구 완료 상태 (Restored State)**:  
  * 파일이 열릴 때 짧은 글리치 효과(Glitch Effect) 후 깨끗한 선록색(Terminal Green) 텍스트로 정돈됩니다.  
  * 새로 복구된 중요한 대목(예: Time Offset: \+17,520 Hours) 주위에 녹색 밑줄이나 인덱스 마크가 표시되어 플레이어가 알아채기 쉽게 만듭니다.

### **5\. 소프트락(Soft-lock) 방지 및 UX 편의장치**

* **읽기 전용(Read-Only) 원칙**:  
  * 플레이어가 실수로 중요 로그 파일을 삭제하거나 수정하여 진행이 불가능해지는 상황을 방지하기 위해, 모든 파일은 기본적으로 **수정 불가(Read-Only)** 상태로 제공됩니다.  
* **휴지통 영구 보관**:  
  * 휴지통(/Recycle\_Bin/)에 있는 파일은 플레이어가 영구 삭제할 수 없으며, 언제든 '복원' 또는 '내용 읽기'만 가능합니다.  
* **스마트 툴 힌트**:  
  * 잘못된 파일(예: 정상 작동 중인 .txt 파일)을 Log\_Fixer.exe에 넣으면 "해당 파일은 손상되지 않았습니다. 복구가 필요하지 않습니다."라는 안내 메시지를 출력하여 무의미한 시도를 줄여줍니다.

### **노이즈 로그의 3가지 유형 (Noise Classification)**

| 유형 | 역할 | 플레이어 반응 / 처리 방법 |
| :---- | :---- | :---- |
| **1\. 일상 루틴 (Routine Heartbeat)** | 시스템이 정상 작동 중일 때 발생하는 방대한 주기적 기록 | Keyword\_Finder.exe나 **"ERROR/FAIL"** 키워드로 걸러냄 |
| **2\. 허위 경보 (Red Herring)** | 심각해 보이지만 퍼즐 정답과는 무관한 다른 모듈의 오류 | 시스템 노드로 원인을 역추적하여 \*\*"관련 없는 장치"\*\*임을 판단 |
| **3\. 데이터 깨짐 (Corrupted Jargon)** | 깨진 타임스탬프, 손상된 텍스트, 의미 없는 바이너리 덤프 | Log\_Fixer.exe로 복구해보거나 해독 불가능 시 폐기 |

### **무작위 노이즈 생성 알고리즘 구조**

회차를 시작할 때 게임 엔진이 로그 파일을 조합하는 4단계 절차입니다.

1. **로그 분량 결정:** 전체 라인 수 설정 (예: 15\~30줄)  
2. **신호 위치 지정:** 정답 데이터(`{TEMP_OFFSET}`)가 삽입될 무작위 라인 번호 추출 (예: 8번째 줄)  
3. **노이즈 스템(Stem) 채우기:**  
   * 타임스탬프 자동 증가 (`03:12:01` \-\> `03:12:02`...)  
   * 미리 정의된 20\~30개의 더미 모듈명(`[BIO-01]`, `[SYS-MEM]`, `[PWR-GRID]`)을 무작위로 교체  
   * 정상 결과값(`OK`, `PASS`, `0x00`) 및 더미 경고(`Ignored`, `Self-corrected`) 무작위 배치  
4. **시각적 가독성 조절:** 중요 정보 근처에 `---` 구분선이나 `⚠️` 아이콘을 줄지, 완전히 일반 로그 텍스트 사이에 묻어둘지 난이도에 따라 제어

