---
title: "[Blender] Root bone이 없는 상태에서 Hip이 최상위(root)로 승격되면서
Root Motion 정보가 소실되는 문제 | Motion Builder 사용"
date: 2026-01-22T02:27:25.357Z
tags: ["Motion Builder", "blender"]
velog_slug: Blender-Moion
---


# Root Motion 정보가 소실
가끔 모션 데이터 소프트웨어에 따라 
블렌더에서 모션데이터를 export 했을 때 Root bone이 없는 상태에서 Hip이 최상위(root)로 승격되면서
Root Motion 정보가 소실되는 문제가 발생한다. 
_(Root Motion이 Hip에 합쳐져서 빠지는 문제)_

## 문제 영상
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3db5d3d93ecdfca0.gif)

루트본 데이터를 잃어버려서 hip이 고정된 상태이다.
(다리가 뜨는 상황) 

### 원래 구조

> Root (이동 전용)
 └ Hips (골반, 몸의 중심)
    └ Spine
    └ Legs ...
    
  ### 블렌더 모션 Export
  
>    Hips (최상위가 됨)
 └ Spine
 └ Legs ...


---

이건 블렌더 문제라기보다
- FBX 구조
- 모션 데이터가 Root-less animation
- Mixamo / Rokoko / Mocap 데이터 등등..
여러가지가 겹쳐지면서 아주 흔하게 발생하는 현상이다.


## 해결방법 | Motion Builder
여러가지 서칭과 노가다를 해 본 결과
블렌더에서 해결하려고 하지말고 Autodesk - Motion Builder를 사용하는 것이 현명하다고 판단이 되었다. 


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1576ebe8f22de618.png)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/94d0b7d44a1a7417.png)
모션빌더 viewer에 드레그해서 모션데이터를 넣고,
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/649cb2c20aecf1b5.png)
FBX Merge -> All Takes 로 불러온다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/24c26a55894d132c.png)
불러온 모습

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6021afe299dae144.png)

Actior 바를 슬라이드 하여 애니메이션이 잘 들어갔는지 확인한 후

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d9f5b3fea33301d5.png)
File - Motion File Export클릭

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/415ba7673db1534a.png)
bvh로 저장

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ea2c588a63e8e147.png)
블렌더에서 bvh 임포트

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/878ee381cddbde9b.png)
정상적으로 들어옴 확인
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f86679c92d031741.gif)

---

### +(추가) 2인 이상일 경우 모션빌더에서 각각 따로 한 캐릭터씩 선택하여 익스포트 해야함.


