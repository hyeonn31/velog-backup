---
title: "[Zbrush] 쿠션효과2 내부편(모델링에 질감 넣기)"
date: 2024-08-16T11:50:02.910Z
tags: ["Zbrush", "노이즈 플러그", "질감"]
velog_slug: Zbrush-쿠션효과2-내부편모델링에-질감-넣기
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/dd99baa4270602e1.png)

모델링에 질감을 넣고싶다면 폴리곤 수가 어느정도 높아야 한다.
그래야 그림이 잘 찍히기 때문.

### 디바이드를 어느정도 높였다면
### 서페이스 - 노이즈
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c93867b4a4e40d31.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d7edbeeedff9bd91.png)

그럼 이렇게 우리가 꺼내놓은 모델링의 이미지가 보이는 창이 뜬다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6668beb0e6222c8f.png)

확대해보면 표면이 보이는데 기본적인 질감이다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/35aeb05953fc0b22.png)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e8c0a6d186d5ac57.png)
노이즈 플러그 메뉴를 클릭하면 노이즈에 관련된 부분을 조절 할 수 있는 슬라이드가 있다.

기본적으로 제공해주는 플러그들이 있다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bf3c50e9082e8326.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/aebe39909a189dd4.png)
 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7040269c30bc0ee5.png)

기본적으로 제공해주는 플러그들은 플러그인 크기와 노이즈세기 두개를 조절해서 사용해주고, 노이즈 크기와 기본 노이즈 믹스는 0 상태로 만들어 준다. 
(노이즈 세기 -는 들어가게, +는 나오게 표현된다.)

+부분 예시
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/44795d1ba0c24324.png)

-부분 예시
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7511b078f2055145.png)


여기서 다른 무늬를 원한다면 노이즈 플러그가 켜져있는 상태에서 에디트를 누르면 기본 제공 플러그들을 보여주는 창이 다시 뜬다.

원하는 노이즈를 만들었으면 실제로 적용시켜줘야 한다. (현재는 가상의 적용)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b46c524f2b3514a9.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c5c4a14742f346c4.png)
자. 이제 이 질감을 예시로 적용해보겠다.

### 첫번째 방법은 노이즈 마스킹
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/580d9def61691630.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/cef9c8ece5d23076.png)
노이즈 마스킹을 클릭하면 이렇게 입힌 질감대로 마스킹이 씌워진다. 
이 상태에서 Move브러쉬로 바꾸어서 art+드래그 
튀어나오게 또는 들어가게 만들어준다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/aafe288370ab50f8.png)
이런식으로
이렇게 해주면 원하는대로 또렷하게 적용 가능하다.
### Ctrl + H 를 눌러서 마스킹 부분을 숨길 수 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5128caea69dde54a.png)

이 방법을 사용하면 내가 더 강조하고 싶은 부분을 더 강하게 넣을 수 있다.
또한 외곽 형태도 많이 안변하게 할 수 있다. 	

-----
전체적으로 한번에 하고 싶다면
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9cef47f58a4eda95.png)

마스킹 되어 있는 상태에서 디포메이션 - 인플레이트 조절

----
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ba7536883f6287f5.png)

두번째 방법은 메쉬에 적용 버튼을 클릭하여 실제 모델링에 적용시킨다. 하지만 이 부분은 팽창하여 그래픽이 적용되기 때문에 원하는 질감과 달라지게 표현될 수 있다. 그래서 거의 사용을 권하지 않는다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9bd968e8a3f5b44d.png)
강도가 전과 비교해 달라진 모습이 보인다. 오브젝트의 외곽도 살짝 부풀어진다. 

메쉬에 적용은 기본 모델링이 팽창하면서 마스크에 적용되기 때문이다.

---
### 자 이번엔 내가 원하는 질감을 넣고 싶을 때

우선 텍스쳐를 찾아야 한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/13d4ee24fcd4aab7.png)
이런식으로 검색해주면 여러 텍스쳐가 뜬다 .
원하는 텍스처를 찾았다면 JPG로 저장해주기 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b0c013b6b302b156.png)
Alpha On/Off 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/84f6b25efac68d80.png)
이미지 선택
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a3c2efdb95af7543.png)
조절,,, 
앟 
### 이게 아닌데 싶다. (실패요인)
이렇게 되는 이유는 노이즈라는 것이
정면에서 때려 박는 듯이 입혀지기 때문이다.

--------
### 다시 해보자.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fce1c0df418b2655.png)
1. z리메셔를 활용하여 폴리곤수를 uv하기 좋은 사이즈로 줄인다
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c235bb45ddd7373f.png)
2. z플러그인 - UV마스터 - 클론으로 작업을 클릭
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/94af15d84b454fd5.png)
서브툴에 CL_가 붙은 클론이 생성된 것을 알 수 있다. 

---

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5d54d2bd15a8ed11.png)
4. Z플러그인 - FBX 내보내기/불러오기 클릭 - 내보내기
FBX로 저장

---

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0a03f225e1b7ae08.png)

5. MAX에 불러온 후 Unwrap UV 적용하기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/45e4db7a966d6fbb.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/133ce7553e66c221.png)

uv펴주기 작업을 진행한다.

----
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2a09fb6d80e3938b.png)
6. file- export - export selected

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2c65433012cd3b48.png)
7. obj로 저장
---
지브러쉬 - tool -  불러오기 - obj 불러오기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/33b01458142accb8.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/36485b3b9682be96.png)
서브툴에 불러온 오브젝트를 확인할 수 있다. 


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/201dbcff5f8c5957.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bb50f33f76845a6f.png)

원하는 위치에 다시 배치 후 - 디바이드로 폴리곤 수 높이기

--
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fcff4fd336c4a431.png)
서페이스 - 노이즈

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8c6df9f47602a334.png)
아까와 똑같이 클릭 후 사진 가져오기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b3cf8471e92c6347.png)

uv로 변경 후 노이즈 조절
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e58db30cdc9c4396.png)

노이즈 마스킹 후 move브러쉬 사용 또는 디포메이션 - 인플레이트 양감 넣기(위에 부분 참조)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0ebbbddbb9c06074.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6504fbb8ac9056ea.png)

## 짠


----

*(번외) 포토샵으로 가져가서 질감 수정을 원한다면
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c97914710447e5a0.png)

max - unwrap uvw - open uv editor에서 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5a66ddb435659c1f.png)
tools - Render UVW Template

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9ae8defff1af6d39.png)
2048 변경 후 render uv template 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1f9910453589c05e.png)

save
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ebbc1487097f4702.png)

tga파일로 저장 -> 포토샵에서 uv위에 그림 작업 후 그림 저장