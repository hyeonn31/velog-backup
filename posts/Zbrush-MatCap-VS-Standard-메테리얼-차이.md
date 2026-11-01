---
title: "[Zbrush] MatCap VS Standard 메테리얼 차이"
date: 2025-01-18T06:14:32.681Z
tags: ["Zbrush", "메테리얼"]
velog_slug: Zbrush-MatCap-VS-Standard-메테리얼-차이
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d082511c9c3c6d4e.png)

## 📗 Standard Material과 MatCap의 차이점1

> 우선 Property에 있는 옵션이 다른 것을 알 수 있다. 

### Standard Material은 
Ambient, Diffuse, Specular, Noise, Metallic 기타등등,,
PBR 기반의 Material 세팅 옵션들이 들어가 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6c9beecff4cb391e.png)


### MatCap Material은

Material 옵션이 비교적 간단하다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c34ab7f40e4574f9.png)
사진과 같이 아래 있는 이미지를 MatCap이미지라고 하는데
이것을 기반으로 오브젝트를 그려주는 것이다. 

## 📗 Standard Material과 MatCap의 차이점2
> Light 차이점

### Standard Material은 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8cb56c7446943600.png)
상단에 Light방향을 바꿔주면
오브젝트의 Light방향이 실시간으로 변경되는것을 확인할 수 있다. 
*이때 라이트의 노란점을 한 번 더 클릭하면 방향이 뒤집힌다._"역광표현", 다시 클릭하면 앞으로 넘어온다.._ 

### MatCap Material은


Light의 방향을 바꿔도 영향을 받지 않는다. 
MapCap 이미지가 그대로 그려지게 되는 것이기 때문에 라이트가 변경되지 않는다. 
