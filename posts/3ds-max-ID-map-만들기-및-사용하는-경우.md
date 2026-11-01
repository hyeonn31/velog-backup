---
title: "[3ds max] Substance painter - ID map 만들기  원하는 부분만 마테리얼 적용하기"
date: 2024-06-22T06:07:10.999Z
tags: ["3ds Max", "Map", "id", "substance painter"]
velog_slug: 3ds-max-ID-map-만들기-및-사용하는-경우
---
보통 ID맵은 섭페에서 전체가 아닌 오브젝트 일부분에 마테리얼을 적용하고 싶을 때 사용한다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d27a5d496ff8e56c.png)
vetexpaint 클릭

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8c24c36176fb0967.png)
그럼 이렇게 창이 생성됨
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e6165d5faefbaef2.png)
기본으로 체크되어있는 것에 대해 설명하자면
페인트는 안보이고 고유의 기본 쉐이더로 보인다는 것이다. 

이녀석이 켜있으면 vetexpaint가 안보인다. 
그래서 두번째 블록 클릭 (색과 쉐이더 보이게)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/64bd1fac384b37b1.png)
첫번째 블럭은 두번째와 같지만 쉐이더가 빠진 상태이고 싶을 때 (색만 보이게)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f33050e967d34f02.png)
그래서 이렇게 파츠를 선택해주고 색깔을 지정해서 paint All을 사용해서 전체 색을 입혀준다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6aa10d3dc4af6c63.png)
그다음 editable poly클릭

fbx저장

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0d90aab0a2134844.png)
섭페에 불러온 후 베이킹에서 id 클릭
id창 더블클릭하면 창이 변경됨 -> 여기서 color source를  vertex color로 변경

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c8af404c24a7d836.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/cd161843f8e02da8.png)

Bake selected textures클릭해서 id맵 뽑기

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/893b6d0deff8cb1e.png)
짜잔

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/122b0db36e3cd1ae.png)
제질 레이어에 적용
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c86c71ca34492466.png)
Add mask with color selection 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/27c5adb08c5277ba.png)
pick color 클릭

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2e1f8b429b31474e.png)
원하는 부분 클릭해보자
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f760a8ccc796633a.png)
짜잔 

그 부분만 적용된 모습이다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/73a848e252064477.png)
이렇게 사용할 수 있다. 

## 주의할 점
하이폴리곤이 있을 경우 하이폴에 Vertex Paint를 입혀야 한다. 


안바뀔 땐
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f29aa247de08b37b.png)
꾹 눌러서
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2f2fb7bf4ddc38f0.png)
네번째 아이콘으로 변경 후 숫자 변경. 
그 후 다시 첫번째 아이콘으로 변경



-----------
<br>

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d1c31546434e0f09.png)
### 포토샵으로 하는 방법도 있다. 
맥스에서 마테리얼을 따로 따로 적용시킨 후 fbx로 저장

그 후 아까와 마찬가지로 bake mash maps들어가서 id체크 후 id클릭해서
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3ce37a2e67febf82.png)
마테리얼 컬러로 클릭

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/105bcbbed24ab89a.png)
다시 common 클릭해서 사이즈2048로 변경 -> bake all


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/08ec6e5eeea3eb62.png)
마테리얼이 따로 따로 들어온 모습
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/83650d4f5eb72976.png)
하나하나 클릭해보면 ID컬러가 다른것을 확인할 수 있다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f783d64938ee9eec.png)
자 그럼 다시 맥스에서 uv를 켜보자. 

이 상태를 2D맵으로 추출해야 한다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ef4c32f45e6c7b79.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/cbb00bada58cb5cb.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ad6c81ba25e03b77.png)


포토샵으로 불러오기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0b1d1b958e422345.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7ecfd8ab49e3642d.png)
자물쇠 부분 클릭해서 일반 레이어로 변경해주기

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1cd0ac22536de17b.png)
블렌딩 모드 - > difference로 변경

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/38d4401d4e1478a7.png)
뭐 일단 대충 이런식으로 색 넣어주기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/31899f9734bba97f.png)
배경색 깔아주고 png 저장
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6ff7505bf4c0e7f2.png)

섭페로 돌아와서 file - import resources클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/70d8d69c891fcfa5.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d5d21cc83a3541d4.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f024f4ef68843fe9.png)
하지만 import가 비활성화 되어있다. 
즉 지정을 해줘야 한다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6b676d0517f54cc3.png)
texture선택

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/71d34a3fa0fa1f0b.png)
하단에 import your resourfes to:부분 클릭
> current session : 켜져있는 동안에만 리소스가 적용되어있는 상태로 
project 'Untitled' : 맵출하고 작업했던 공간에 추가로 해서 사용
library 'your_essets' : 내가 사용하는 essets라이브러리에 저장

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fa6718aa502450da.png)
우리는 첫번째 current session을 선택해보자
import버튼이 활성화 된 모습이다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9355926254d7ebd6.png)

그럼 만들어놓은 ID 맵이 texture창에서 보인다


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/aa1bf8c90ec3c58e.png)

끌어서 Select id map에 드래그 해서 넣어준다.


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/877dc840373ecf3c.png)
아까와 똑같이 적용 가능하다. 


------

+ 
실은 이렇게 간단한 부분의경우 ID맵을 사용하는 것보다 섭페에 기능이 있다. 이것을 활용해도 된다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2124960e7cb2d9a2.png)
마테리얼 레이어에 입히고 , 블렉마스크 입혀준 다음 폴리곤 필 키고 전체 도형 선택한 후 클릭해주면 그부분만 들어간다..(간단하네)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/88eb55c14f55d123.png)
이렇게 같이 들어가는 경우가 생기는데 그럴땐 브러쉬로 지워주면 된다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/218d74b54f062c0d.png)
이때 이렇게 붙어있는부분이 간섭되어 같이 지워지는 경우가 생긴다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e33482fdcf2cdcab.png)

이때 브러쉬 속성이 uv로 되어있어야 다른부분을 침범하지 않는다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fc09551b978ea707.png)
이렇게 지워주면 됨