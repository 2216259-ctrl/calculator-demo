---
name: Phase 5 - 배포
about: 프로덕션 빌드 및 GitHub Pages 배포
title: "[Phase 5] 배포"
labels: deployment, phase-5
assignees: ''
---

## 📋 작업 배경

개발이 완료된 계산기 웹앱을 프로덕션 환경으로 빌드하고 GitHub Pages에 배포합니다. 배포 전 설정 확인, 빌드 테스트, 배포 후 검증, 문서 업데이트를 포함합니다.

## 🎯 작업 내용

### 1. 배포 준비 (1시간)

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

### 2. GitHub 배포 (30분)

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

### 3. 문서 업데이트 (1시간)

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

## ✅ 인수 조건

- [ ] 프로덕션 빌드가 성공적으로 생성됨
- [ ] GitHub Pages에 정상 배포됨
- [ ] 배포된 사이트에서 모든 기능이 정상 작동함
  - [ ] 기본 계산
  - [ ] 공학 함수
  - [ ] 히스토리
  - [ ] 다크모드
  - [ ] 키보드 입력
- [ ] README.md에 배포 URL이 포함됨
- [ ] 문서가 최신 상태로 업데이트됨
- [ ] 배포 URL이 공개적으로 접근 가능함

## 📚 참고 자료

- [GitHub Pages 문서](https://docs.github.com/en/pages)
- [GitHub Actions 문서](https://docs.github.com/en/actions)
- [배포 가이드](../../.github/DEPLOYMENT.md)

## ⏱️ 예상 소요 시간

2.5시간

## 🔗 관련 이슈

- Depends on: #8 (Phase 4 - 통합 및 테스트)

## 🎉 완료 후

이 이슈가 완료되면 프로젝트의 모든 Phase가 완료됩니다!
