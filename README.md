# HtmlMovieToSpriteEditor 🎞️
> **웹 브라우저 기반 2D 스프라이트 슬라이서 & Gemini AI 프롬프트 대시보드**  
> **Browser-Based 2D Sprite Slicer & Gemini AI Prompt Dashboard**

이 프로젝트는 터미널 기반 AI 에이전트 파이프라인 프로젝트인 [aldegad/sprite-gen](https://github.com/aldegad/sprite-gen)에서 영감을 받아 제작되었습니다. `sprite-gen`의 스프라이트 상태 추출, 크로마키 투명화, 프레임 추출 파이프라인 개념을 **설치 없이 웹 브라우저에서 즉시 작동하는 강력한 시각적 GUI 대시보드**로 구현했습니다.

This project is heavily inspired by [aldegad/sprite-gen](https://github.com/aldegad/sprite-gen), a terminal/CLI-focused pipeline for 2D game sprite generation. We took the core concepts of state extraction, chroma keying, and frame pipelines from `sprite-gen` and transformed them into a **highly interactive, zero-installation web GUI dashboard**.

---

## 🌟 주요 특징 (Key Features)

### 1. 🎥 비디오 슬라이서 및 크로마키 필터 (Video Slicer & Chroma Key Filter)
* **비디오 프레임 추출**: MP4 등의 동영상을 불러와 프레임 단위로 쪼개어 스프라이트를 추출합니다.
* **실시간 크로마키(Chroma Key)**: 스포이트(Pipette) 도구로 배경색을 클릭하여 추출하고, 허용 오차(Tolerance) 및 에지 부드러움(Soft Edge) 슬라이더를 통해 알파 투명도를 완벽하게 분리합니다.
* **크롭 영역 조정**: 크롭 크기와 X/Y 좌표 설정을 통해 캐릭터의 중심 영역만 깔끔하게 오려냅니다.

### 2. ⏱️ 비주얼 타임라인 및 프레임 편집기 (Visual Timeline & Frame Editor)
* **듀얼 핸들 타임라인**: 각 애니메이션 상태(Idle, Walk, Attack 등)의 시작점과 끝점을 마우스 드래그로 조절합니다.
* **프레임 수동 비주얼 편집기**: 썸네일 그리드에서 원하는 프레임을 직접 개별 선택/해제하거나, 재생 주기(Skip)를 일괄 설정하여 원하는 모션을 정밀하게 제어할 수 있습니다.
* **실시간 루프 미리보기**: 편집 중인 스프라이트가 어떻게 애니메이션되는지 별도 뷰어에서 실시간으로 확인할 수 있습니다.

### 3. 📐 스프라이트 시트 및 애니메이션 수출 (Sprite Sheet & Animation Exporter)
* **2의 거듭제곱(Po2) 최적 정렬**: Unity 등 게임 엔진에서 선호하는 $2^n$ 크기 사각형 형태로 스프라이트 시트를 자동 정렬하며, 최적 해상도 추천 기능을 제공합니다.
* **오디오/효과음 추출**: 특정 모션 상태의 비디오 구간 음성을 `.wav` 파일로 즉시 추출합니다.
* **유니티 애니메이션 클립 (.anim) 내보내기**: 유니티의 텍스처 GUID와 동기화하여 바로 유니티 엔진에 드롭할 수 있는 `.anim` 설정 파일을 생성합니다.

### 4. 🤖 Gemini AI 프롬프트 매니저 (Gemini AI Prompt Manager)
* **AI 이미지-프롬프트 분석기**: 캐릭터 이미지를 업로드하고 Gemini API (`gemini-2.5-flash` 등)를 통해 정밀한 외형 태그(NovelAI 스타일)와 묘사문을 자동으로 추출합니다.
* **오토 파일럿 템플릿 빌더**: 클릭 한 번으로 캐릭터 상태별(Idle, Run, Jump 등) 마스터 프롬프트 및 파생 프롬프트를 자동으로 구조화해 줍니다.

### 5. 📂 프로젝트 저장 및 일괄 다운로드 (Project State & Batch Download)
* **JSON 설정 저장/로드**: 슬라이싱 및 프롬프트 작업 상태를 언제든 `.json` 파일로 로컬에 백업하고 다시 복구할 수 있습니다.
* **전체 리소스 일괄 압축**: 생성된 스프라이트 시트 PNG, 사운드 WAV, 상태 설정 JSON 등 모든 결과물을 단 하나의 `.zip` 파일로 묶어 다운로드합니다.

---

## 🛠️ 기술 스택 (Tech Stack)
* **Core**: Pure HTML5, CSS3, Vanilla JavaScript (ES6)
* **Libraries**: [JSZip](https://stuk.github.io/jszip/) (클라이언트 사이드 ZIP 압축 지원)
* **AI Integration**: Google Gemini API SDK (클라이언트 사이드 호출)
* **Design System**: 다크 모드 기반의 프리미엄 글래스모피즘(Glassmorphism) 및 네온 글로우 스타일링 적용

---

## 📂 프로젝트 구조 (Repository Structure)
```bash
HtmlMovieToSpriteEditor/
├── .agents/              # AI 에이전트 전용 로컬 커스터마이징 및 자동화 스킬 정의
│   └── skills/
│       ├── file-based-testing/                 # file:// 프로토콜 로컬 테스트 가이드 스킬
│       ├── auto-header-update/                 # 소스코드 내 메타데이터 헤더 자동 기입 스킬
│       └── readme-license-and-structure-sync/     # 리드미 구조 및 라이선스 변경 시 상호 동기화 스킬
├── index.html            # 메인 통합 대시보드 (비디오 슬라이서 및 프롬프트 매니저)
├── Data/                 # 설정 정보 및 Gemini API 연동 모듈
│   ├── gemini.js         # Gemini API 호출 기본값 설정 스크립트
│   └── README.md         # 캐릭터 리소스 이용 가이드라인 및 설명
├── Projects/             # 저장된 프로젝트 JSON 백업 디렉토리
│   ├── README.md         # 프로젝트 백업 디렉토리 설명 문서
│   ├── dajung_pixel_settings.json
│   └── dajung_NeoMaid_2d_config.json
├── HtmlPageSamples/      # 각 기능별 개별 실험실/테스트 페이지들
│   ├── VideoStateSpriteCreator.html    # 스프라이트 생성 실험기
│   ├── ImageToPrompte.html             # 이미지-프롬프트 추출 전용
│   ├── 2DSpritePromptAStateManager.html # 상태 관리기
│   ├── VideoToWave.html                # 오디오 추출 테스트
│   ├── ImageGenTester.html             # 이미지 생성 테스트기
│   └── GoogleAIStudioSample.html       # AI Studio 연동 샘플
├── LICENSE               # 소스 코드 라이센스 파일 (Apache 2.0)
└── README.md             # 프로젝트 소개 파일 (본 문서)
```

---

## 🚀 사용 방법 (Quick Start)

본 프로젝트는 서버 설치가 필요 없는 **순수 정적 웹 애플리케이션**입니다. 로컬 파일 시스템에서 바로 구동할 수 있습니다.

1. 이 저장소를 로컬로 클론하거나 다운로드합니다.
2. `index.html` 파일을 더블클릭하여 브라우저(`file://` 프로토콜)에서 바로 엽니다.
3. **스프라이트 생성하기**:
   * `비디오 소스 로드` 버튼을 클릭하여 스프라이트로 추출할 녹화 영상을 불러옵니다.
   * `크로마키 활성화` 후 스포이트 아이콘을 누르고 비디오의 배경색을 선택하여 투명화합니다.
   * 타임라인이나 프레임 수동 편집기를 활용해 애니메이션 상태의 프레임 구간을 잡아줍니다.
   * `스프라이트 다운로드 (.png)` 및 `유니티 클립 내보내기`를 사용해 게임 리소스로 출력합니다.
4. **프롬프트 관리 및 생성하기**:
   * 상단의 `프롬프트 매니저` 탭으로 전환합니다.
   * `AI 추출 생성기` 버튼을 눌러 Gemini API 키를 등록하고 분석할 캐릭터 원화를 업로드합니다.
   * 추출 완료된 프롬프트 태그를 적용해 상태별 텍스트 프롬프트를 자동으로 구성합니다.

> [!NOTE]
> 브라우저의 로컬 보안 정책상 일부 테스트 페이지에서 iframe이 오작동할 수 있으나, 본 프로젝트는 이를 우회하여 서브 구성 요소 클릭 시 브라우저 팝업 창(Popup Window)을 띄우는 방식으로 오프라인 로컬 환경(`file://`)에 최적화되어 있습니다.

---

## 🤝 기여 및 피드백 (Contributing & Feedback)
이 프로젝트에 관심이 있거나 기능 개선을 원하시는 분들은 언제든 Issue나 Pull Request를 통해 기여해 주세요!

---

## 📄 라이센스 및 이용 약관 (License & Terms of Use)

- **소스 코드 (Source Code)**: 이 프로젝트의 소스 코드는 **Apache License 2.0**에 따라 배포됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참고하세요.
- **캐릭터 리소스 및 에셋 (Character Assets & Sprites)**: 본 저장소의 `Data/` 및 `Projects/` 디렉토리에 포함된 캐릭터 디자인 및 스프라이트 리소스(예: `dajung` 캐릭터 에셋)는 **상업적 이용 및 수정이 가능하나, 몇 가지 중요한 제한 사항(19금/혐오 표현 금지 등)이 적용**됩니다.
  * 사용 시 **반드시 출처를 표기**해야 합니다. (예: `Character design and assets: [저작자명 또는 프로젝트 링크]`)
  * 성인물(NSFW/19금), 혐오 표현, 정치/종교적 선동 목적으로 캐릭터를 사용하는 것은 금지됩니다.
  * 자세한 허용 범위와 금지 조건은 각 폴더의 **[캐릭터 리소스 이용 가이드라인 (Data/README.md)](Data/README.md)** 및 **[Projects/README.md](Projects/README.md)** 문서를 반드시 참고해 주세요.

- **Source Code**: The source code of this project is licensed under the **Apache License 2.0**. See the [LICENSE](LICENSE) file for details.
- **Character Assets & Sprites**: The character designs and sprite assets in the `Data/` and `Projects/` directories (e.g., `dajung` assets) are free for commercial use and modification, but subject to **important restrictions (Prohibition of NSFW/Hate Speech)**.
  * **Attribution is required**. (e.g., `Character design and assets by [Author Name or Project Link]`)
  * Use in adult (NSFW) content, hate speech, or political/religious propaganda is strictly prohibited.
  * Please refer to the **[Character Usage Guidelines (Data/README.md)](Data/README.md)** and **[Projects/README.md](Projects/README.md)** for complete terms.

---

Inspired by [aldegad/sprite-gen](https://github.com/aldegad/sprite-gen) with ❤️.
