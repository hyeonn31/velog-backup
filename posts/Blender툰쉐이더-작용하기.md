---
title: "[Blender] 툰쉐이더 적용하기"
date: 2025-10-17T01:30:17.503Z
tags: ["blender"]
velog_slug: Blender툰쉐이더-작용하기
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e7f048cff47cd1cf.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2c3c22219ee270e4.png)
## 1. 툰쉐이더 적용
선택된 부분이 툰쉐이더 적용한 방법이고
 
 ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d0dbc94d38db1a9c.png)
 ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f6b97b08eef8e98c.png)

이때 이 multiply는 mix로 검색한 뒤 아래창에서 multiply로 변경해야한다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4c1d2d80aec282ad.png)
그 후 texture paint 이미지를 mix에 연결한다.


---

## 2. 아웃라인 생성
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e65c1306496c0ade.png)
카툰풍에서는 그림 느낌을 살리기 위해 아웃라인을 생성해주는 것이 좋다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3e337dd1450aac1f.png)
우선 툰쉐이더 밑에 머테리얼을 하나 생성한 뒤 surface를 Emission으로 바꾼다.
색상은 원하는컬러로 변경한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a1e938351305bcaa.png)
Settings에서 backface culling - camera 체크
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bb81f3b6c81dfef5.png)
그 후 도구창에서 solidify를 선택한다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/59944bc5594f8f66.png)
mode 는 simple로 변경해주고
thickness를 알맞게 조절한다.(너무 두껍지 않게)
normals의 flip을  눌러 뒤집어주고 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4999a69e3ccb74ef.png)
머테리얼의 offset을 두번째가 아웃라인 메테리얼이었으니 1로 변경한다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/31e015ee58684321.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3ef1398e306be819.png)


