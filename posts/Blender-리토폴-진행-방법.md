---
title: "[Blender] 리토폴 진행 방법"
date: 2025-07-04T05:11:21.290Z
tags: ["blender"]
velog_slug: Blender-리토폴-진행-방법
---


## 블렌더에서 시작 방법
https://extensions.blender.org/add-ons/polyquilt-fork/
해당 사이트에서 PolyQuilt 다운로드 후 블렌더에 가져오기

그 후 블렌더에서 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/eb4b9506572a0c54.png)
Install from Disk를 통해 다운로드 파일 가져오기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6f18813b68f1acef.png)
활성화(체크)

그럼 이렇게 툴바에 하나 아이콘이 추가된다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c3e9de37d1659b56.png)



![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d9da39132b6245d0.png)
우선 예시를 위한 작은 공 상태에서 시작
Plane 추가
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b2500de2917467b1.png)


Edit 모드로 변경(Teb)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/417009b363f2e6b0.png)

상단에 Snap활성화, 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/609a314668b6c742.png)

Face로 변경
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/59aa3ddaf91b4d66.png)

Retopology 활성화
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ccfec794dd6bc56e.png)

색은 여기서 바꿀 수 있다. (현재 더 잘보이게 하기 위해 변경함)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5e89bba25fff2027.png)

꺼냈던 Plane은 다시 삭제
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d0a5ff81aa24cf24.png)

PolyQuilt 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/865dd221b2d9c657.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ac91b1a5e97e2506.png)
잘된다. 


----

## 리토폴 진행 방법

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fbaba548b719cfc8.png)
선에 마우스를 가져다 대면 작은 화살표가 흰색으로 변경된다. 그때 드레그 하면 하나의 면을 더 뽑을 수 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f97bcd5657706ef2.png)
이런식으로


**선 + shift : 예측하여 리토폴 자동 생성 기능 
선 + ctrl : 전체 자르기
선 + 선 : 그 만큼 자르기
길게누르기 + 면 : 면 삭제
길게누르기 + 점 : 점 삭제
길게누르기 + 선 : 선 삭제**

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d0f708e491567d23.png)
이런식으로 리토폴을 하다보면 모양이 망가지는 경우가 생기는데 
**shift+ 문지르기** : 부드럽게 릴렉스 (펴지기)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bf41b5ffb8075883.png)
유용한 기능이다. 


---

## PolyQuilt 애드온의 다른 기능
### 1. EdgeLoop
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/37ce720258197a6f.png)
전체 모서리를 이동하거나 모서리 경계에서 새 면을 만들 수 있다.

### 2. LoopCup
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6fad50b720d1ef91.png)
엣지루프로자르기가 가능하다
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a73c5327dd76668f.png)

### 3. Knife 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7c4c280e5471468d.png)
자르기기능

### 4. Delete
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b56f66855aad1753.png)
한번에 삭제 가능
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5f92ec990d25b616.png)

### 5. Seam 
이음세 라인 확인 가능(Ctrl이랑 같이 쓰면 루프로 선택)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/57ba4e0bf7b2260d.png)

### 6. Edge Extrude(점에서 당기기)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/311291c9d4177f21.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/53244b6e86a5a374.png)

### 7. mirror
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1ac24d8ced12ed6d.png)
우측상단

### 8. symmetrize
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/15f9f2ae0eeba383.png)
한 면에 했을 경우
모든 면을 선택하고 메시 메뉴로 가서 symmetrize 선택
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5cf1fe3fc27a49ed.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7cd3c96e49edf5a3.png)
원하는 위치 선택
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0e207eb0f10ae9d2.png)
복사된 모습


### 9. 리토폴 띄우기(공간) + 부드럽게 정리 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/242bf7412cde842f.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/49183997f29b8330.png)
offset 으로 조절


