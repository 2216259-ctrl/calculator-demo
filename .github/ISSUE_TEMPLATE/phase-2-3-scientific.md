---
name: Phase 2.3 - Scientific 클래스 구현 (TDD)
about: 공학 함수 구현 (삼각함수, 로그, 지수)
title: "[Phase 2.3] Scientific 클래스 - 공학 함수 (TDD)"
labels: core-logic, tdd, phase-2
assignees: ''
---

## 📋 작업 배경

공학용 계산기의 핵심 기능인 공학 함수(삼각함수, 로그, 지수 등)를 TDD 방식으로 구현합니다. 각도 모드(deg/rad/grad) 전환 기능도 포함됩니다.

## 🎯 작업 내용

### 1. 테스트 작성 (Red)

#### `tests/core/Scientific.test.js` 생성

- [ ] 각도 변환 테스트 (deg ↔ rad ↔ grad)
- [ ] 삼각함수 테스트 (deg 모드)
  - sin(30°) ≈ 0.5
  - cos(60°) ≈ 0.5
  - tan(45°) ≈ 1
- [ ] 삼각함수 테스트 (rad 모드)
- [ ] 역삼각함수 테스트
- [ ] 로그 함수 테스트 (log, ln)
- [ ] 지수 함수 테스트 (pow, sqrt)
- [ ] 상수 테스트 (PI, E)

### 2. 구현 (Green)

#### `src/core/Scientific.js` 생성

- [ ] Scientific 클래스 정의
- [ ] 각도 변환 메서드 (toRadians, toDegrees)
- [ ] 삼각함수 메서드 (sin, cos, tan)
- [ ] 역삼각함수 메서드 (asin, acos, atan)
- [ ] 로그/지수 메서드 (log, ln, pow, sqrt)
- [ ] 상수 getter (PI, E)
- [ ] 각도 모드 setter

### 3. 리팩토링 (Refactor)

- [ ] 에러 처리 개선
- [ ] 정밀도 처리 (부동소수점 오차)
- [ ] 테스트 재실행

## ✅ 인수 조건

- [ ] 모든 테스트 통과
- [ ] 테스트 커버리지 90% 이상
- [ ] sin(30°) = 0.5 정확히 계산됨
- [ ] 각도 모드 전환이 정상 작동함
- [ ] 로그 함수 에러 처리 (log(0), log(-1))
- [ ] ESLint 에러 없음

## ⏱️ 예상 소요 시간

3시간

## 🔗 관련 이슈

- Depends on: #1 (Phase 1)
