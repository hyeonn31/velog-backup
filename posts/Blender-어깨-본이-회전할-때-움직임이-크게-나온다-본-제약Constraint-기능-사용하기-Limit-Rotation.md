---
title: "[Blender] 어깨 본이 회전할 때 움직임이 크게 나온다? 본 제약(Constraint) 기능 사용하기 | Limit Rotation"
date: 2025-09-09T08:19:04.387Z
tags: ["blender"]
velog_slug: Blender-어깨-본이-회전할-때-움직임이-크게-나온다-본-제약Constraint-기능-사용하기-Limit-Rotation
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a86cc7dd254ebe06.png)
캐릭터 리깅을 진행할 때 본데이터가 제약범위를 넘어 씹히는 경우가 있다. 

이를 방지하는 방법이 바로 본에 제약조건을 걸어 자연스러운 범위 안에서만 움직이도록 하는 것이다. 

**1. 어깨 본 선택 → Pose Mode로 들어가기**
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/35e1d62763d87915.png)![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ce16e5ca57eadaf7.png)



**2. 오른쪽 패널에서 Bone Constraints 탭(체인 모양 아이콘) 열기**
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9263e5ad56c83286.png)

**3. Add Bone Constraint → Limit Rotation 추가**
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/190f073a4d912411.png)

**4. 설정:**
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7e8df159dc748a40.png)

X / Y / Z 축 중 필요한 축만 활성화 (예: X,Z축 회전만 제한)

Minimum / Maximum 값 입력해서 회전 범위를 제한

**Owner-> Local Space**로 맞추면 본의 로컬 축 기준으로 제한 가능

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/048ef5bf35762013.png)
마찬가지로 메쉬도local모드로 변경

아직 정확한 기준을 모르겠어서 우선 이리저리 회전해보면서
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/aab880624c012314.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5275a319103d9061.png)
원하는 모양이 나올 때까지 제한을 걸어준다. 

---
 
### 하지만 유니티에서는 블렌더 제약은 무용지물이고, 유니티 쪽에서 제약을 따로 걸어야 한다.

블렌더 제약조건은 유니티에 안 넘어감.

유니티 안에서 실시간 제약을 원한다면:
- Animation Rigging 패키지 → 제약 설정 (추천)
- 직접 C# 스크립트로 각도 Clamp (유연) 설정
