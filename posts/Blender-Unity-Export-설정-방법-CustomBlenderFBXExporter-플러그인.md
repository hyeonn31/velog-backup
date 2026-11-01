---
title: "[Blender] Unity Export 설정 방법 | [CustomBlenderFBXExporter] 플러그인"
date: 2025-08-29T00:52:25.928Z
tags: ["blender"]
velog_slug: Blender-Unity-Export-설정-방법-CustomBlenderFBXExporter-플러그인
---

블렌더에서 리그와 함께 메시만 내보내려고 했을 때, 계층 구조에 'Armature'라는 빈 루트 본이 추가된다..

내가 내보낸 모델이 내가 가져온 모델과 다른것을 확인할 수 있다.

이는 다른 애니메이션 파일이 뼈대 계층 구조와 일치해야 하기 때문에 Unity 애니메이션 시스템과 호환되지 않는다.

최악의 상황은 현재 FBX 익스포터(2021)에서 'Key All Bones' 옵션을 켜면 'Armature'(원치 않는 루트 본)에 대한 애니메이션 곡선이 생성된다. 이로 인해 Unity 네이티브 루트 모션이 작동하지 않는다.

이는 원래 개발자의 잘못은 아니다. Blender 의 API는 플러그인이 내보내는 데 사용하는 구조를 노출하기 때문.

'아마추어'는 블렌더 데이터의 일부이다 원래 내보내기 기능은 API에서 받은 데이터를 그대로 내보낸다.

그래서 아마추어 데이터를 제거하기 위한 플러그인이 있다. 

## 💎 CustomBlenderFBXExporter 링크
> https://github.com/A-Ribeiro/CustomBlenderFBXExporter
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/110f9afe4ac05467.png)

위 플러그인을 다운받은 다음 압축을 풀지 않고 블렌더 설정에서 Add-ons 화면에 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bf7fb1fffee3bd4d.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e57e07bd1c6ff583.png)
우측 상단 화살표를 클릭하여 Install from Disk를 클릭해서 압축파일을 불러온다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b69981126755eeea.png)
그럼 익스포트 창에 aRibeiro가 생성된 것을 알 수 있다. 

해당 설정으로 익스포트 한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6c87394b7ab7266f.png)
