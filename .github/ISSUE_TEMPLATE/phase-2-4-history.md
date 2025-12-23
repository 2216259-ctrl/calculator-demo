---
name: Phase 2.4 - History 클래스 구현 (TDD)
about: 히스토리 관리 및 LocalStorage 연동
title: "[Phase 2.4] History 클래스 - 히스토리 관리 (TDD)"
labels: core-logic, tdd, phase-2
assignees: ''
---

## 📋 작업 배경

계산 기록을 저장하고 관리하는 History 클래스를 TDD 방식으로 구현합니다. LocalStorage를 사용하여 브라우저를 닫아도 히스토리가 유지되도록 합니다. **DIP(의존성 역전 원칙)**을 적용하여 Storage를 추상화합니다.

## 🎯 작업 내용

### 1. 테스트 작성 (Red)

#### `tests/core/History.test.js` 생성

- [ ] LocalStorage 모킹 설정
- [ ] 히스토리 추가 테스트
- [ ] 히스토리 조회 테스트
- [ ] 히스토리 삭제 테스트
- [ ] 최대 50개 항목 제한 테스트
- [ ] LocalStorage 저장/로드 테스트

### 2. 구현 (Green)

#### `src/core/History.js` 생성

- [ ] History 클래스 정의
- [ ] add(equation, result) 메서드
- [ ] getAll() 메서드
- [ ] clear() 메서드
- [ ] remove(id) 메서드
- [ ] saveToStorage() 메서드
- [ ] loadFromStorage() 메서드

### 3. 리팩토링 (Refactor)

- [ ] Storage 인터페이스 추상화 (DIP)
- [ ] LocalStorage, MemoryStorage 구현
- [ ] 의존성 주입으로 변경
- [ ] 테스트 재실행

## ✅ 인수 조건

- [ ] 모든 테스트 통과
- [ ] 테스트 커버리지 90% 이상
- [ ] 히스토리가 LocalStorage에 저장됨
- [ ] 최대 50개 항목 제한 동작
- [ ] Storage 추상화 적용 (DIP)
- [ ] ESLint 에러 없음

## ⏱️ 예상 소요 시간

2시간

## 🔗 관련 이슈

- Depends on: #1 (Phase 1)
