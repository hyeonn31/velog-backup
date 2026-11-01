---
title: "[Unity] Visual Effect 초기화 블록 이해하기"
date: 2025-09-16T13:30:23.119Z
tags: ["Unity"]
velog_slug: Unity-Unity-Visual-Effect-초기화-블록-이해하기
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3908e96fb97a260b.png)

## 📘 Initialize Particle 
>:  파티클이 생성될 때 초기 속성을 부여

- capacity : 최대 파티클 수용량
- bounds :  파티클이 생성되는 위치  상대적 위치 및 범위

### 📕 Set attribute (Set이라는 방식을 통해 속성값 할당하기)
뭔가 데이터를 초기에 할당하고 싶다면 자연스럽게 Set을 생각하면 된다. 

> - Set velocity Random : 파티클이 힘을 받는 방향 설정
- Set Lifetime Random : 파티클의 수명 설정
- Set Position :  파티클이 생성되는 위치(Vector3)설정 -> x,y,z
- Set Size : 파티클의 크기 설정
- Set angle : 파티클의 회전값 설정

- initalize 블록에서는 파티클 초기의 기본적인 속성을 넣어주고, update/output블록에서 추가적인 속성을 부여

---



