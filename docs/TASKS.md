# 구현 작업 목록

> 전체 구현 계획은 [Implementation Plan](file:///C:/Users/user/.gemini/antigravity/brain/77e69c00-2298-4d9f-900f-80d9db44cc4a/implementation_plan.md) 참고

---

## 📋 Phase 1: 프로젝트 초기 설정 (45분)

### 1.1 Node.js 프로젝트 초기화
- [ ] `npm init -y` 실행
- [ ] `package.json` 생성 확인
- [ ] 프로젝트 이름 및 설명 수정

### 1.2 개발 도구 설치
- [ ] Vite 설치: `npm install -D vite`
- [ ] Jest 설치: `npm install -D jest @jest/globals`
- [ ] Babel 설치: `npm install -D @babel/preset-env babel-jest`
- [ ] ESLint 설치: `npm install -D eslint`
- [ ] Prettier 설치: `npm install -D prettier`

### 1.3 Tailwind CSS 설정
- [ ] Tailwind 설치: `npm install -D tailwindcss postcss autoprefixer`
- [ ] `npx tailwindcss init` 실행
- [ ] `tailwind.config.js` 설정
- [ ] PostCSS 설정

### 1.4 설정 파일 생성
- [ ] `vite.config.js` 생성 및 설정
- [ ] `jest.config.js` 생성 및 설정
- [ ] `.eslintrc.js` 생성
- [ ] `.prettierrc` 생성
- [ ] `.gitignore` 업데이트

### 1.5 디렉토리 구조 생성
- [ ] `src/` 디렉토리 생성
- [ ] `src/core/` 생성 (코어 로직)
- [ ] `src/ui/` 생성 (UI 코드)
- [ ] `src/utils/` 생성 (유틸리티)
- [ ] `tests/` 디렉토리 생성
- [ ] `tests/core/` 생성
- [ ] `tests/utils/` 생성
- [ ] `public/` 디렉토리 생성
- [ ] `styles/` 디렉토리 생성

### 1.6 package.json 스크립트 설정
- [ ] `"dev": "vite"` 추가
- [ ] `"build": "vite build"` 추가
- [ ] `"preview": "vite preview"` 추가
- [ ] `"test": "jest"` 추가
- [ ] `"test:watch": "jest --watch"` 추가
- [ ] `"test:coverage": "jest --coverage"` 추가

---

## 🧮 Phase 2: 코어 로직 구현 (TDD)

### 2.1 Calculator 클래스 - 기본 연산 (3시간)

#### 2.1.1 테스트 작성 (Red)
- [ ] `tests/core/Calculator.test.js` 파일 생성
- [ ] 테스트 환경 설정 (describe, beforeEach)
- [ ] **숫자 입력 테스트**
  - [ ] 단일 숫자 입력 테스트
  - [ ] 여러 자릿수 입력 테스트
  - [ ] 0 입력 테스트
- [ ] **소수점 입력 테스트**
  - [ ] 소수점 입력 테스트
  - [ ] 중복 소수점 방지 테스트
  - [ ] 0.5 같은 입력 테스트
- [ ] **덧셈 테스트**
  - [ ] 양수 + 양수
  - [ ] 음수 + 음수
  - [ ] 양수 + 음수
  - [ ] 소수점 덧셈
- [ ] **뺄셈 테스트**
  - [ ] 큰 수 - 작은 수
  - [ ] 작은 수 - 큰 수 (음수 결과)
  - [ ] 소수점 뺄셈
- [ ] **곱셈 테스트**
  - [ ] 양수 × 양수
  - [ ] 음수 × 양수
  - [ ] 소수점 곱셈
- [ ] **나눗셈 테스트**
  - [ ] 정상 나눗셈
  - [ ] 0으로 나누기 (Error 반환)
  - [ ] 소수점 나눗셈
- [ ] **기타 기능 테스트**
  - [ ] AC (전체 지우기)
  - [ ] +/- (부호 변경)
  - [ ] % (백분율)
  - [ ] Backspace (마지막 입력 삭제)

#### 2.1.2 구현 (Green)
- [ ] `src/core/Calculator.js` 파일 생성
- [ ] Calculator 클래스 정의
- [ ] **생성자 구현**
  - [ ] `currentValue` 초기화
  - [ ] `previousValue` 초기화
  - [ ] `operation` 초기화
  - [ ] `equation` 초기화
  - [ ] `isNewInput` 플래그 초기화
- [ ] **inputNumber() 메서드**
  - [ ] 숫자 문자열 추가 로직
  - [ ] 새 입력 시작 처리
  - [ ] 최대 자릿수 제한
- [ ] **inputDecimal() 메서드**
  - [ ] 소수점 추가 로직
  - [ ] 중복 소수점 방지
- [ ] **inputOperator() 메서드**
  - [ ] 연산자 저장
  - [ ] previousValue 설정
  - [ ] 연속 연산 처리
- [ ] **calculate() 메서드**
  - [ ] 연산 수행
  - [ ] 결과 저장
  - [ ] 에러 처리
- [ ] **clear() 메서드**
  - [ ] 모든 상태 초기화
- [ ] **toggleSign() 메서드**
  - [ ] 부호 변경 로직
- [ ] **percentage() 메서드**
  - [ ] 백분율 계산
- [ ] **backspace() 메서드**
  - [ ] 마지막 문자 삭제

#### 2.1.3 리팩토링 (Refactor)
- [ ] 중복 코드 제거
- [ ] 메서드 분리 (SRP 적용)
- [ ] 매직 넘버 상수화
- [ ] 주석 추가
- [ ] 테스트 재실행 및 통과 확인

### 2.2 Operations 클래스 - 연산 추상화 (2시간)

#### 2.2.1 테스트 작성 (Red)
- [ ] `tests/core/Operations.test.js` 파일 생성
- [ ] **Operation 베이스 클래스 테스트**
  - [ ] execute() 메서드 존재 확인
- [ ] **Addition 테스트**
  - [ ] 5 + 3 = 8
  - [ ] -5 + -3 = -8
  - [ ] 0.1 + 0.2 = 0.3
- [ ] **Subtraction 테스트**
  - [ ] 5 - 3 = 2
  - [ ] 3 - 5 = -2
- [ ] **Multiplication 테스트**
  - [ ] 5 × 3 = 15
  - [ ] -5 × 3 = -15
- [ ] **Division 테스트**
  - [ ] 6 ÷ 3 = 2
  - [ ] 5 ÷ 2 = 2.5
  - [ ] 5 ÷ 0 = Error
- [ ] **OperationFactory 테스트**
  - [ ] '+' → Addition 인스턴스
  - [ ] '-' → Subtraction 인스턴스
  - [ ] 잘못된 연산자 → Error

#### 2.2.2 구현 (Green)
- [ ] `src/core/Operations.js` 파일 생성
- [ ] **Operation 베이스 클래스**
  - [ ] execute(a, b) 추상 메서드
- [ ] **Addition 클래스**
  - [ ] Operation 상속
  - [ ] execute() 구현
- [ ] **Subtraction 클래스**
  - [ ] Operation 상속
  - [ ] execute() 구현
- [ ] **Multiplication 클래스**
  - [ ] Operation 상속
  - [ ] execute() 구현
- [ ] **Division 클래스**
  - [ ] Operation 상속
  - [ ] execute() 구현
  - [ ] 0으로 나누기 에러 처리
- [ ] **OperationFactory 클래스**
  - [ ] create(operator) 메서드
  - [ ] 연산자 매핑

#### 2.2.3 리팩토링 (Refactor)
- [ ] OCP 원칙 확인 (새 연산 추가 시 기존 코드 수정 불필요)
- [ ] LSP 원칙 확인 (모든 연산이 Operation 대체 가능)
- [ ] 테스트 재실행

#### 2.2.4 Calculator와 통합
- [ ] Calculator에서 Operations 사용하도록 수정
- [ ] 의존성 주입 적용 (DIP)
- [ ] 통합 테스트 작성 및 실행

### 2.3 Scientific 클래스 - 공학 함수 (3시간)

#### 2.3.1 테스트 작성 (Red)
- [ ] `tests/core/Scientific.test.js` 파일 생성
- [ ] **각도 변환 테스트**
  - [ ] deg → rad 변환
  - [ ] rad → deg 변환
  - [ ] grad 변환
- [ ] **삼각함수 테스트 (deg 모드)**
  - [ ] sin(30°) ≈ 0.5
  - [ ] cos(60°) ≈ 0.5
  - [ ] tan(45°) ≈ 1
  - [ ] sin(90°) ≈ 1
- [ ] **삼각함수 테스트 (rad 모드)**
  - [ ] sin(π/6) ≈ 0.5
  - [ ] cos(π/3) ≈ 0.5
- [ ] **역삼각함수 테스트**
  - [ ] asin(0.5) ≈ 30° (deg 모드)
  - [ ] acos(0.5) ≈ 60° (deg 모드)
  - [ ] atan(1) ≈ 45° (deg 모드)
- [ ] **로그 함수 테스트**
  - [ ] log(100) = 2
  - [ ] log(1000) = 3
  - [ ] log(0) = Error
  - [ ] log(-1) = Error
- [ ] **자연로그 테스트**
  - [ ] ln(e) = 1
  - [ ] ln(1) = 0
- [ ] **지수 함수 테스트**
  - [ ] pow(2, 3) = 8
  - [ ] pow(5, 2) = 25
  - [ ] sqrt(9) = 3
  - [ ] sqrt(16) = 4
- [ ] **상수 테스트**
  - [ ] PI ≈ 3.14159
  - [ ] E ≈ 2.71828

#### 2.3.2 구현 (Green)
- [ ] `src/core/Scientific.js` 파일 생성
- [ ] Scientific 클래스 정의
- [ ] **생성자**
  - [ ] angleMode 초기화 (deg/rad/grad)
- [ ] **각도 변환 메서드**
  - [ ] toRadians(angle)
  - [ ] toDegrees(radian)
- [ ] **삼각함수 메서드**
  - [ ] sin(x)
  - [ ] cos(x)
  - [ ] tan(x)
- [ ] **역삼각함수 메서드**
  - [ ] asin(x)
  - [ ] acos(x)
  - [ ] atan(x)
- [ ] **로그/지수 메서드**
  - [ ] log(x) - 상용로그
  - [ ] ln(x) - 자연로그
  - [ ] pow(x, y)
  - [ ] sqrt(x)
- [ ] **상수 getter**
  - [ ] get PI()
  - [ ] get E()
- [ ] **각도 모드 setter**
  - [ ] setAngleMode(mode)

#### 2.3.3 리팩토링 (Refactor)
- [ ] 에러 처리 개선
- [ ] 정밀도 처리 (부동소수점 오차)
- [ ] 테스트 재실행

### 2.4 History 클래스 - 히스토리 관리 (2시간)

#### 2.4.1 테스트 작성 (Red)
- [ ] `tests/core/History.test.js` 파일 생성
- [ ] LocalStorage 모킹 설정
- [ ] **추가 테스트**
  - [ ] 히스토리 항목 추가
  - [ ] 타임스탬프 자동 생성
  - [ ] ID 자동 생성
- [ ] **조회 테스트**
  - [ ] 전체 히스토리 조회
  - [ ] 빈 히스토리 조회
- [ ] **삭제 테스트**
  - [ ] 전체 삭제
  - [ ] 특정 항목 삭제
- [ ] **제한 테스트**
  - [ ] 최대 50개 항목 제한
  - [ ] 초과 시 오래된 항목 삭제
- [ ] **저장소 테스트**
  - [ ] LocalStorage 저장
  - [ ] LocalStorage 로드
  - [ ] 저장소 없을 때 빈 배열 반환

#### 2.4.2 구현 (Green)
- [ ] `src/core/History.js` 파일 생성
- [ ] History 클래스 정의
- [ ] **생성자**
  - [ ] maxItems 설정
  - [ ] items 배열 초기화
  - [ ] 저장소에서 로드
- [ ] **add(equation, result) 메서드**
  - [ ] 항목 생성 (id, equation, result, timestamp)
  - [ ] 배열 앞에 추가
  - [ ] 최대 개수 초과 시 마지막 항목 제거
  - [ ] 저장소에 저장
- [ ] **getAll() 메서드**
  - [ ] items 반환
- [ ] **clear() 메서드**
  - [ ] items 초기화
  - [ ] 저장소 초기화
- [ ] **remove(id) 메서드**
  - [ ] 특정 항목 삭제
  - [ ] 저장소 업데이트
- [ ] **saveToStorage() 메서드**
  - [ ] JSON.stringify로 변환
  - [ ] localStorage.setItem
- [ ] **loadFromStorage() 메서드**
  - [ ] localStorage.getItem
  - [ ] JSON.parse로 파싱
  - [ ] 에러 처리

#### 2.4.3 리팩토링 (Refactor)
- [ ] Storage 인터페이스 추상화 (DIP)
- [ ] LocalStorage, MemoryStorage 구현
- [ ] 의존성 주입으로 변경
- [ ] 테스트 재실행

### 2.5 Utils - 유틸리티 함수 (1.5시간)

#### 2.5.1 Formatter 테스트 및 구현
- [ ] `tests/utils/formatter.test.js` 파일 생성
- [ ] **formatNumber 테스트**
  - [ ] 1234 → "1,234"
  - [ ] 1234567 → "1,234,567"
  - [ ] 1234.56 → "1,234.56"
  - [ ] 0.123 → "0.123"
- [ ] **formatDecimal 테스트**
  - [ ] 소수점 자릿수 제한
  - [ ] 불필요한 0 제거
- [ ] `src/utils/formatter.js` 구현
  - [ ] formatNumber(num) 함수
  - [ ] formatDecimal(num, places) 함수

#### 2.5.2 Validator 테스트 및 구현
- [ ] `tests/utils/validator.test.js` 파일 생성
- [ ] **isValidNumber 테스트**
  - [ ] "123" → true
  - [ ] "12.34" → true
  - [ ] "abc" → false
  - [ ] "" → false
- [ ] **isValidExpression 테스트**
  - [ ] 괄호 균형 확인
  - [ ] 연속 연산자 확인
- [ ] `src/utils/validator.js` 구현
  - [ ] isValidNumber(str) 함수
  - [ ] isValidExpression(expr) 함수

---

## 🎨 Phase 3: UI 구현 (10.5시간)

### 3.1 HTML 마크업 (1.5시간)

- [ ] `public/index.html` 파일 생성
- [ ] **기본 구조**
  - [ ] DOCTYPE 및 html 태그
  - [ ] head 섹션 (meta, title, fonts)
  - [ ] body 태그 및 클래스
- [ ] **헤더 영역**
  - [ ] header 태그
  - [ ] 메뉴 아이콘
  - [ ] 모드 표시 (Scientific)
  - [ ] 히스토리 아이콘
  - [ ] 설정 아이콘
- [ ] **디스플레이 영역**
  - [ ] section#display
  - [ ] 수식 표시 div (#equation)
  - [ ] 결과 표시 div (#result)
- [ ] **키패드 영역**
  - [ ] section#keypad
  - [ ] 드래그 핸들
  - [ ] 공학 함수 그리드 (5×2)
  - [ ] 메인 키패드 그리드 (4×5)
- [ ] **버튼 요소**
  - [ ] data-value 속성 추가
  - [ ] data-function 속성 추가
  - [ ] 적절한 클래스 추가
- [ ] **접근성**
  - [ ] ARIA 레이블 추가
  - [ ] role 속성 추가
  - [ ] tabindex 설정

### 3.2 CSS 스타일링 (3시간)

#### 3.2.1 Tailwind 설정
- [ ] `tailwind.config.js` 커스텀 설정
  - [ ] 컬러 팔레트 정의
  - [ ] 폰트 패밀리 설정
  - [ ] 간격 및 크기 설정
- [ ] `styles/main.css` 생성
  - [ ] @tailwind 지시어 추가
  - [ ] 커스텀 CSS 추가

#### 3.2.2 레이아웃 스타일
- [ ] **전체 레이아웃**
  - [ ] body 스타일 (배경, 폰트)
  - [ ] 최대 너비 설정 (448px)
  - [ ] 중앙 정렬
- [ ] **헤더 스타일**
  - [ ] 패딩 및 간격
  - [ ] 아이콘 크기 및 색상
  - [ ] 호버 효과
- [ ] **디스플레이 스타일**
  - [ ] 수식 텍스트 (크기, 색상, 정렬)
  - [ ] 결과 텍스트 (크기, 굵기, 정렬)
  - [ ] 여백 및 패딩

#### 3.2.3 키패드 스타일
- [ ] **키패드 컨테이너**
  - [ ] 배경색
  - [ ] 모서리 둥글게 (32px)
  - [ ] 그림자 효과
  - [ ] 패딩
- [ ] **버튼 공통 스타일**
  - [ ] 크기 (72px × 72px)
  - [ ] 모서리 둥글게 (20px)
  - [ ] 폰트 크기 및 굵기
  - [ ] transition 효과
- [ ] **버튼 유형별 스타일**
  - [ ] 숫자 버튼 (흰색/어두운 배경)
  - [ ] 연산자 버튼 (파란색 강조)
  - [ ] 기능 버튼 (회색)
  - [ ] 공학 함수 버튼 (작은 크기)
  - [ ] 등호 버튼 (파란색 + 글로우)
- [ ] **버튼 인터랙션**
  - [ ] hover 효과 (밝기 증가)
  - [ ] active 효과 (스케일 감소)
  - [ ] focus 효과

#### 3.2.4 다크모드
- [ ] **다크모드 변수**
  - [ ] 배경색 정의
  - [ ] 텍스트 색상 정의
  - [ ] 버튼 색상 정의
- [ ] **다크모드 클래스**
  - [ ] .dark body 스타일
  - [ ] .dark 버튼 스타일
  - [ ] .dark 디스플레이 스타일

#### 3.2.5 반응형
- [ ] 모바일 (< 448px) 스타일
- [ ] 태블릿 스타일 (선택적)
- [ ] 가로 모드 처리

### 3.3 Display 클래스 (1.5시간)

- [ ] `src/ui/Display.js` 파일 생성
- [ ] Display 클래스 정의
- [ ] **생성자**
  - [ ] equationElement 저장
  - [ ] resultElement 저장
  - [ ] DOM 요소 캐싱
- [ ] **updateResult(value) 메서드**
  - [ ] 숫자 포맷팅
  - [ ] textContent 업데이트
- [ ] **updateEquation(equation) 메서드**
  - [ ] textContent 업데이트
- [ ] **showError(message) 메서드**
  - [ ] 에러 메시지 표시
  - [ ] 스타일 변경 (선택적)
- [ ] **clear() 메서드**
  - [ ] 수식 및 결과 초기화
- [ ] **수동 테스트**
  - [ ] 브라우저에서 결과 표시 확인
  - [ ] 수식 표시 확인
  - [ ] 에러 표시 확인

### 3.4 EventHandler 클래스 (2시간)

- [ ] `src/ui/EventHandler.js` 파일 생성
- [ ] EventHandler 클래스 정의
- [ ] **생성자**
  - [ ] calculator 인스턴스 저장
  - [ ] display 인스턴스 저장
  - [ ] listeners 배열 초기화
- [ ] **setupEventListeners() 메서드**
  - [ ] 버튼 클릭 이벤트 (이벤트 위임)
  - [ ] 키보드 이벤트
- [ ] **handleButtonClick(event) 메서드**
  - [ ] 숫자 버튼 처리
  - [ ] 연산자 버튼 처리
  - [ ] 기능 버튼 처리 (AC, +/-, %)
  - [ ] 공학 함수 버튼 처리
  - [ ] 등호 버튼 처리
- [ ] **handleKeyboard(event) 메서드**
  - [ ] 숫자 키 (0-9)
  - [ ] 연산자 키 (+, -, *, /)
  - [ ] Enter (=)
  - [ ] Escape (AC)
  - [ ] Backspace
- [ ] **destroy() 메서드**
  - [ ] 모든 이벤트 리스너 제거
- [ ] **수동 테스트**
  - [ ] 버튼 클릭 동작 확인
  - [ ] 키보드 입력 동작 확인

### 3.5 ThemeManager 클래스 (1시간)

#### 3.5.1 구현
- [ ] `src/ui/ThemeManager.js` 파일 생성
- [ ] ThemeManager 클래스 정의
- [ ] **생성자**
  - [ ] 현재 테마 로드
- [ ] **toggleTheme() 메서드**
  - [ ] dark 클래스 토글
  - [ ] 테마 저장
- [ ] **loadTheme() 메서드**
  - [ ] localStorage에서 테마 로드
  - [ ] 기본값 처리
- [ ] **saveTheme(theme) 메서드**
  - [ ] localStorage에 테마 저장
- [ ] **getCurrentTheme() 메서드**
  - [ ] 현재 테마 반환

### 3.6 Main 진입점 (1.5시간)

#### 3.6.1 App 클래스 구현
- [ ] `src/main.js` 파일 생성
- [ ] App 클래스 정의
- [ ] **생성자**
  - [ ] 의존성 생성 및 주입
  - [ ] Calculator 인스턴스
  - [ ] Scientific 인스턴스
  - [ ] History 인스턴스
  - [ ] Display 인스턴스
  - [ ] EventHandler 인스턴스
  - [ ] ThemeManager 인스턴스
- [ ] **init() 메서드**
  - [ ] 이벤트 리스너 설정
  - [ ] 테마 로드
  - [ ] 초기 화면 설정
- [ ] **DOMContentLoaded 이벤트**
  - [ ] App 인스턴스 생성
  - [ ] init() 호출

#### 3.6.2 통합 테스트
- [ ] 전체 플로우 수동 테스트
- [ ] 버튼 클릭 동작 확인
- [ ] 키보드 입력 확인
- [ ] 계산 결과 확인

---

## 🧪 Phase 4: 통합 및 테스트 (4시간)

### 4.1 코어 로직 통합 테스트 (2시간)

- [ ] `tests/integration/core.test.js` 생성
- [ ] **Calculator + Operations 통합**
  - [ ] 기본 계산 플로우 테스트
  - [ ] 연속 계산 테스트
  - [ ] 에러 처리 테스트
- [ ] **Calculator + Scientific 통합**
  - [ ] 공학 함수 계산 플로우
  - [ ] 각도 모드 전환 후 계산
- [ ] **Calculator + History 통합**
  - [ ] 계산 후 히스토리 저장 확인
  - [ ] 히스토리 로드 확인
- [ ] **전체 코어 로직 통합**
  - [ ] 복잡한 계산 시나리오
  - [ ] 에러 복구 시나리오

### 4.2 수동 브라우저 테스트 (1시간)

- [ ] **Chrome 테스트**
  - [ ] 기본 계산 동작 확인
  - [ ] 공학 함수 동작 확인
  - [ ] 키보드 입력 확인
  - [ ] 다크모드 전환 확인
  - [ ] 개발자 도구 콘솔 에러 확인
- [ ] **Firefox 테스트**
  - [ ] 기본 기능 동작
  - [ ] 호환성 확인
- [ ] **Safari 테스트** (가능한 경우)
  - [ ] 기본 기능 동작
- [ ] **Edge 테스트**
  - [ ] 기본 기능 동작
- [ ] **모바일 브라우저 테스트**
  - [ ] Chrome Mobile
  - [ ] Safari Mobile (iOS)
  - [ ] 터치 인터랙션 확인

### 4.3 성능 최적화 (1시간)

- [ ] **번들 크기 확인**
  - [ ] `npm run build` 실행
  - [ ] 번들 크기 분석
- [ ] **Lighthouse 테스트**
  - [ ] Performance 점수 확인
  - [ ] Accessibility 점수 확인
  - [ ] Best Practices 점수 확인
  - [ ] SEO 점수 확인
- [ ] **최적화 적용**
  - [ ] 이미지 최적화 (해당 시)
  - [ ] CSS 최소화
  - [ ] JS 최소화

### 4.4 코어 로직 테스트 커버리지 확인

- [ ] `npm run test:coverage` 실행
- [ ] 커버리지 리포트 확인
- [ ] **코어 로직 90% 이상** 달성 확인
  - [ ] Calculator 클래스
  - [ ] Operations 클래스
  - [ ] Scientific 클래스
  - [ ] History 클래스
  - [ ] Utils
- [ ] 미달 시 테스트 추가

---

## 🚀 Phase 5: 배포 (2.5시간)

### 5.1 배포 준비 (1시간)

- [ ] **Vite 설정**
  - [ ] `vite.config.js`에서 base path 설정
  - [ ] 저장소 이름과 일치하는지 확인
- [ ] **프로덕션 빌드 테스트**
  - [ ] `npm run build` 실행
  - [ ] `dist/` 폴더 생성 확인
  - [ ] `npm run preview` 실행
  - [ ] 로컬에서 프로덕션 빌드 테스트
- [ ] **환경 변수 확인** (필요 시)
  - [ ] `.env` 파일 설정
  - [ ] 환경별 설정 분리

### 5.2 GitHub 배포 (30분)

- [ ] **코드 커밋**
  - [ ] 변경사항 스테이징
  - [ ] 의미있는 커밋 메시지 작성
  - [ ] 커밋 실행
- [ ] **GitHub 푸시**
  - [ ] `git push origin main`
- [ ] **GitHub Actions 확인**
  - [ ] Actions 탭에서 워크플로우 실행 확인
  - [ ] 빌드 성공 확인
  - [ ] 배포 성공 확인
- [ ] **GitHub Pages 확인**
  - [ ] Settings → Pages에서 URL 확인
  - [ ] 배포된 사이트 접속
  - [ ] 모든 기능 동작 확인

### 5.3 문서 업데이트 (1시간)

- [ ] **README.md 업데이트**
  - [ ] 설치 방법 추가
  - [ ] 실행 방법 추가
  - [ ] 배포 URL 추가
  - [ ] 스크린샷 추가 (선택적)
- [ ] **API 문서 작성** (선택적)
  - [ ] Calculator API
  - [ ] Scientific API
  - [ ] History API
- [ ] **사용자 가이드 작성** (선택적)
  - [ ] 기본 사용법
  - [ ] 공학 함수 사용법
  - [ ] 키보드 단축키

---

## ✅ 체크포인트

### Checkpoint 1: 기본 계산기 동작 ✓
완료 조건:
- [ ] 사칙연산 모두 동작
- [ ] 숫자 입력 및 표시 정상
- [ ] **코어 로직** 테스트 커버리지 90%+
- [ ] UI 기본 구조 완성 (수동 테스트)

### Checkpoint 2: 공학 함수 추가 ✓
완료 조건:
- [ ] 삼각함수 동작 (sin, cos, tan)
- [ ] 로그/지수 함수 동작
- [ ] 각도 모드 전환 동작
- [ ] Scientific 테스트 커버리지 90%+

### Checkpoint 3: UI 완성 ✓
완료 조건:
- [ ] 디자인 참고 자료와 일치
- [ ] 다크모드 동작
- [ ] 반응형 레이아웃 동작
- [ ] 모든 버튼 인터랙션 정상

### Checkpoint 4: 배포 완료 ✓
완료 조건:
- [ ] GitHub Pages에 배포됨
- [ ] 모든 기능 정상 동작
- [ ] 브라우저 호환성 확인
- [ ] Lighthouse 점수 80점 이상

---

## 📊 진행 상황 요약

| Phase | 상태 | 진행률 |
|-------|------|--------|
| Phase 1: 프로젝트 설정 | ⬜ | 0% |
| Phase 2: 코어 로직 | ⬜ | 0% |
| Phase 3: UI 구현 | ⬜ | 0% |
| Phase 4: 테스트 | ⬜ | 0% |
| Phase 5: 배포 | ⬜ | 0% |
| **전체** | ⬜ | **0%** |

---

## 🎯 다음 작업

**즉시 시작**: Phase 1.1 - Node.js 프로젝트 초기화

준비되면 시작하겠습니다!
