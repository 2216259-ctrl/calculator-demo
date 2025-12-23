---
name: Phase 2.1 - Calculator 클래스 구현 (TDD)
about: TDD로 기본 계산기 로직 구현
title: "[Phase 2.1] Calculator 클래스 - 기본 연산 (TDD)"
labels: core-logic, tdd, phase-2
assignees: ''
---

## 📋 작업 배경

공학용 계산기의 핵심인 기본 계산 로직을 TDD 방식으로 구현합니다. 사칙연산, 소수점 처리, 에러 처리 등 계산기의 기본 기능을 포함합니다. 이 작업은 **TDD 원칙**을 엄격히 따라 Red-Green-Refactor 사이클로 진행됩니다.

## 🎯 작업 내용

### 1. 테스트 작성 (Red)

#### `tests/core/Calculator.test.js` 생성

- [ ] 테스트 환경 설정 (describe, beforeEach)
- [ ] **숫자 입력 테스트**
  - [ ] 단일 숫자 입력
  - [ ] 여러 자릿수 입력
  - [ ] 0 입력
- [ ] **소수점 입력 테스트**
  - [ ] 소수점 입력
  - [ ] 중복 소수점 방지
  - [ ] 0.5 같은 입력
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

### 2. 구현 (Green)

#### `src/core/Calculator.js` 생성

- [ ] Calculator 클래스 정의
- [ ] **생성자 구현**
  - [ ] `currentValue` 초기화
  - [ ] `previousValue` 초기화
  - [ ] `operation` 초기화
  - [ ] `equation` 초기화
  - [ ] `isNewInput` 플래그 초기화
- [ ] **메서드 구현**
  - [ ] `inputNumber(num)` - 숫자 입력
  - [ ] `inputDecimal()` - 소수점 입력
  - [ ] `inputOperator(op)` - 연산자 입력
  - [ ] `calculate()` - 계산 실행
  - [ ] `clear()` - 전체 지우기
  - [ ] `toggleSign()` - 부호 변경
  - [ ] `percentage()` - 백분율
  - [ ] `backspace()` - 마지막 입력 삭제

### 3. 리팩토링 (Refactor)

- [ ] 중복 코드 제거
- [ ] 메서드 분리 (SRP 적용)
- [ ] 매직 넘버 상수화
- [ ] 주석 추가
- [ ] 테스트 재실행 및 통과 확인

## ✅ 인수 조건

- [ ] 모든 테스트가 통과함 (Green)
- [ ] 테스트 커버리지 90% 이상
- [ ] 사칙연산이 정확하게 동작함
- [ ] 0으로 나누기 시 "Error" 반환
- [ ] 소수점 입력이 올바르게 처리됨
- [ ] AC, +/-, % 기능이 정상 동작함
- [ ] 코드가 SOLID 원칙을 준수함 (특히 SRP)
- [ ] ESLint 에러가 없음

## 📚 참고 자료

- [TDD 규칙](../../docs/rules/tdd.md)
- [SOLID 원칙](../../docs/rules/solid.md)
- [Jest 공식 문서](https://jestjs.io/)

## ⏱️ 예상 소요 시간

3시간

## 🔗 관련 이슈

- Depends on: #1 (Phase 1 - 프로젝트 초기 설정)
