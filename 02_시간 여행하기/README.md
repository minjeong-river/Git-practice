# 시간 여행하기

얄코님의 [제대로 파는 Git & GitHub](https://inf.run/FGN4) 강의 내용을 정리한 개인 공부 목적용 저장소입니다.

## 변화를 타임캡슐에 담아 묻기

### 1. 프로젝트의 변경사항들을 타임캡슐(버전)에 담기

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176208705-76426320-5093-4883-8ae1-cfb412eff8ca.png">

- `No commits yet` : 아직 버전을 만들지 않은 상태.
- `Untracked files` : Git의 관리에 들어간 적 없는 파일.

1. 파일 담기
```
git add tigers.yaml // 파일 하나 담기
git add .           // 모든 파일 담기
```

2. 변경사항 확인
```
git status
```
<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176209056-8a5620fc-105b-45b6-9d14-ae9a7b04e860.png">

- `Changes to be committed` : 버전 관리할 준비가 되었음을 의미.


### 2. 타임캡슐 묻기

1. 아래 명령어로 `Commit`

```
git commit -m "FIRST COMMIT"
```

- `-m` : 커밋 메시지까지 함께 작성하기

2. 아래 명령어와 소스트리로 확인

```
git log
```

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176209260-5b949576-d272-465f-a17e-fab51292e133.png">


### 3. 다음 변경사항들을 만들고 타임캡슐에 묻기

#### 변경사항
1. `lions.yaml` 파일 삭제
2. `tigers.yaml`의 manager를 Donald로 변경
3. `leopards.yaml` 파일 추가
4. `git status`로 확인

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176209581-08415b95-aea7-4888-8abe-b8db36dfdfb4.png">

5. `git diff`로 상세 확인 : k 또는 j 위아래 스크롤 사용
6. 캡슐에 담기
```
git add .
```

7. 아래 명령어로 확인
```
git status
```
<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176210037-3239de42-3b31-44c0-b964-56e32e70c8d4.png">

8. 아래 명령어로 `Commit`

```
git commit -m "Replace Lions with Leopards"
```

9. 아래 명령어와 소스트리로 확인
```
git log
```
<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176210210-aec51c7b-440f-4021-8c0c-49687ab33708.png">

---

## 🐰 과거로 돌아가는 두 가지 방법

###  reset
- 원하는 시점으로 돌아간 뒤 이후 내역들을 삭제한다.
- 아예 현재가 없었던 것처럼 원하는 과거로 돌아갈 수 있다.
- reset은 이력을 남기지 않는다.

### revert
- 과거로 돌아가겠다는 이력을 남기고 원하는 시점의 커밋으로 돌아간다.
- 즉, 이전의 커밋 내역을 남겨두고 새로운 커밋을 생성하면서 과거로 돌아간다.

---

## 과거로 돌아가기 실습

### 1. reset 사용해서 과거로 돌아가기

1. 아래 명령어로 커밋 내역 확인

```
git log
```

2. 되돌아갈 시점 : `Add team Cheetas`의 커밋 해시 복사
3. 아래 명령어 입력

```
git reset --hard 돌아갈 커밋 해시
```

<img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176212878-b9e0eba5-8189-4eb5-a154-044fe8eb1622.png">

### 2. revert 로 과거의 커밋 되돌리기

1. Add George to Tigers의 커밋 해시 구하기
2. 아래 명령어로 **revert**
```
git revert 되돌릴 커밋 해시
```
3. `:wq`로 커밋 메시지 저장 [[참고] Vi명령어](#vi-명령어)

<div style="border: 1px solid #dfdfdf;">
    <img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176213453-76755745-a4d5-4a97-9620-6581c9b5870e.png">
</div>

### 3. 커밋해버리지 않고 revert하기

```
git revert --no-commit 되돌릴  커밋 해시
```

1. 원하는 다른 작업을 추가한 다음 함께 커밋하고 싶을 때 사용한다.
2. 취소하려면 `git reset --hard`

---

## SourceTree로 진행해보기

### 1. 변경사항 만들고 커밋하기

1. 커밋할 파일 `+` 버튼 클릭 / 모두 스테이지에 올리기
<div style="border: 1px solid #dfdfdf;">
    <img width="100%" alt="image" src="https://user-images.githubusercontent.com/108013728/176217920-61ad601d-6c7d-4dd8-be23-893c6706023a.png">
</div>

2. 커밋 버튼 클릭
3. 커밋 메시지 입력 후 커밋 버튼 클릭

### 2. revert
1. 해당 커밋에 마우스 우클릭 > 커밋 되돌리기 > 예

### 3. reset
1. 해당 커밋에 마우스 우클릭 > 이 커밋까지 현재 브랜치를 초기화
2. 사용중인 모드를 `Hard`로 변경 > 확인 > 예

---

### 참고

#### Vi 명령어

|작업|Vi 명령어|상세|
|:---:|:---:|:---:|
|입력 시작|i|명령어 입력 모드에서 텍스트 입력 모드로 전환|
|입력 종료|`ESC`|텍스트 입력 모드에서 명령어 입력 모드로 전환|
|저장 없이 종료|:q||
|저장 없이 강제 종료|:q!|입력한 것이 있을 때 사용|
|저장하고 종료|:wq|입력한 것이 있을 때 사용|
|위로 스크롤|k|`get log` 등에서 내역이 길 때 사용|
|아래로 스크롤|j|`git log` 등에서 내역이 길 때 사용|