---
name: Phase 2.5 - Utils 구현 (TDD)
about: 유틸리티 함수 (포맷팅, 유효성 검사)
title: "[Phase 2.5] Utils - 유틸리티 함수 (TDD)"
labels: core-logic, tdd, phase-2
assignees: ''
---

## 📋 작업 배경

숫자 포맷팅, 유효성 검사 등 프로젝트 전반에서 사용되는 유틸리티 함수를 TDD 방식으로 구현합니다.

## 🎯 작업 내용

### 1. Formatter 테스트 및 구현

#### `tests/utils/formatter.test.js` 생성

- [ ] formatNumber 테스트
  - 1234 → "1,234"
  - 1234567 → "1,234,567"
  - 1234.56 → "1,234.56"
- [ ] formatDecimal 테스트

#### `src/utils/formatter.js` 구현

- [ ] formatNumber(num) 함수
- [ ] formatDecimal(num, places) 함수

### 2. Validator 테스트 및 구현

#### `tests/utils/validator.test.js` 생성

- [ ] isValidNumber 테스트
- [ ] isValidExpression 테스트 (괄호 균형, 연속 연산자)

#### `src/utils/validator.js` 구현

- [ ] isValidNumber(str) 함수
- [ ] isValidExpression(expr) 함수

## ✅ 인수 조건

- [ ] 모든 테스트 통과
- [ ] 테스트 커버리지 90% 이상
- [ ] 천 단위 구분이 정확함
- [ ] 유효성 검사가 정확함
- [ ] ESLint 에러 없음

## ⏱️ 예상 소요 시간

1.5시간

## 🔗 관련 이슈

- Depends on: #1 (Phase 1)
