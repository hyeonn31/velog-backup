---
title: "[Blender] 모든 오브젝트에서 애니메이션(키프레임) 삭제 방법 | 원치 않는 애니메이션, 머터리얼 삭제 방법"
date: 2025-07-23T02:20:19.404Z
tags: ["blender"]
velog_slug: Blender-모든-오브젝트에서-애니메이션키프레임-삭제-방법-원치-않는-애니메이션-삭제-방법
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f101dae7a53aceb7.png)
블렌더에서 작업을 진행 중 렉이 많이 걸려서 찾아보니
모든 오브젝트에 원치 않는 애니메이션이 들어가 있었다. 
그래서 유니티에서 엄청 오래 임포트 되었던...


이 부분을 해결하기 위해 쉬운 방법으로 

## 📘 오브젝트클릭 후 Alt + A -> 삭제 
이렇게 해서 삭제 되었으면 좋으련만
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b290c2b301c67410.png)
Report:Error가 났다.

그렇다면 다음 방법은 스크립팅을 이용하는 것이다.


---
 ## 📘 Python 스크립트로 전체 키프레임 삭제 (확실한 방법)
 
 ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/99fe266cf9a40b6a.png)
상단 Scripting바를 클릭하고 console창에 
```

import bpy

for obj in bpy.data.objects:
    if obj.animation_data:
        obj.animation_data_clear()
```
을 넣고 Enter 2번 (블렌더에서는 한 줄 더 빈 줄을 넣어줘야 실행됨)

[위 코드는 모든 오브젝트에서 애니메이션 데이터를 완전히 지운다. (위치, 회전, 스케일 포함)]


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ddaf647d85bead20.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/72626ed6f2116823.png)

다시 레이아웃 모드로 돌아와서 보면 모두 지워진 모습을 볼 수 있다.

---
### (선택) 모든 Shape Key 애니메이션도 제거
만약 쉐이프 키(Shape Keys)에 애니메이션이 있다면 아래도 실행
```
for obj in bpy.data.objects:
    if obj.data.shape_keys:
        if obj.data.shape_keys.animation_data:
            obj.data.shape_keys.animation_data_clear()
```


---

### 💡 보너스 팁: 애니메이션이 들어있는 오브젝트 찾기
Timeline에서 아무것도 안 보이는 경우 그럴 땐 아래처럼 찾을 수 있다.
```
for obj in bpy.data.objects:
    if obj.animation_data:
        print(obj.name)

```
---
시원하다

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3a59e13be9ebe070.png)

---

## 📘 머터리얼 전부 삭제
```
import bpy

for obj in bpy.data.objects:
    if obj.type == 'MESH':  # 메시 타입 오브젝트만 대상으로 함
        obj.data.materials.clear()

```

