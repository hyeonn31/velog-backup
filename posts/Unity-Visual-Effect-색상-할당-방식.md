---
title: "[Unity] Visual Effect | 색상 할당 방식"
date: 2025-09-16T13:46:22.537Z
tags: ["Unity"]
velog_slug: Unity-Visual-Effect-색상-할당-방식
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/879ee0402660a661.png)

## 1. [set color] 단일컬러

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/808599e9a579571f.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c4b753131b291dd7.png)


## 2. [Set Color Random] 랜덤 방식
랜덤 방식을 사용하여 다양한 범위를 설정하는 것

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c4b753131b291dd7.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5eebbe66bf1357b5.png)

1번에서 사용한 set color를 클릭하고 유니티 inspector 창에서 Random을 PerComponent로 변경하면 블록이 랜덤을 위해 
A와 B로 변경된다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/dbd78346eb5aee9a.png)



## 3. 외부에서 색을 설정하기 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/808599e9a579571f.png)
마찬가지로  "Set Color"를 설정하고 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/57fd812a46ee2f7f.png)
블록 밖에서 Sample Gradient노드를 생성한다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f2e26b3065d43951.png)
그라디언트를 클릭해보면 기존 색띠들을 이용하거나 만들 수 있는 방식이다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6e2b633865cd9642.png)
원하는 색띠를 만들어서 set color에 할당해주면 된다. 
나는 노란색이 가장 많이 나오도록 노랑의 비중을 많이 두었다. 

그 다음에는 색의 띠에서 값을 가지고 올 땐 이 Time 값을 이용해서 샘플링이 필요하다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fe95a5099882bb3d.png)
한 번 더 블록 밖에서 Random Number노드를 생성한다. 
이때 Seed값은 아무거나 넣어줘도 상관없다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/97fae65384a5299f.png)

이런식으로 만들면 색상의 변형을 줄 수 있지만, 주 컬러가 많이 나타나게끔 할당을 할 수 있다. 

