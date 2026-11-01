---
title: "[ZBrush] ZBrush 모델링완성 후 3ds Max로 가져갈때 "
date: 2024-05-18T08:11:04.945Z
tags: ["Zbrush", "데시메이션 마스터"]
velog_slug: ZBrush-ZBrush-모델링완성-후-3ds-Max로-가져갈때
---


맥스로 가져가려면
면수를 많이 줄여줘야 한다.(10만~30만 단위)

***그 전에 시야 통합으로 모든 오브젝트를 하나로 합쳐주고 시작한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/762436ceb0cd459d.png)


Z플러그인 - 데시메이션 마스터
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d1094aa0741a166b.png)

선택 프리프로세싱 : 선택한 부분만 하겠다.
전체 프피프로세싱 : 모든 오브젝트를 한번에 계산

첫번째로 계산해보자.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a120f2a517f0a113.png)
이렇게 계산중

완료 되었다면
다시 z플러그인에 데시메이션 마스터에 들어가보자.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1725339481fb7cce.png)

퍼센트 되어있는 부분을 살짝 조절해보면
밑에있는 k폴리곤과 k포인트가 바뀌는 것을 볼 수 있다. 

우리는 k포인트를 본다.


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3abd179aa679097f.png)
(포인트 기준으로 보기 때문)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/de904b85e5d38402.png)
앞에 3자리면 10만단위, 4자리면 100만단위이다.

10만 단위만 필요하다. ex)30만개 정도 필요하면 300입력
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f655c0b3881287f8.png)

다시 선택 데시메이트 클릭

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/77fe6598cc15fccc.png)
90만으로 바뀐 포인트 카운트를 볼 수 있다. 
디테일을 그대로 유지가 된 상태로 만들어지게 된다. 

이것이 바로 데시메이션 기능이다. 

완료가 되었다면 이제 맥스로 보내기 위해 내보내기를 해준다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e8167eabe3565a5b.png)


Obj로 저장하기 ->

맥스에서 열기



** FBX로 내보내기 기능도 있다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e81e0b02b900cd13.png)

