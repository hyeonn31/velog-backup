---
title: "[Unity] Visual Effect | Set Custom Node"
date: 2025-09-16T14:46:41.078Z
tags: ["Unity"]
velog_slug: Unity-Visual-Effect-Set-Custom-Node
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f38a2e57d1f64876.png)

## 📕 Set/Get Custom Value
> : 원하는 value값을 자유롭게 추가하고 사용할 수 있는 노드

---

### 방법
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ec7002962549cd1d.png)
 
1. Set CustomAttribute 노드 추가
2. Inspector에 추가한 노드가 나타남
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f3eb1cc53c5cedf7.png)

---


3. 연결하고자 하는 노드의 Attribute Type 지정하기
(Set과 Get의 이름과 Attribute는 동일해야한다. )

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6293a29b939661b5.png)

이름  SpecialValue로 변경, Vector3로 변경

---


4. 그래프 블록 밖에 Get CustomAttribute 노드 추가

  ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/53cb583abe24831a.png)
  유니티 안 inspector창에서 set처럼 이름을 변경할 수 있다. 
**** Custom Attribute의 이름을 변경할 경우, Get custom도 똑같은 이름으로 변경 ( =이름이 동일해야한다. )**
    
  
Get도 마찬가지로 SpecialValue로 변경해주고, 앞게 Set CustomAttribute에서 Vector3로 했으니 똑같이 변경해준다.


   
 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e871ccffeed12219.png)

---

5. 노드 연결(사진찍는걸 까먹어서...이름 hi로 편의를 위해 급하게 넣어놨음)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0ce2312a6c88d628.png)



---

# 🚨🚨🚨 Custom Attribute가 안뜰경우
열받게도 유니티 21.3.9f1버전에선 자동 활성화가 아니였던 것이다... 한시간동안 찾았다. 

edit - Preferences - visual effects - 두번째 항목 체크
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ace63da03ecfb79e.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5c25af0b2d62813f.png)

