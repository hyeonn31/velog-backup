---
title: "[Git] 꼭 기억해야 하는 기본 명령어 정리"
date: 2025-09-07T09:20:28.157Z
tags: ["git"]
velog_slug: Git-꼭-기억해야-하는-기본-명령어-정리
---
# 꼭 기억해야 하는 기본 명령어 정리
## 📌 터미널 기본 명령어 | 리눅스 명령
➡️ Git을 쓰기 전에 컴퓨터 안에서 파일과 폴더를 다루는 기본기에 집중

### 📂 디렉터리(폴더) 이동 & 관리

- **cd ~** : 홈 디렉터리(집 폴더)로 이동

- **mkdir** mine : mine이라는 새 디렉터리 만들기

- **cd** mine : mine 디렉터리로 이동

- **cd ..** : 한 단계 상위(부모) 디렉터리로 이동

- **pwd** : 현재 내가 있는 경로 확인

---

### 👀 디렉터리 내용 보기

- **ls** : 현재 디렉터리 안의 파일/폴더 보기

- **ls -l** : 파일/폴더를 자세히 보기 (권한, 크기, 날짜 등)

- **ls -a** : 숨김 파일까지 모두 보기

---

### 🗑️ 파일 & 폴더 삭제

- **rm -r  ** mine : mine 폴더와 그 안의 내용까지 삭제
🔺이때 삭제할 디렉터리의 상위 디렉터리에서 rm명령을 입력해야함.

---

### 📝 파일 다루기 

- **vim** f1.txt : f1.txt 파일 만들거나 열기 (Vim 에디터 사용)

- **cat** f1.txt : f1.txt 파일 내용을 터미널에 출력

---

### 🔧 기타 자주 쓰는 명령어

- **clear** : 터미널 화면 깨끗하게 지우기

- **exit** : 터미널 종료

---

## 📌Git 자체 명령어 | Git으로 버전 관리하기 기초
➡️ Git이 실제로 코드 버전을 관리하고 GitHub 같은 곳과 연결하는 과정에 집중

### 🏁 Git 시작하기

- **git init** : 현재 폴더를 Git 저장소로 만들기 
깃을 사용할 수 있도록 디렉터리를 초기화하는 것(Git 관리 시작)

- **git clone [주소]** : 인터넷에 있는 저장소를 내 컴퓨터로 복사


---


### ✅ 파일 상태 관리

- **git status** : 현재 상태 확인 (추가됨? 수정됨? 커밋했는지?)

> 1. 현재 master브랜치에 있으며, 아직 커밋한파일이 없고, 현재 커밋할 파일도 없을 경우 
ㅎ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/04f4be874bb9755d.png)


> 2. 깃에서 아직 한 번도 버전 관리하지 않은 파일(Untracked files)이 있음
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/361ce9708be4b51e.png)
 

> 3. 다음과 같은 새 파일을 커밋할 것임
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/420394dc6b1c9ecd.png)


> 4. 버전 만들 파일이 없고, 작업 트리도 수정사항 없이 깨끗함 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/46abe33961938d66.png)

>5. 해당 파일이 수정되었고, 아직 스테이징 상태가 아님
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8c88d1d0b6edf672.png)

_더 자세한 내용은 아래 글을 참고하자. ⬇️_
[Git 파일 상태 쉽게 이해하기](https://velog.io/@heart/Git-Git-%ED%8C%8C%EC%9D%BC-%EC%83%81%ED%83%9C-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-Untracked-Modified-Staged-Unmodified#-%ED%9D%90%EB%A6%84)


---
### ♦️ 커밋 — 준비하기
- **git add [파일명]** : 특정 파일을 커밋할 준비하기 (스테이징)

- **git add . **: 현재 폴더 안 모든 변경 파일을 스테이징



### 💾 커밋(Commit) — 저장하기

- **git commit -m "메시지"** : 변경 사항 저장 (메시지 안에는 어떤 변경인지 짧게 적기)

---


### 📜 커밋 내역 보기

- **git log** : 커밋 기록 확인 | 방금 커밋한 버전에 대한 설명이 나타남. 커밋을 만든 사람, 만든 시간과 커밋 메시지가 함께 나타남. 수정한 파일을 커밋하면 이렇게 수정과 관련된 여러 정보를 함께 저장할 수 있고, 필요할 때 확인할 수 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4b00108eb848d680.png)
이때 commit 이라는 항목 옆에 영문과 숫자로 된 긴 문자열은 "commit hash" 또는 "git hash"라고 부른다. -> 커밋을 구별하는 아이디이다.

커밋 해시 옆에 있는 (HEAD -> master)는 이 버전이 가장 최신이라는 표시이다. 


- **git log --oneline** : 간단하게 한 줄씩 기록 확인

- **git log --stat** : 커밋에 관련된 파일까지 함께 살펴보기
가장 최근의 커밋부터 순서대로 커밋 메시지와 관련 파일이 나열된다. 
---

### 🖊️ 방금 커밋한 메시지 수정하기
- **git commit --amend** : 가장 최근의 커밋 메시지를 수정

### ➕ 스테이징과 커밋 한꺼번에 처리하기
- ** git commit -am** : commit 명령에 -am 옵션을 사용하면 스테이지에 올리고 커밋하는 과정을 한꺼번에 처리할 수 있다.
🔺단, 이 방법은 한 번이라도 커밋한 적이 있는 파일을 다시 커밋할 때만 사용할 수 있다. 

---

### ✔️ 변경 사항 확인하기
- ** git diff** : 작업 트리에 있는 파일과 스테이지에 있는 파일을 비교하거나, 스테이지에 있는 파일과 저장소에 있는 최신 커밋을 비교해서 수정한 파일을 커밋하기 전에 최종적으로 검토할 수 있음
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e93eff9dc1665cba.png)
-2는 '2'가 삭제되었다는 뜻이고, 
+two는 'two'라는 내용이 추가되었다는 뜻

---

### ✖️ .gitignore 파일로 버전 관리에서 제외하기
버전 관리 중인 디렉터리 안에 버전 관리를 하지 않을 특정 파일 또는 디렉터리가 있다면 .gitignore파일을 만들어 목록을 지정할 수 있다. 빔을 사용해서 .gitignore 파일을 만들어 그 안에 버전 관리하지 않을 파일 또는 디렉터리 이름이나 파일 확장자를 입력하면 된다. 

주로 개인적으로 메모해 놓은 파일이나 프로그램 사용 중에 자동으로 생성된 swp파일, 백업 파일 등이 이 목록에 포함된다. 


---

### 🔄 원격 저장소와 연결

- git remote add origin [주소] : 원격 저장소(GitHub 등) 연결

- git push origin main : 내 변경 내용을 원격 저장소로 올리기

- git pull origin main : 원격 저장소에서 최신 내용을 가져오기

---

### 🛠️ 가지(branch) 다루기 
- git branch : 브랜치 목록 확인

- git branch [브랜치명] : 새 브랜치 만들기

- git checkout [브랜치명] : 해당 브랜치로 이동

- git merge [브랜치명] : 브랜치 합치기

---


👉 이렇게만 알아도 기본적인 Git 흐름은 알 수 있다.
보통 순서는

```
git init → git add → git commit → git push
```


이렇게 많이 쓰인다.

>**[0] 초기 설정 (처음 한 번)**
    git config --global user.name  "이름"
    git config --global user.email "이메일"
                |
                v
**[1] 프로젝트 폴더 준비**
    mkdir myapp
    cd myapp
                |
                v
**[2] Git 시작**
    git init
    git branch -M main   # 선택(메인 브랜치 이름 정리)
                |
                v
**[3] 파일 만들기/수정**
    (예: README.md 작성/수정)
                |
                v
**[4] 상태 확인**
    git status
                |
                v
**[5] 스테이징(add)**
    git add .            # 전부 올리기
    (또는) git add 파일명
                |
                v
**[6] 커밋(commit)**
    git commit -m "변경 내용 한 줄 설명"
                |
                v
**[7] 원격 연결(처음 한 번)**
    git remote add origin https://...git
                |
                v
**[8] 첫 푸시(처음 한 번)**
    git push -u origin main
                |
                v
**[9] 이후 반복 루틴**
    (협업이면 먼저) git pull origin main
    수정 → git status → git add → git commit → git push


---

### 💡 작은 팁

커밋 메시지는 “무엇을, 왜”를 짧게: feat: 로그인 버튼 색 변경 처럼.

파일을 빼먹었으면 다시 git add → git commit --amend(메시지 재사용)도 가능.

푸시 전에 팀 작업이면 항상 git pull origin main으로 최신 반영!