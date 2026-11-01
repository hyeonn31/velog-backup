---
title: "[Blender] 애니메이션 렌더링 시 프레임 속도 조정"
date: 2026-01-20T08:33:47.904Z
tags: ["blender"]
velog_slug: Blender-애니메이션-렌더링-시-프레임-속도-조정
---
블렌더에서 렌더한 애니메이션이 실제보다 빠르게 나오거나 느리게 나오는 경우는 거의 항상 프레임 설정 불일치 때문이다.


렌더 속도 = FPS 기준이라서
뷰포트에서 본 속도랑 FPS가 다르면 체감 속도가 달라짐

확인 경로

Output Properties (프린터 아이콘)
→ Frame Rate
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/872bdd4779fdc005.png)


### 보통 쓰는 값
- 게임/일반: 30 fps
- 영화: 24 fps
- 모션캡처/엔진용: 60 fps

예를 들어
애니메이션은 30fps 기준으로 만들었는데
출력이 60fps면
→ 2배 빠르게 재생됨

### ✅ 해결
→ 작업할 때 기준으로 했던 FPS로 맞추기