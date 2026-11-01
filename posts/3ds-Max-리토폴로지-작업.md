---
title: "[3ds Max] 리토폴로지 작업"
date: 2024-05-18T15:26:39.267Z
tags: ["3ds Max", "리토폴로지"]
velog_slug: 3ds-Max-리토폴로지-작업
---
1. obj로 불러온 작업물 mash로 되어 있기 때문에 Editable Poly로 변경해준다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0343aa3d51312135.png)


2. 좌측 상단에 Freeform
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bdf00e515e9bd96a.png)


3.
Grid부분 아래화살표 클릭 - Draw On : Surface
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7d464d869ab9a9fc.png)

그럼 Pick이라는 버튼이 활성화 된다. 클릭해주자.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f160b7bfe2e8e8bb.png)

그 후 내 오브젝트 클릭

그러면 Pick자리에 내 하이폴 이름이 등록이 된다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4e7077e1c62715a3.png)

이 상태에서 PolyDraw클릭 -> New Object클릭 : 그럼 버텍스에 불이 들어온다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7a1287d4986329da.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/be0b07adec1c0381.png)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/be0956fbed8097b2.png)
이 두가지 기능으로 우린 면을 만들어 줄 것이다. 

> ### **1. Step Build : 점을 찍어서 만들어 줄 때 씀 **

점 4개를 찍은 후 ㅣ커서를 가져다 대고 shift + 왼->오 드레그 해주면 면이 생긴다. 


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f23ca89b2ba874a0.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c585e4a7ae7adee1.png)


짠



![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1e8cc0d3f89b2847.png)
이렇게 

하이폴과 면이 겹쳐지면 안된다. 
그래서 이럴 땐 Offset수치로 조절해 준 후 Conform버튼 을 누르고 해당 부위를 문질러주면 적용이된다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/32f76e9e0b4e088d.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/159dfd1c7e66d72b.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/86a9e2d269a07b4a.png)

짠


>#### Step Build 단축키 모음
 Ctrl + Shift + Art : 점하나 이동(Drag)
Atr + 점 찍으면 : 점 하나 삭제



> ### 2. Extend : 면을 만들어 줄 때 씀

Shift + 클릭 드레그 해주면 면이 뽑힌다.

>#### Extent 단축키 모음
옆면을 뽑을 때에는 모서리 점 부분 클릭해서 드레그 해주기![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d64434602d0ce06b.png)
Ctrl + 면 클릭 : 면 지워짐
Ctrl + Shift : 여러면 한번에 뽑기


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5be85c4bcab9e243.png)

이 버튼은 만져주기 버튼



![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9964e41fc8bf9a9d.png)

떨어져 있는 면 합칠 땐 Optimize 클릭하고 shift누른 상태로 점에서 점 드레그
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/227a53d6c1607ebf.png)

---

### * 이때 선택한 부분만 엣지 보이게 적용하는 법
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5d4d55d80ebe38ce.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/18d0bca26d4b15ba.png)

Display Selected with Edged Faces클릭



--------


## 분리해서 사용할 것
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/28df6d43bac29cd1.png)
자 이렇게 지브러쉬에서 한 덩어리를 가지고 왔다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c4e4eb648ff65615.png)
이렇게 하나하나 디테치 해서 사용할 것