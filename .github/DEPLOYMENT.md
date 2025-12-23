# GitHub Actions 배포 가이드

## 개요
이 프로젝트는 GitHub Actions를 사용하여 자동으로 빌드하고 GitHub Pages에 배포됩니다.

## 워크플로우 파일

### 1. deploy.yml (Vite 빌드 사용)
Vite를 사용하여 프로젝트를 빌드한 후 배포하는 워크플로우입니다.

**사용 시기**: npm 프로젝트로 개발할 때

**필요 파일**:
- `package.json`
- `vite.config.js`

### 2. deploy-static.yml (정적 파일 배포)
빌드 과정 없이 정적 HTML/CSS/JS 파일을 직접 배포하는 워크플로우입니다.

**사용 시기**: 순수 HTML/CSS/JS로 개발할 때 (현재 권장)

**배포 파일**: 루트 디렉토리의 모든 파일

## GitHub Pages 설정 방법

### 1단계: 저장소 설정
1. GitHub 저장소로 이동
2. **Settings** 탭 클릭
3. 왼쪽 메뉴에서 **Pages** 클릭
4. **Source**를 **GitHub Actions**로 선택

### 2단계: 워크플로우 선택
현재 프로젝트에 두 개의 워크플로우가 있습니다:

#### 옵션 A: 정적 파일 배포 (권장)
순수 HTML/CSS/JS로 개발하는 경우:
- `deploy-static.yml` 사용
- `deploy.yml` 파일 삭제 또는 비활성화

#### 옵션 B: Vite 빌드 후 배포
npm 프로젝트로 개발하는 경우:
- `deploy.yml` 사용
- `deploy-static.yml` 파일 삭제 또는 비활성화
- `package.json` 및 `vite.config.js` 생성 필요

### 3단계: 배포
```bash
# 코드를 main 브랜치에 푸시
git add .
git commit -m "Deploy calculator app"
git push origin main
```

GitHub Actions가 자동으로 실행되어 배포됩니다.

### 4단계: 배포 확인
1. GitHub 저장소의 **Actions** 탭에서 워크플로우 실행 확인
2. **Settings → Pages**에서 배포 URL 확인
3. URL: `https://<username>.github.io/<repository-name>/`

## 트러블슈팅

### 워크플로우가 실행되지 않는 경우
- `.github/workflows/` 폴더가 올바른 위치에 있는지 확인
- YAML 파일 문법 오류 확인
- main 브랜치에 푸시했는지 확인

### 권한 오류가 발생하는 경우
1. **Settings → Actions → General**로 이동
2. **Workflow permissions**를 "Read and write permissions"로 설정
3. "Allow GitHub Actions to create and approve pull requests" 체크

### 404 에러가 발생하는 경우
- 파일 경로 확인 (대소문자 구분)
- `index.html` 파일이 루트에 있는지 확인
- GitHub Pages 설정이 올바른지 확인

## 현재 권장 설정

현재 프로젝트는 순수 HTML/CSS/JS로 개발되므로:

1. **사용할 워크플로우**: `deploy-static.yml`
2. **삭제할 워크플로우**: `deploy.yml` (또는 이름 변경하여 비활성화)
3. **배포 파일**: 루트의 `index.html`, CSS, JS 파일들

## 참고 자료
- [GitHub Pages 공식 문서](https://docs.github.com/en/pages)
- [GitHub Actions 공식 문서](https://docs.github.com/en/actions)
