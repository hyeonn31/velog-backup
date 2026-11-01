---
title: "[Zbrush] 머리카락 끝부분 표현"
date: 2025-01-17T14:30:33.125Z
tags: ["Zbrush", "머리카락"]
velog_slug: Zbrush-머리카락-끝부분-표현
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6b8860b9f57b9ea8.png)
### **1. 서브툴 Cube 3D를 꺼낸다.**
어김없이 Shift+F 눌러서 프레임 켜주고

### **2. 폴리그룹 - Group By Normals로 그룹 재배치해주기**

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8590784d97bf18a5.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/76997a76da172b0c.png)

### **3. Geometry - ZRemesher - KeepGroups클릭 후 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d033f6cce1e3fb5e.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9164cec83d2dbcd7.png)
ZRemesher클릭~
그리고 Hair(절반) 클릭 후 원하는 사이즈 나올 때까지 Zremesher클릭해서 면수 줄이기


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/68ffa94fc30b3ec0.png)
이렇게 최소화 면으로 만들어주자. 


### 4. brush - ZModeler -> Edge 부분 마우스 대고 - spacebar - insert를 활용해서 선 지우기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9fc16c0bda7576d1.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5b5313a0c434fc0c.png)
Alt누른 상태로 지워나가기

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/73dcc54e84df6095.png)
### 5. 위쪽면만 마스킹해서 반전해주고 -> 방사형으로 모양 만들어주기(윗부분 줄이기)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/940260078de3ded4.png)
뒷부분도 엣지 두군데 잡아서 마스킹 후 사선으로 컷팅된 듯한 모형으로 변형해주기

### 6. Divide가 없는 상태에서는 Ctrl 누른 상태로 드레그 하여 같은 Subtool내에서 복사를 할 수있다. 복사해주자.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a49721373572a9a1.png)
윗부분에 나온 폴리그룹노멀을 이용하여 각자 다른 그룹의 객체가 될 수 있도록 만들어주면서 작업한다. 


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f4e51116a9de2e8b.png)
어느정도 머리카락 덩어리를 완성했다면

### 7. Geometry - 크리즈 - 크리즈 폴리그룹 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/45dfb5858e1c2627.png)


### 8.  Ctrl+D ->  디바이드 2번 올려주기 
### 9. Geometry - 크리즈 - 전체 언크리즈 클릭
### 10. Ctrl+D -> 디바이드 1번 올려주기

이 과정을 거치면
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6e1f7cc21b3084a2.png)

이런 느낌? 
> * 팁이 있다면 위에서 봤을때 어느정도 채워진 느낌이 들어야 한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/56a7c56d6c93c580.png)


### 11. Geometry - Divide - 하위레벨 삭제
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f91aba0827c16891.png)

### 12. brush - inflat 사용해서 팽창시키기 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2cb6d1cddb29ba95.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8c67fc347e4fedbe.png)
이렇게 하면 좀 더 뭉쳐 있는 너낌이 든다

이제 이 상태에서 DynaMesh를 활용해 보자

### 13. 밀도 1000이상으로 맞춰주고 다이나메쉬로 합쳐주기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/df64649be1590069.png)

### 14. Smooth활용해서 깔끔하게 정리

### 15. Move Brush활용해서 휘어짐 표현
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9042cb3fc6e4f4e8.png)
### 16. Ctrl+Shift 누른 후  KnifeCurve로 윗부분 날리기


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2897848b65db4bf6.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bc7135c6e496c65e.png)

### 17. brush - Pinch 활용해서  
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ea377a9d2947fc0f.png)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3178a3fccd4a7e93.png)
Alt누른 상태로 끝부분 클릭 드래그하여 모아주기

move나 inflat ,,등등 알아서 다듬기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f6bd67a83cc088db.png)

요런 느낌