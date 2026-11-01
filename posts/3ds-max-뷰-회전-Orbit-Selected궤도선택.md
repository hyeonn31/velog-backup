---
title: "[3ds max] 뷰 회전 | Orbit Selected(궤도선택)"
date: 2025-03-06T07:15:53.476Z
tags: ["3ds Max"]
velog_slug: 3ds-max-뷰-회전-Orbit-Selected궤도선택
---


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0fdbb06877af2aa4.png)

##  Orbit Selected는
>3ds Max에서 선택한 오브젝트를 중심으로 회전(Orbit)하는 기능이다. 일반적인 Orbit 기능은 씬(Scene)의 중심을 기준으로 카메라를 회전시키지만, "Orbit Selected"는 선택한 특정 오브젝트를 중심으로 카메라를 회전시킬 수 있다.

--------

### 1. Orbit Selected 기능의 사용 목적
✔️ **선택한 오브젝트에 집중:** 씬 전체가 아니라 특정 오브젝트를 자세히 관찰하고 수정할 때 유용하다.
✔️ **빠른 작업 흐름:** 복잡한 씬에서 특정 오브젝트를 중심으로 쉽게 작업할 수 있다.
✔️ **정밀한 조작:** 작은 오브젝트나 특정 부분을 더 편하게 다룰 수 있다.

----
### 2. Orbit Selected 활성화 방법

**① 단축키 사용**
1. 오브젝트 선택 (Mesh, Light, Camera 등)
2. [Z] 키를 눌러서 선택한 오브젝트를 뷰의 중심으로 정렬
3. **[Alt] + [Middle Mouse Button (휠 클릭)]** 을 누른 채 마우스를 움직이면 선택한 오브젝트 중심으로 Orbit이 작동

**② Viewport Navigation 버튼 사용**
1.오브젝트 선택
2.Viewport 오른쪽 아래 Navigation 패널에서 "Orbit" 아이콘 클릭
3.**"Orbit Selected"** 모드로 변경

**③ 마우스 우클릭 메뉴 사용**
1.오브젝트를 선택한 상태에서 Viewport에서 마우스 우클릭
2."Tools (도구)" → "Orbit Selected" 클릭
3.마우스를 움직여서 원하는 방향으로 Orbit 조작

------------

### 3. Orbit Selected 모드 종류
Orbit Selected 기능에는 몇 가지 다른 옵션이 있습니다.

#### ③ Orbit (기본 Orbit 모드)
- 특정 선택 없이 씬 전체를 중심으로 Orbit
- 뷰 중심을 회전의 중심으로 사용하기 때문에 오브젝트가 뷰포트의 가장자리에 있으면 회전하면서 시야를 벗어날 수 있다. 

#### ④ Orbit Selected(선택한 궤도)
- 클릭하면 노란 원이 뜨는데 그 노란원을 중심으로 회전함. 

#### ① Orbit SubObject (서브 오브젝트 회전)
- 선택한 Vertex, Edge, Face 같은 하위 요소를 중심으로 회전
- Editable Poly나 Editable Mesh 편집 시 유용
- 궤도 하위 오브젝트로 현재 선택한 것의 중심을 회전의 중심으로 사용

#### ② Orbit Point of Interest (관심 지점 회전)
- 특정 지점을 기준으로 Orbit
- 주로 Camera 작업 시 사용
- 클릭하면 점이 생기는데 그것이 커서 위치(관심점)가 되고 , 
그것을 중심으로 회전하게 된다. 뷰가 중심을 기준으로 회전하는 동안 관심점은 뷰포트에서 같은 위치를 유지한다. 

----

### 4. Orbit Selected 활용 팁

✅ 복잡한 씬에서 특정 오브젝트에 집중할 때: 너무 많은 오브젝트가 있으면 작업하기 어려운데, Orbit Selected를 사용하면 원하는 대상에 쉽게 초점을 맞출 수 있습니다.

✅ 캐릭터 모델링 시 얼굴이나 손가락 같은 작은 부분을 수정할 때: 원하는 부분만 확대하고 회전할 수 있어 세밀한 작업이 가능함.

✅ 카메라 애니메이션 작업 시 특정 지점 주위를 도는 경로를 만들 때 유용.

----

### 5. Orbit Selected가 작동하지 않을 때 해결 방법

- Z 키를 눌러 뷰를 리셋
- 오브젝트가 너무 멀리 있을 경우, Perspective 뷰에서 작업
- Viewport 설정에서 Orbit 모드를 확인 (Viewport Navigation 메뉴에서 변경 가능)


---
### 결론
3ds Max의 **Orbit Selected** 기능은 **선택한 오브젝트를 중심으로 회전하여 작업할 수 있도록 도와주는 강력한 도구**입니다. 모델링, 애니메이션, 씬 구성 등 다양한 작업에서 유용하게 활용할 수 있으니 익숙해지면 작업 속도가 훨씬 빨라질 것 😊
