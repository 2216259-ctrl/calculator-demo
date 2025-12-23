---
name: Phase 2.2 - Operations 클래스 구현 (TDD)
about: 연산 추상화 및 SOLID 원칙 적용
title: "[Phase 2.2] Operations 클래스 - 연산 추상화 (TDD)"
labels: core-logic, tdd, solid, phase-2
assignees: ''
---

## 📋 작업 배경

Calculator 클래스의 연산 로직을 추상화하여 확장 가능한 구조로 개선합니다. 전략 패턴을 사용하여 새로운 연산 추가 시 기존 코드 수정이 불필요하도록 **OCP(개방-폐쇄 원칙)**를 적용합니다.

## 🎯 작업 내용

### 1. 테스트 작성 (Red)

#### `tests/core/Operations.test.js` 생성

- [ ] Operation 베이스 클래스 테스트
- [ ] Addition 테스트 (5 + 3 = 8, -5 + -3 = -8, 0.1 + 0.2 = 0.3)
- [ ] Subtraction 테스트 (5 - 3 = 2, 3 - 5 = -2)
- [ ] Multiplication 테스트 (5 × 3 = 15, -5 × 3 = -15)
- [ ] Division 테스트 (6 ÷ 3 = 2, 5 ÷ 2 = 2.5, 5 ÷ 0 = Error)
- [ ] OperationFactory 테스트

### 2. 구현 (Green)

#### `src/core/Operations.js` 생성

- [ ] Operation 베이스 클래스
- [ ] Addition 클래스
- [ ] Subtraction 클래스
- [ ] Multiplication 클래스
- [ ] Division 클래스 (0으로 나누기 에러 처리)
- [ ] OperationFactory 클래스

### 3. 리팩토링 (Refactor)

- [ ] OCP 원칙 확인
- [ ] LSP 원칙 확인
- [ ] 테스트 재실행

### 4. Calculator 통합

- [ ] Calculator에서 Operations 사용하도록 수정
- [ ] 의존성 주입 적용 (DIP)
- [ ] 통합 테스트 작성 및 실행

## ✅ 인수 조건

- [ ] 모든 테스트 통과
- [ ] 테스트 커버리지 90% 이상
- [ ] 새로운 연산 추가 시 기존 코드 수정 불필요 (OCP)
- [ ] 모든 연산 클래스가 Operation 대체 가능 (LSP)
- [ ] Calculator와 정상 통합됨
- [ ] ESLint 에러 없음

## 📚 참고 자료

- [SOLID 원칙 - OCP](../../docs/rules/solid.md#o---openclosed-principle-개방-폐쇄-원칙)
- [전략 패턴](https://refactoring.guru/design-patterns/strategy)

## ⏱️ 예상 소요 시간

2시간

## 🔗 관련 이슈

- Depends on: #2 (Phase 2.1 - Calculator 클래스)
