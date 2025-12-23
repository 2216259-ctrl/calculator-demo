---
name: Phase 3 - UI 구현
about: HTML, CSS, UI 클래스 구현
title: "[Phase 3] UI 구현"
labels: ui, frontend, phase-3
assignees: ''
---

## 📋 작업 배경

계산기의 사용자 인터페이스를 구현합니다. 디자인 참고 자료(`docs/design/reference.html`)를 기반으로 HTML 마크업, Tailwind CSS 스타일링, UI 클래스들을 구현합니다. **UI 컴포넌트는 자동화 테스트를 작성하지 않고 브라우저에서 수동으로 테스트합니다.**

## 🎯 작업 내용

### 1. HTML 마크업 (1.5시간)

- [ ] `public/index.html` 파일 생성
- [ ] 헤더 영역 (메뉴, 모드 표시, 히스토리, 설정)
- [ ] 디스플레이 영역 (수식, 결과)
- [ ] 키패드 영역 (공학 함수 5×2, 메인 키패드 4×5)
- [ ] ARIA 레이블 추가
- [ ] data-value, data-function 속성 추가

### 2. CSS 스타일링 (3시간)

- [ ] `tailwind.config.js` 커스텀 설정
- [ ] `styles/main.css` 생성
- [ ] 전체 레이아웃 스타일
- [ ] 헤더 스타일
- [ ] 디스플레이 스타일
- [ ] 키패드 및 버튼 스타일
- [ ] 다크모드 스타일
- [ ] 반응형 레이아웃

### 3. Display 클래스 (1.5시간)

- [ ] `src/ui/Display.js` 생성
- [ ] updateResult(value) 메서드
- [ ] updateEquation(equation) 메서드
- [ ] showError(message) 메서드
- [ ] clear() 메서드
- [ ] **수동 테스트**: 브라우저에서 표시 확인

### 4. EventHandler 클래스 (2시간)

- [ ] `src/ui/EventHandler.js` 생성
- [ ] setupEventListeners() 메서드
- [ ] handleButtonClick(event) 메서드
- [ ] handleKeyboard(event) 메서드
- [ ] destroy() 메서드
- [ ] **수동 테스트**: 버튼 클릭 및 키보드 입력 확인

### 5. ThemeManager 클래스 (1시간)

- [ ] `src/ui/ThemeManager.js` 생성
- [ ] toggleTheme() 메서드
- [ ] loadTheme() 메서드
- [ ] saveTheme(theme) 메서드
- [ ] **수동 테스트**: 테마 전환 확인

### 6. Main 진입점 (1.5시간)

- [ ] `src/main.js` 생성
- [ ] App 클래스 구현
- [ ] 의존성 주입 설정
- [ ] init() 메서드
- [ ] DOMContentLoaded 이벤트 핸들러
- [ ] **통합 테스트**: 전체 플로우 수동 테스트

## ✅ 인수 조건

- [ ] 디자인 참고 자료와 UI가 일치함
- [ ] 다크모드/라이트모드가 정상 작동함
- [ ] 모든 버튼 클릭이 정상 작동함
- [ ] 키보드 입력이 정상 작동함
  - 숫자 키 (0-9)
  - 연산자 키 (+, -, *, /)
  - Enter (=), Escape (AC), Backspace
- [ ] 반응형 레이아웃이 정상 작동함 (모바일, 태블릿, 데스크톱)
- [ ] 접근성 기준 충족 (ARIA 레이블)
- [ ] ESLint 에러 없음
- [ ] Chrome, Firefox, Safari, Edge에서 정상 작동 확인

## 📚 참고 자료

- [디자인 참고](../../docs/design/reference.html)
- [디자인 스크린샷](../../docs/design/screenshot.png)
- [Tailwind CSS 문서](https://tailwindcss.com/)

## ⏱️ 예상 소요 시간

10.5시간

## 🔗 관련 이슈

- Depends on: #2 (Phase 2.1 - Calculator 클래스)
- Depends on: #4 (Phase 2.3 - Scientific 클래스)
