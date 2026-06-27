---
name: auto-header-update
description: Automatically documents modifications by adding or updating a specific header comment block at the top of every code file in the repository.
---

# 파일 헤더 메타데이터 자동 업데이트 규칙 (Automatic File Header Metadata Update Rules)

이 프로젝트의 소스 코드 파일(HTML, JS 등)을 생성하거나 수정할 때, 에이전트는 파일의 가장 첫 머리에 아래 형식의 메타데이터 주석 블록을 반드시 작성하거나 업데이트해야 합니다.

When creating or modifying source code files (HTML, JS, etc.) in this repository, agents must write or update the following metadata comment block at the very top of the file.

---

## 1. 헤더 포맷 (Header Format)

### HTML / XML 파일의 경우
```html
<!--
프롬프터: downkhg@gmail.com
모델: gemini
에이전트: <현재 실행 중인 에이전트 이름 (예: Antigravity)>
마지막수정사항: <수정된 작업의 주요 요약 내용>
-->
```

### JavaScript / CSS 파일의 경우
```javascript
/**
 * 프롬프터: downkhg@gmail.com
 * 모델: gemini
 * 에이전트: <현재 실행 중인 에이전트 이름 (예: Antigravity)>
 * 마지막수정사항: <수정된 작업의 주요 요약 내용>
 */
```

---

## 2. 업데이트 수행 기준 (Instruction for Agents)

1. **상시 검사**: 임의의 파일(HTML, JS, CSS 등)을 수정하여 저장하기 직전, 파일의 첫 줄(또는 BOM 문자 바로 뒤)에 해당 헤더가 존재하는지 확인합니다.
2. **헤더 부재 시**: 헤더가 없다면 위의 포맷을 사용하여 신규 작성합니다.
3. **헤더 존재 시**: 기존 헤더를 덮어쓰거나 `마지막수정사항` 및 `에이전트` 정보를 현재 수행 중인 태스크에 맞게 갱신합니다.
4. **일관성 유지**: `프롬프터: downkhg@gmail.com` 및 `모델: gemini` 값은 고정으로 유지하며, `에이전트`와 `마지막수정사항`만 최신화합니다.
