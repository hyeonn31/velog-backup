---
title: "[3ds max] 바이메쉬네임과 맥스에서 파츠분리 후 베이킹 하는 방법"
date: 2024-06-22T04:53:42.196Z
tags: ["3ds Max", "substance painter", "바이메쉬", "베이킹"]
velog_slug: 3ds-max-바이메쉬네임과-맥스에서-파츠분리-후-베이킹-하는-방법
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/35a8c999b13a8f12.png)

작업을 하면서 이런식으로 오브젝트가 묻어나오는 경우가 많아서 해결 방법을 정리해보았다.
매우 중요한 부분이다!!
크게 2가지 이다. 

#### 첫번째 방법은 Match - By Mesh Name을 활용하는 방법이다. 
이 방법은 오브젝트 개별로 이름을 통일해서 묻어남을 방지해주는 방법이다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/000f70c2dfc4a4a1.png)
해골을 클릭했을 때 오브젝트 이름 확인 -> [sk_low]로 변경
>### 중요 _low를 붙이는 이유 :
아래 사진인 substance painter에 들어가서 베이킹 메뉴에 보면
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/66a927890e03ee24.png)
_high, _low가 있다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fa3ae4cd9b722e55.png)
여기서  By Mesh Name 을 사용하려면 뒤에 하이폴은 _high를 붙여줘야하고, 
로우폴은 _low를 붙여줘야 계산을 해서 맵을 뽑아준다.

<br>

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/498d16f7969786b6.png)

마찬가지로 하이폴 해골을 클릭 후 이름을 [sk_high]로 변경해준다. 


>링부분도 이름을 변경해준다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/13e52b1f6b0c7b16.png)
로우폴 링부분 : [t_low]
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/61cc005c0ae927d7.png)
하이폴 링부분 : [t_high]


이렇게 해주면 준비끝!

로우폴은 로우폴끼리, 하이폴은 하이폴끼리 선택해서 export selected를 해준다. (fbx)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d92d66e3a94c1399.png)

-------------
<br>
다시 섭페로 와서

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/340a6b65f7fc04f1.png)
로우폴을 불러온 모습

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/530a85cc2c035ab9.png)
Bake mesh Maps클릭 - > nomal 맵만 클릭(잘 작동하는지 확인을 위해) -> 하이폴 불러오기 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5c629cdbfc371317.png)

Match -> By Mesh Name으로 변경

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3783ba8ca5125e83.png)
그러면 아까와 같은 오류가 사라지고 깔끔하게 뽑힌 모습을 볼 수 있다. 


----------------
#### 두번째 방법은 맥스나 기타 사용하는 3D 프로그램에서 객체끼리 분리를 해서 뽑는 방법이 있다. 
첫번째 방법에서 이름을 통일하기가 귀찮다 라고 하면


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d7007cb6ba105192.png)
겹쳐지는 부분 (즉 분리되어야 하는 부분을)을 하이폴이랑 로우폴 같이 잡고 간격을 벌려준다. 

이 때 주의할 점은 후에 다시 원점으로 돌려줘야 하는데 기준점이 영점으로 안잡혀있으면 나중에 되돌리기 힘들다. 

그래서 이 작업을 하기 전에 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0eb1e6d9d9cebcc7.png)
오브젝트를 영점으로 맞춰주고 시작해야한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4c475dcfb78b56f9.png)

(맥스 : move 우클릭하면 위치값 나옴.)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/acd7a5d0434084f0.png)
하이라키 클릭 -> Affect Pivot Only 클릭-> 모든 좌표 0으로 수정
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3b7f54900788af93.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b3b35454e27ee12b.png)


이제 끄고 다시 분리를 해준다. 

이때 ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/39cee2a2338754e2.png)
하이폴 따로 로우폴 따로 움직여주면 절대 안된다. 
노말맵을 추출할 땐 하이폴과 로우폴 위치가 정확하게 일치해야 가져올 수 있다. 

그래서 같이 잡고 이동시킨다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1a62102a96f02693.png)

로우폴은 로우폴대로 저장(로우폴 링, 해골), 하이폴은 하이폴끼리 저장해준다(하이폴 링, 해골). (이름 통일 필요없음)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/30ab2e9f8bf1afec.png)

그리고 섭페에 로우폴을 불러온다. 
하이폴도 불러와보자
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/730d188f94372c9e.png)
이때는 match를 Always로 추출한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ce90cc0aafcc5de7.png)

묻어나는 곳 없이 깔끔하게 뽑힌 모습


------------
그런데 여기서 문제없이 뽑은건 좋은데,,,
채색 작업을 하려면 원래 위치에서 하는게 좋잖아요
그래서 원래 위치로 바꿔치기 하는 법에 대해 알아보자.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f0c47e6f50452852.png)
아까 불러온 0점 잡아놓았던 맥스를 다시 켜주고
이동했던 링을 다시 0으로 잡아준다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bf59b4d4f2f93731.png)
이 상태에서 로우폴만 다시 저장한다. 

그다음 바꿔치기를 하려면 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1080214453072e77.png)

Edit - project configuration 클릭 - > select에서 다시 저장한 로우폴 불러오기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/98b6b118652b66c1.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2713366bc7558301.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a598a193d32d0d12.png)
그러면 조립이 된 상태로 다시 불러와진다. 

