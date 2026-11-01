---
title: "[Blender] 블렌더에서 본(Bone)을 움직일 때 메시의 스케일 작아지는 문제"
date: 2025-09-11T02:52:49.056Z
tags: ["blender"]
velog_slug: Blender-블렌더에서-본Bone을-움직일-때-캐릭터의-스케일이-작아지는-문제
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/20f26f90feb22327.gif)

본에 메쉬를 리깅했을 때 회전 시 메쉬의 크기가 변형되는 경우가 있다.
이때 가장먼저 확인해봐야할 부분은 **Amature에서 Preserve Volume에 체크**가 되어 있는지이다.


---

### 방법
1. Object Mode로 전환.

2. 스케일이 줄어드는 **메시(Object)**를 선택. (본이 아니라 캐릭터 메쉬)

3. 오른쪽 속성 패널에서 렌치 아이콘(Modifier Properties) 클릭.

4. 이미 리깅을 했기 때문에 리스트 중에 Armature라는 수정자가 있을 것이다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/77182720bb074e11.png)


> 없으면 Add Modifier → Deform → Armature에서 새로 추가할 수 있다.
- **Object** : 캐릭터와 연결할 Armature 오브젝트 선택.
- **Preserve Volume** : 체크하면 스케일이 작아지는 문제를 방지.
- **Vertex Groups** : 웨이트가 지정된 본 그룹을 사용.
- ** Bind To **: 보통 Vertex Groups와 Bone Envelopes 중 Vertex Groups를 선택.

5. preserve Volume 체크
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1e8a567b17248f27.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3f2272bfecf3cabd.gif)

이제 본을 움직여도 메쉬의 크기는 변하지 않는다.

(●'◡'●)(●'◡'●)

