---
title: "[Substance Painter] Bake mash Maps 종류는 뭐가 있을까?"
date: 2024-06-20T16:37:15.137Z
tags: ["Baking", "back mash maps", "substance painter"]
velog_slug: Substance-Painter-Bake-mash-Maps-종류는-뭐가-있을까
---
처음에 substance painter를 열게 되면 3ds max에서 작업한 하이폴과 로우폴을 가져와야 한다. 그때 기본적으로 가져올 맵들의 종류에 대해 간단히 알아보자.


> ##  1. Normal
> >하이폴리곤의 정보를 가진 맵
Zbrush에서 작업한 모델링 데이터를 High Mesh라고 함.
Normal은 반드시 베이킹 해야함
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3ef92ba4c18a6f2d.png)
면이 뻗어나가는 백터 방향을 개선해서 뽑아주는 탄젠트 노말이라고 보면된다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/94ea49244753260f.png)
이런식으로?



> ## 2. World space normal
오브젝트 공간의 데이터를 가진 맵
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/71129d5ac7b62c6a.png)
전체 공간을 계산해서 뽑아주는 normal

>## 3. ID Map 
모델링의 좌표에 컬러 정보를 가지고 있는 맵
가장 중요한 맵 중 1개
영역을 나눌 때 주로 사용


> ## 4. Ambient occlusion
빛과 그림자 정보를 가진 맵
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/22d631cbc16e69b7.png)
간단히 말해서 그림자 맵

>## 5. Curvalture
나오고 들어옴 정보를 가진 곡률맵
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2b54360abee21ca5.png)
 디테일 맵
>> 가장 중요한 맵중 1개
텍스트의 퀄리티를 좌지우지함
잘 나올수록 좋다.
 
 > ## 6. Position
 바닥하고의 거리 정보를 가진 맵(Y축)
 ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3c6b13a25c87dd07.png)
위치에 대한 맵

>## 7. Thickness 
얇은 부분, 두꺼운 영역을 표현한 맵
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ba737f4408fc702f.png)
두깨에 관한 맵

이러한 맵들이 뽑혀져 있어야 다른 기능들과 효과들이 제대로 들어가게 된다. 





