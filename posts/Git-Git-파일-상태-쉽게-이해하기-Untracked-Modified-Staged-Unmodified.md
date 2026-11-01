---
title: "[Git] Git 파일 상태 쉽게 이해하기 (Untracked, Modified, Staged, Unmodified) "
date: 2025-09-07T14:15:16.696Z
tags: ["git"]
velog_slug: Git-Git-파일-상태-쉽게-이해하기-Untracked-Modified-Staged-Unmodified
---
# 📌 핵심(한줄 요약)

>- **untracked** = 깃이 모르는 새 파일
- **modified** = 깃에 있던 파일을 내가 바꿨음(아직 스테이지X)
- **staged** = 다음 커밋을 위해 올려둔 상태(준비 완료)
- **unmodified** = 마지막 커밋과 같아서 변경 없음

---

## 📘 Git의 세 공간

Git은 파일을 세 군데로 관리한다. :

**1. 작업 디렉터리(Working Directory)** — 내가 실제로 파일을 편집하는 곳 (내 컴퓨터 폴더)

**2. 스테이징 영역(Staging Area / Index)** — 커밋할 내용을 잠깐 담아두는 곳(준비 박스)

**3. 로컬 저장소(Repository / HEAD)** — 최종적으로 저장된 커밋들이 있는 곳(금고)

### ♒ 흐름:
> 작업 디렉터리 → (git add) → 스테이징 → (git commit) → 로컬 저장소

---

## 1) Untracked (추적되지 않는 파일)

>= 새로 만든 파일인데 Git이 모르는 상태야. 아직 git add 한 적 없음.

예시: notes.txt를 새로 만들었다. 
git status하면 **Untracked files:**에 **notes.txt**가 보인다.

>🛎️ **보는 명령어: git status**

#### 처리 방법:
- 저장하고 싶으면: git add notes.txt → (스테이지로 이동)
- Git에 포함시키기 싫으면: .gitignore에 이름 추가

🔺한 줄 요약: 새 파일 = Git이 모름 → git add 해서 알려줘야 함.

---


## 2) Modified (수정된 파일)

>= 그 파일은 이미 Git이 알고(커밋된) 있었지만, 내가 편집해서 내용이 바뀐 상태. 아직 스테이징은 안 함.

예시: notes.txt를 커밋한 뒤 내용을 고쳤어. git status에 modified: notes.txt로 나옴.


> 🛎️ 차이 보는 명령어: **git diff** notes.txt → 작업 디렉터리의 변경사항(아직 스테이지X)을 보여줘.

#### 처리 방법:
- 커밋 준비하려면: git add notes.txt → staged 상태로 옮김
- 변경 취소하려면(원래대로 돌리고 싶으면): git restore notes.txt (안전하게 되돌림)

🔺한 줄 요약: 수정은 했지만 아직 준비(스테이지) 전 상태.

---

## 3) Staged (스테이지된 파일)

>= 파일의 변경사항이 스테이징 영역에 올라간 상태 — 다음 git commit에 포함될 준비가 완료됨. (새 파일 또는 수정된 파일 모두 해당 가능)

예시: git add notes.txt 한 뒤 git status에 Changes to be committed:로 보임.

>🛎️ 차이 보는 명령어: **git diff --staged** 또는 **git diff --cached** → 스테이지된(커밋될) 내용의 차이 보여줌.

#### 처리 방법:

- 커밋하려면: **git commit -m "메시지"**
- 스테이지에서 빼려면: **git reset HEAD** notes.txt 또는 **git restore --staged** notes.txt

🔺한 줄 요약: 스테이지 = “커밋 직전의 대기열”.

---

## 4) Unmodified (변경 없음)

>= 작업 디렉터리의 파일이 마지막 커밋(HEAD) 과 동일한 상태. 즉, 변경 사항 없음.

무엇을 의미하나?: 안정된 상태 — git status가 nothing to commit, working tree clean 처럼 보이면 모든 게 unmodified.

🔺 한 줄 요약: 손대지 않은, 커밋과 같은 상태.


---

###  빠른 명령어 치트 시트
상태 확인: **git status**

수정(스테이지 전) 비교: **git diff**

스테이지된 내용 보기: **git diff --staged** (또는 --cached)

스테이지에 올리기: **git add <파일>**

스테이지에서 빼기: **git reset HEAD <파일>** 또는 **git restore --staged <파일>**

변경 되돌리기(작업트리에서): **git restore <파일>**

커밋하기: **git commit -m "메시지"**


