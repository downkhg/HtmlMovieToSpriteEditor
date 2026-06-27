---
name: readme-license-and-structure-sync
description: Ensures repository README files (root and subdirectories) are updated, synchronized, and documented whenever file structures, license terms, or major code fixes occur.
---

# 리드미 문서 및 라이선스 동기화 규칙 (README License & Structure Sync Rules)

이 프로젝트를 수정 및 업데이트하는 에이전트는 파일 구조 변경, 소스 코드 또는 캐릭터 라이선스 수정, 주요 코드 픽스(Fix) 사항이 발생할 때 최상위 및 하위 폴더의 `README.md` 문서를 동기화하고 최신 상태로 유지해야 합니다.

When modifying this repository, agents must synchronize and update all `README.md` files (root and subdirectories) to ensure file structures, licensing, and key changes are documented correctly.

---

## 1. 리드미 업데이트 수행 기준 (Triggers for Update)

1. **파일/디렉토리 구조의 변경 (Structure Changes)**:
   * 파일 추가, 폴더명 변경(예: `Samples` -> `HtmlPageSamples`), 또는 파일 삭제 발생 시.
   * **필수 행동**: 최상위 `README.md` 의 `## 📂 프로젝트 구조 (Repository Structure)` 섹션의 트리를 반드시 최신 상태로 수정해야 합니다.

2. **라이선스 정책 및 이용 제한 추가 (License Modifications)**:
   * 소스 코드 라이선스(Apache 2.0) 또는 캐릭터 리소스 가이드라인(CC BY 4.0 및 성인물/혐오표현 제한 등)에 수정이 생겼을 때.
   * **필수 행동**: 
     * 최상위 [README.md](file:///c:/Users/downk.KHG-HOME/source/repos/HtmlMovieToSprite/README.md)의 라이선스 섹션을 업데이트합니다.
     * 하위 폴더의 가이드라인 문서인 [Data/README.md](file:///c:/Users/downk.KHG-HOME/source/repos/HtmlMovieToSprite/Data/README.md)와 [Projects/README.md](file:///c:/Users/downk.KHG-HOME/source/repos/HtmlMovieToSprite/Projects/README.md)도 상호 동기화하여 변경점을 고르게 반영합니다.

3. **중요 코드 및 기능 픽스 (Key Fixes)**:
   * 버그 픽스, 보안 패치, 혹은 기능 개선이 완료되었을 때.
   * **필수 행동**: 관련된 모든 문서에 픽스사항을 기록하여 사용자가 최신 상태를 알 수 있도록 업데이트합니다.

---

## 2. 문서 점검 체크리스트 (Agent Checklist)

에이전트는 작업을 마치기 전에 다음 사항을 한 번 더 검사해야 합니다.

* [ ] 최상위 `README.md` 의 파일 경로 트리가 실제 리포지토리의 파일들과 완전히 일치하는가?
* [ ] 최상위 `README.md` 에서 가리키는 `Data/README.md` 및 `Projects/README.md` 로의 상대 경로 마크다운 링크가 깨지지 않고 제대로 연결되어 있는가?
* [ ] 캐릭터 리소스 이용 약관(상업 이용 허용, 출처 필수, 성인물/혐오표현 금지)이 `Data/README.md`와 `Projects/README.md`에 동일하게 최신화되어 적용되었는가?
* [ ] 각 개별 테스트 페이지 코드 파일 상단의 에이전트 수정사항 주석이 실제 문서 변경 기록과 동기화되어 있는가?
