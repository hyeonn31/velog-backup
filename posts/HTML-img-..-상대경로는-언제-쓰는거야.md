---
title: "[HTML] <img> ../ 상대경로는 언제 쓰는거야?"
date: 2024-03-22T07:39:57.658Z
tags: ["html", "경로"]
velog_slug: HTML-img-..-상대경로는-언제-쓰는거야
---
midia폴더에 있는 이미지를 쓰고 싶은데 현재 html이 폴더 안에 들어가 있다면 우리 폴더의 위쪽 폴더에 들어있다고 알려줘야 한다. 
즉 ./는 현재 내가 있는 폴더에 추가로 . 을 붙여 상단에 있는 폴더를 가리켜 주는 것이다. 
**./**(지금 내가 있는 폴더) + **(점하나 더) **= **../**(상단 폴더)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6d2d9496558183ba.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/70edd85ca592e646.png)

../ : 현재 위치의 상단 폴더 

../은 상단폴더를 의미(상위 디렉터리)