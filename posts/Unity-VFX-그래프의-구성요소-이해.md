---
title: "[Unity] VFX 그래프의 구성요소 이해"
date: 2025-09-10T14:28:26.116Z
tags: ["Unity"]
velog_slug: Unity-VFX-그래프의-구성요소-이해
---
기본적으로 비주얼 그래프의 파티클이 만들어지고 작동하는 원리는

## 📕 SET과 GET
set : 파티클의 attribute(속성) 데이터를 할당하는 것
get attribute: 앞서 set으로 할당한 attribute(속성) 데이터를 받아온다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4d7e75b3eeb35452.png)

initialize에서 set으로 attribute를 넣어주고
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/85733a662544a6f2.png)

update에서 get으로 attribute를 가져오는 것이 일반적이다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3eae997e907190b8.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/aeb5a16276f1e789.png)


그 후 out put에서 다시 set으로 재할당하게 되면 의도하는 결과물이 생성된다.

attribute외에도 함수나 로직, time등을 통해 파티클을 변화시킬 수 있다. 

## 📕 System(Template)  
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d57a9b9eba14811c.png)

독립된 contexts들의 연결된 노드로 이루어져 있다. 
이러한 샘플들이 있기 때문에 조금씩 비틀어가며 작업을 하면 빨리 진행할 수 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/297ebadd2d3bf56b.png)
