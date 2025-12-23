---
name: Phase 1 - 프로젝트 초기 설정
about: 개발 환경 설정 및 프로젝트 구조 생성
title: "[Phase 1] 프로젝트 초기 설정"
labels: setup, phase-1
assignees: ''
---

## 📋 작업 배경

공학용 계산기 웹앱 개발을 위한 초기 프로젝트 환경을 설정합니다. Node.js 프로젝트 초기화, 개발 도구 설치, 디렉토리 구조 생성 등 개발을 시작하기 위한 기반을 마련합니다.

## 🎯 작업 내용

### 1. Node.js 프로젝트 초기화
- [ ] `npm init -y` 실행
- [ ] `package.json` 생성 확인
- [ ] 프로젝트 이름 및 설명 수정

### 2. 개발 도구 설치
- [ ] Vite 설치: `npm install -D vite`
- [ ] Jest 설치: `npm install -D jest @jest/globals`
- [ ] Babel 설치: `npm install -D @babel/preset-env babel-jest`
- [ ] ESLint 설치: `npm install -D eslint`
- [ ] Prettier 설치: `npm install -D prettier`

### 3. Tailwind CSS 설정
- [ ] Tailwind 설치: `npm install -D tailwindcss postcss autoprefixer`
- [ ] `npx tailwindcss init` 실행
- [ ] `tailwind.config.js` 설정
- [ ] PostCSS 설정

### 4. 설정 파일 생성
- [ ] `vite.config.js` 생성 및 설정
- [ ] `jest.config.js` 생성 및 설정
- [ ] `.eslintrc.js` 생성
- [ ] `.prettierrc` 생성
- [ ] `.gitignore` 업데이트

### 5. 디렉토리 구조 생성
```
src/
├── core/          # 코어 로직 (TDD 적용)
├── ui/            # UI 관련 코드
├── utils/         # 유틸리티
└── main.js        # 진입점

tests/
├── core/          # 코어 로직 테스트
└── utils/         # 유틸리티 테스트

public/
└── index.html     # HTML 파일

styles/
└── main.css       # CSS 파일
```

### 6. package.json 스크립트 설정
- [ ] `"dev": "vite"` 추가
- [ ] `"build": "vite build"` 추가
- [ ] `"preview": "vite preview"` 추가
- [ ] `"test": "jest"` 추가
- [ ] `"test:watch": "jest --watch"` 추가
- [ ] `"test:coverage": "jest --coverage"` 추가

## ✅ 인수 조건

- [ ] `npm run dev` 명령어가 정상 실행됨
- [ ] `npm test` 명령어가 정상 실행됨 (테스트 없어도 Jest 실행됨)
- [ ] 모든 디렉토리가 생성됨
- [ ] 설정 파일들이 모두 존재하고 올바르게 설정됨
- [ ] ESLint와 Prettier가 정상 작동함

## 📚 참고 자료

- [Vite 공식 문서](https://vitejs.dev/)
- [Jest 공식 문서](https://jestjs.io/)
- [Tailwind CSS 공식 문서](https://tailwindcss.com/)

## ⏱️ 예상 소요 시간

45분
