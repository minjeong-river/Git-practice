# 차원 넘나들기

얄코님의 [제대로 파는 Git & GitHub](https://inf.run/FGN4) 강의 내용을 정리한 개인 공부 목적용 저장소입니다.

## 여러 branch 만들어보기

![branches](https://user-images.githubusercontent.com/108013728/176220523-89fd56ad-8a5d-42b4-af8d-6e8eeeacd87f.png)

### Branch: 분기된 가지 (다른 차원)

- 프로젝트를 하나 이상의 모습으로 관리해야 할 때
    - 실배포용, 테스트서버용, 새로운 시도용

- 여러 작업들이 각각 독립되어 진행될 때
    - 신기능 1, 신기능 2, 코드개선, 긴급수정...
    - 각각의 차원에서 작업한 뒤 확정된 것을 메인 차원에 통합

이 모든 것을 하나의 프로젝트 폴더에서 진행할 수 있도록 한다!

### 1. 브랜치 생성 / 이동 / 삭제하기

1. 브랜치 생성
```
git branch 새 브랜치명
```

2. 브랜치 목록 확인
```
git branch
```

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176222183-99c6580a-5cd1-4416-858e-124a82c64e4f.png">

- `*` : 현재 브렌치

3. 브랜치로 이동
```
git switch 이동할 브랜치명
```

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176222584-8909c91e-2018-42ac-92a4-a746470fbb1d.png">


### 2. 브랜치 생성과 동시에 이동하기
```
git switch -c new-teams
```

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176223109-5f068b0a-4f62-49b0-a0a5-4c388b715156.png">


### 3. 브랜치 이름 바꾸기
```
git branch -m 기존 브랜치명 새 브랜치명
```

### 4. 브랜치 삭제하기
```
git branch -d 삭제할 브랜치명
```

### 5. 여러 브랜치의 내역 편리하게 보기
```
git log --all --decorate --oneline --graph
```

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176473752-74ac07ca-859f-4586-b99b-2f07bc8f1dbc.png">

<div style="border: 1px solid #dfdfdf;">
    <img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176227565-da8aaa48-987b-43b0-8da4-b92b7067bc66.png">
</div>

---

## 🐰 branch를 합치는 두 가지 방법

<img width="600" alt="init" src="https://user-images.githubusercontent.com/108013728/176470218-c8c378b6-665f-4f64-af41-5a7163f0e26d.png">

### 1. merge

<img width="600" alt="merge" src="https://user-images.githubusercontent.com/108013728/176470486-84383dce-28fa-4423-9d05-c55897a8ad65.png">

- 두 브랜치를 이어붙인다. 그 과정에서 커밋 하나가 더 생겨난다.
- 새로 생기는 커밋에는 원래 브랜치랑 병합될 브랜치의 모든 변화들이 담긴다.
- 브랜치 사용내역을 남길 필요가 있을 때 적합한 방식이다.

### 2. rebase

<img width="600" alt="rebase" src="https://user-images.githubusercontent.com/108013728/176471649-2fb87615-0ddc-4ab5-9e47-ea8a7099dd9b.png">


- 브랜치를 다른 브랜치에 이어붙인다.
- 브렌치 뒤에 다른 브랜치가 위치하게 된다.
- 한 줄로 깔끔히 정리된 내역을 유지하기 원할 때 적합하다.

---

## branch 합치기

### 1. merge로 합치기

1. 브랜치로 이동
```
git switch 메인 브렌치명
```

2. 아래의 명령어로 병합
```
git merge 메인 브랜치에 병합될 브랜치명
```

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176473844-52155866-b901-400a-9fcc-5c818fd82323.png">

<div style="border: 1px solid #dfdfdf;">
    <img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176473059-54fd338e-7dc6-44c4-bb4f-5be0a0bef932.png">
</div><br/>

3. 병합된 브랜치는 삭제

```
git branch -d 메인 브랜치에 병합된 브랜치명
```

<div style="border: 1px solid #dfdfdf;">
    <img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176474940-5d3a790f-1fc6-4b5d-822c-d8a70dcdbbc8.png">
</div>

### 2. rebase로 합치기

1. rebase할 대상 브랜치로 이동
```
git switch rebase할 대상 브랜치
```

2. 아래의 명령어로 병합
```
git rebase 메인 브랜치
```

3. 브랜치 이동
```
git switch 메인 브랜치
```

4. 아래 명령어로 fast-forward
```
git merge rebase한 대상 브랜치
```

5. rebase한 브랜치는 삭제
```
git branch -d rebase한 브랜치
```

<div style="border: 1px solid #dfdfdf;">
    <img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176477673-abb9231c-bcaf-493f-a54f-86e4949928b1.png">
</div>