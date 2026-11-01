---
title: "[Substance painter] fill layer에서 추가로 브러쉬 사용을 하고 싶을 땐 어떻게 해야 할까?"
date: 2024-06-20T17:27:31.041Z
tags: ["fill layer", "substance painter", "브러쉬"]
velog_slug: Substance-painter-fill-layer에서-추가로-브러쉬-사용을-하고-싶을-땐-어떻게-해야-할까
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6b8fd498fcf18fac.png)

자동차 도색을 예로 들면
새차가 나왔을 땐 도색이 안되어있다. 그 상태에서 페인트를 입히고, 그렇게 나온차가 쓰다보면 더러워 진다. 
그 더러워지는 부분을 레이어를 통해 만들어준다고 생각하면 된다. (디테일)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/862ce01e157e67a7.png)
베이스 컬러를 만들고 그 위에 또 fill layer를 만든다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5fdee8d6391c24b5.png)

이렇게 되면 밑에 색이 가려지게 된다. 

이럴땐 마스크 기능을 사용한다. 
** fill  layer 를 사용할 땐 반드시 마스크 기능을 사용한다!**
마스크 기능은 흰색 부분은 보이겠다. 검정색은 안보이게 하겠다는 기능이다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e53c2c0fcf363985.png)
### **Add black mask**를 클릭해주면

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2111e878b77b8e94.png)
만들어진 마스크는 일반레이어이다(paint layer).
현재 모두 검은 화면이다. (즉, 모두 안보이게 숨겨뒀으니, 첫번째 깔았던 빨간색 fill layer 가 보이는 것이다. ) 
그렇기 때문에 도구들이 활성화 된다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bd794b294b1af21d.png)
그리고 그려보면 짜잔. 

색 바꾸고 싶을땐 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d9b4c443a2c71215.png)
첫번째 블록인 fill layer에서 바꿔주고,
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4b41c331732549ff.png)
두번째 블록은 paint layer이기 때문에, 그림을 그릴 수 있다. 그려지는 부분이 첫번째 블록인 fill layer가 보이게 해준다. 

#### 추가로 fill layer에서 height를 사용할 땐 마스크가 걸려 있어야 한다