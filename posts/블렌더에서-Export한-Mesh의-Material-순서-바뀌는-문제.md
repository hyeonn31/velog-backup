---
title: "블렌더에서 Export한 Mesh의 Material 순서 바뀌는 문제"
date: 2026-01-14T03:26:08.650Z
tags: ["blender", "export"]
velog_slug: 블렌더에서-Export한-Mesh의-Material-순서-바뀌는-문제
---
Export한 Mesh의 Material 순서 바뀌는 문제가 종종 발생한다. 

내가 겪은 예시로는 
블렌더에서는 메테리얼 순서가 
1. wear
2. logo
3. joint 
로 되어있는데

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/87c2c997e496bb4e.png)

유니티로 불러오면 메테리얼 순서가 변경되어 꼬이는 경우가 발생했다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/689168db7b2e5189.png)


---

보통은 블렌더에서 그냥 순서 조정해서 내보내도 그대로들어오지만 아닌경우 해당 방법을 사용해보자. 

## 방법 1. 해당 파츠 메테리얼로 분리 후 다시 합치기(단축키P)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ecec22a1f8b7edb0.png)
분리한 후

밑으로 깔고싶은부분부터 차례대로 잡은 후 ctrl+j로 합쳐준다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c220d45da5c8529a.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/35fdd325e1e8aa09.png)
다시 합쳐진 모습

그 후 다시 export해서 확인해보기


## 방법 2. Mesh > Sort Elements… > Material
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/189c52d2650b7ce6.png)

될 때가 있고, 안될 때가 있다... 그래서 일단 적용해보기