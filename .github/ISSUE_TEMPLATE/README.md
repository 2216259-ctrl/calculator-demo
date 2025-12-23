# GitHub 이슈 생성 가이드

이 디렉토리에는 프로젝트의 각 Phase별 GitHub 이슈 템플릿이 포함되어 있습니다.

## 📋 이슈 목록

| # | Phase | 제목 | 예상 시간 | 의존성 |
|---|-------|------|----------|--------|
| 1 | Phase 1 | 프로젝트 초기 설정 | 45분 | - |
| 2 | Phase 2.1 | Calculator 클래스 (TDD) | 3시간 | #1 |
| 3 | Phase 2.2 | Operations 클래스 (TDD) | 2시간 | #2 |
| 4 | Phase 2.3 | Scientific 클래스 (TDD) | 3시간 | #1 |
| 5 | Phase 2.4 | History 클래스 (TDD) | 2시간 | #1 |
| 6 | Phase 2.5 | Utils (TDD) | 1.5시간 | #1 |
| 7 | Phase 3 | UI 구현 | 10.5시간 | #2, #4 |
| 8 | Phase 4 | 통합 및 테스트 | 4시간 | #2-7 |
| 9 | Phase 5 | 배포 | 2.5시간 | #8 |

**총 예상 시간**: 약 29시간

## 🚀 이슈 생성 방법

### 방법 1: GitHub 웹 인터페이스 (권장)

1. GitHub 저장소로 이동
2. **Issues** 탭 클릭
3. **New issue** 클릭
4. 원하는 템플릿 선택 (예: "Phase 1 - 프로젝트 초기 설정")
5. 필요시 내용 수정
6. **Submit new issue** 클릭

### 방법 2: GitHub CLI 사용

GitHub CLI가 설치되어 있다면:

```bash
# Phase 1 이슈 생성
gh issue create --template phase-1-setup.md

# Phase 2.1 이슈 생성
gh issue create --template phase-2-1-calculator.md

# 모든 이슈 한번에 생성
gh issue create --template phase-1-setup.md
gh issue create --template phase-2-1-calculator.md
gh issue create --template phase-2-2-operations.md
gh issue create --template phase-2-3-scientific.md
gh issue create --template phase-2-4-history.md
gh issue create --template phase-2-5-utils.md
gh issue create --template phase-3-ui.md
gh issue create --template phase-4-testing.md
gh issue create --template phase-5-deployment.md
```

## 📝 이슈 템플릿 구조

각 이슈 템플릿은 다음 섹션을 포함합니다:

### 📋 작업 배경
- 왜 이 작업이 필요한지
- 어떤 문제를 해결하는지

### 🎯 작업 내용
- 구체적인 작업 목록 (체크박스)
- TDD 사이클 (Red-Green-Refactor)
- 세부 구현 사항

### ✅ 인수 조건
- 작업 완료 기준
- 테스트 커버리지 목표
- 품질 기준

### 📚 참고 자료
- 관련 문서 링크
- 외부 참고 자료

### ⏱️ 예상 소요 시간
- 작업 예상 시간

### 🔗 관련 이슈
- 의존성 관계
- 선행 작업

## 🏷️ 라벨 체계

- `setup`: 프로젝트 설정 관련
- `core-logic`: 코어 로직 구현
- `tdd`: TDD로 구현되는 작업
- `solid`: SOLID 원칙 적용
- `ui`: UI 관련 작업
- `frontend`: 프론트엔드 작업
- `testing`: 테스트 관련
- `integration`: 통합 테스트
- `deployment`: 배포 관련
- `phase-1`, `phase-2`, `phase-3`, `phase-4`, `phase-5`: Phase 구분

## 📌 작업 순서

권장 작업 순서:

1. **Phase 1** - 프로젝트 초기 설정 (필수)
2. **Phase 2.1** - Calculator 클래스 (필수)
3. **Phase 2.2** - Operations 클래스
4. **Phase 2.3** - Scientific 클래스
5. **Phase 2.4** - History 클래스 (선택적)
6. **Phase 2.5** - Utils
7. **Phase 3** - UI 구현
8. **Phase 4** - 통합 및 테스트
9. **Phase 5** - 배포

## 💡 팁

- 각 이슈는 독립적으로 작업 가능하도록 설계됨
- Phase 2 작업들은 병렬로 진행 가능 (Calculator 제외)
- TDD 규칙을 반드시 준수 (코어 로직만)
- UI는 수동 테스트로 진행

## 📖 관련 문서

- [TASKS.md](../../docs/TASKS.md) - 상세 작업 목록
- [Implementation Plan](../../.gemini/antigravity/brain/77e69c00-2298-4d9f-900f-80d9db44cc4a/implementation_plan.md) - 전체 구현 계획
- [TDD 규칙](../../docs/rules/tdd.md)
- [SOLID 원칙](../../docs/rules/solid.md)
