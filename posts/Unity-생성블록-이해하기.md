---
title: "[Unity] Unity Visual Effect 생성블록 이해하기"
date: 2025-09-10T14:45:12.121Z
tags: ["Unity"]
velog_slug: Unity-생성블록-이해하기
---
## 📘 Spawn System 
> : 파티클의 생성을 담당(얼마나 많이, 어떤 주기로)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a2d569f541d9d919.png)


###  	♦️ Constant Spawn Rate 
> : 지속적으로 (초당)정해진 양의 파티클을 생성

### ♦️ Variable Spawn Rate 
> : x~y범위의 (초당)양과 주기로 파티클을 생성

### ♦️ Single Burst 
> : 파티클을 일회성으로 생성(SendEvent())

- constant(고정 값)과 random(랜덤 범위값) 적용 가능

- **Count** : 생성할 파티클의 양
- ** Delay** : 파티클 생성 이벤트 발생 후 딜레이 값
 -  Single Burst는 Event block으로 제어
 
 
  - SendEvent(eventNameOrld)
  - SendEvent(eventNameOrld, eventAttribute)
   
   