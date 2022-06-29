# Git 시작하기

얄코님의 [제대로 파는 Git & GitHub](https://inf.run/FGN4) 강의 내용을 정리한 개인 공부 목적용 저장소입니다.

## 강의를 위한 설치와 세팅 (윈도우)

### 1. Git 설치

1. https://git-scm.com/ 로 이동해서 Git을 다운로드.
2. 설치 후 Git Bash에서 아래 명령어로 테스트 실행.
```
git --version
```
3. 아래 명령어를 입력한다. 윈도우와 맥에서 엔터 방식 차이로 인한 오류를 방지.
```
git config --global core.autocrlf true 
```

### 2. SourceTree 설치

1. https://www.sourcetreeapp.com/ 로 이동해서 다운로드.

### 3. VS Code의 기본 터미널을 Git Bash로 설정
1. VS Code에서 `Ctrl + Shift + P`
2. `Select Default Profile` 검색하여 선택
3. `Git Bash` 선택
4. 터미널에서 +로 새 창을 열어서 기본으로 Git Bash가 설정된 것 확인

---

## Git 설정 & 프로젝트 관리 시작하기

### Git 최초 설정

#### 1. Git 전역으로 사용자 이름과 이메일 주소를 설정

터미널 프로그램에서 아래 명령어 실행

```
git config --global user.name "(본인 이름)"
```
```
git config --global user.email "(본인 이메일)"
```

아래의 명령어들로 확인

```
git config --global user.name
```
```
git config --global user.email
```

#### 2. 기본 브랜치명 변경

```
git config --global init.defaultBranch main
```

### 프로젝트 생성 & Git 관리 시작

폴더를 생성하고 VS Code 터미널에서 아래 명령어 입력

```
git init
```

폴더에 숨김모드 해제 후 .git 폴더 생성 확인

---

## Git에게 맡기지 않을 것들

### 1. Git의 관리에서 특정 파일/폴더를 배제해야 할 경우

- 포함할 필요가 없을 때 : 자동으로 생성 또는 다운로드되는 파일들 (빌드 결과물, 라이브러리)
- 포함하지 말아야 할 때 : 보안상 민감한 정보를 담은 파일

#### `.gitignore` 파일을 사용해서 배제할 요소들을 지정할 수 있다.

1. 폴더에 .gitignore 파일 생성
2. .gitignore 파일에 배제할 파일/폴더를 입력
3. 아래 명령어로 상태 확인

```
git status
```

### 2. .gitignore 형식
```
# 이렇게 #를 사용해서 주석

# 모든 file.c
file.c

# 최상위 폴더의 file.c
/file.c

# 모든 .c 확장자 파일
*.c

# .c 확장자지만 무시하지 않을 파일
!not_ignore_this.c

# logs란 이름의 파일 또는 폴더와 그 내용들
logs

# logs란 이름의 폴더와 그 내용들
logs/

# logs 폴더 바로 안의 debug.log와 .c 파일들
logs/debug.log
logs/*.c

# logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
logs/**/debug.log
```

