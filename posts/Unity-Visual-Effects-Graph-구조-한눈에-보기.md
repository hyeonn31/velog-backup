---
title: "[Unity] Visual Effects Graph 구조 한눈에 보기"
date: 2025-09-07T06:18:02.393Z
tags: ["Unity", "Visual Effects Graph"]
velog_slug: Unity-Visual-Effects-Graph-구조-한눈에-보기
---
# 🎇 Visual Effects Graph 정리


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9ae6c26c7341a79f.png)

## 1️⃣ 전체 구조 이해하기
처음에 중요한 점은 전체 구성이 어떻게 이루어져 있는지를 알아야 한다. 
그리고 각 구성마다 담당하는 역할을 이해하는 것이 필요하다. 


VFX Graph는 크게 3단계로 나눌 수 있다.

**1. Spawn** → 파티클 생성 (언제, 몇 개를 만들지?)

**2. Initialize Particle** → 파티클 초기값 설정 (속도, 수명, 크기 등 기본 속성 부여)

**3. Update / Output ** → 파티클 변화 & 렌더링 (시간에 따라 크기, 색, 방향, 투명도 변화 → 화면에 출력)

👉 중요한 점은 “무엇을 언제 초기화해야 하는지, 무엇을 매 프레임 업데이트해야 하는지” 구분하는 것.
예: 수명(Life)은 초기화 단계에서 한 번 정해지지만, 크기/색상 변화는 시간에 따라 계속 업데이트됨.

--- 
## 2️⃣ Spawn | 파티클 생성
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bca0584affb7c379.png)
이 Spawn은 파티클이 언제, 얼마나 생성되는지 결정하는 구간이다. 

생성 방식:
- **Single Burst (단발성)**: 한 번에 정해진 수만큼 생성.
- **Continuous (연속 생성)**: 일정한 주기로 계속 생성.

현재 사진으로는 연속 생성 방식을 이용하여 16개씩 생성하고 있다. 

16개씩 생성을 하면, 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2993c0bd503325f0.png)

받아주는 쪽인 Initialize Particle에서는 최대 몇 개까지 허용할 수 있게 할 것인지를 나타낸다. 

**"Capacity가 32개"** 라는 것은, 화면상에 표시할 수 있는 파티클의 최대 개수가 32개라는 뜻이다.  

> 📌정리 : 매번 16개씩 생성 → Initialize 단계에서 Capacity = 32로 설정 → 동시에 최대 32개까지만 화면에 보임.

---


## 3️⃣ Initialize Particle | 초기 속성 부여
속도와 수명을 부여하는 곳인데 파티클이 태어날 때 한 번만 설정되는 값들이다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/43a704e9ed60a538.png)

### ♦️ Bounds (경계 박스)
- GPU가 파티클이 어디 있는지 계산하기 위한 범위.
- 일반적으로 Manual 설정, Center = (0,0,0), Size = (100,100,100) 정도로 넉넉히 설정.

---

### ♦️ Set Velocity Random (Per-component) | 속도

- Set Velocity Random (Per-component) 사용 → X, Y, Z별 랜덤 속도 범위 설정.
- 예: (-0.333, 0.2, -0.333) 범위 → 각 파티클이 무작위 방향으로 퍼져나감.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f44bd28acb1cd3a8.png)


연속 생성 방식에서 가장 중요한 요소인 파티클이 계속 생성된다면, 사라져야하는 부분도 필요하다. 
그것이 바로 수명과 관련된 것 **Set Life Random (Uniform)** 이다.

---

### ♦️ Set Life Random (Uniform) | 수명
보통 수명은 범위로 준다 라고 기억해주면 된다. 

- Set Life Random (Uniform) → 파티클의 살아있는 시간.
- 예: 1 ~ 3초 → 생성된 파티클은 1~3초 후 사라짐.

⚠️ 연속 생성에서는 꼭 Life 값을 줘야 파티클이 적당히 사라지고 새로 생성됨.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7bc85fe203bd8536.png)
지금은 1초 ~ 3초 사이에 죽는다는 뜻이다. 



---

## 4️⃣ Output Particle Quad | 화면에 출력
파티클을 실제 화면에 **쿼드(사각 평면)**로 렌더링.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1bc08fb63c3f372e.png)



### ♦️ Orient: Face Camera Plane | 카메라 바라보기
- 체크 시 → 파티클이 항상 카메라를 바라봄 (Billboard 효과).
- 체크 해제 시 → 카메라 각도에 따라 납작하게 보이는 문제 발생.
👉 대부분의 경우 켜두는 게 일반적.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/99d6bf074b68823c.png)
orient를 비활성화 했을 경우

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/169549c9dbc30bef.png)
이런식으로 파티클의 납작한 부분이 보인다. 

이 파티클의 아웃풋 타입은 쿼드(플레인)타입인데, 카메라를 향하도록 설정하지 않아서 카메라 위치에 따라 납작하게 보일 수 있다. 

---

### ♦️ Set Size Over Life | 수명에 따른 크기 변화
- 파티클의 크기를 시간 흐름에 따라 그래프로 조절.
- 예:
  - 점점 커짐 → 연기, 폭발 퍼짐 효과.
  - 점점 작아짐 → 불꽃, 별빛 사라짐 효과. 
  
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bade64c9b4c9bde1.png)
예를 들어 수명이 0~1 사이를 흘러갈 때 파티클의 사이즈 변화는 어떻게 할거야? 
할 때 현재 사진에서는 점점 커지는 형태이다. 

작아지는 형태로 바꿔보자.

#### 그래프 변경하는 방법
변경을 원하는 지점에 마우스 우클릭 -> Edit Key를 클릭해서 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/74a1c0f882d01026.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/33f275af63ad12fa.png)
Value에 값입력
반대 점도 value에 0을 입력하면 이런식으로 변경된다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c8e377e3c330aad1.png)

이렇게 설정하면 초기에는 크게 보이지만 시간이 지나며 점차 작아지는 것을 확인 할 수 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a0ce3297b0c2f184.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/dddd7398845b77f0.png)
그래서 여러가지 원하는 대로 그래프를 조절해서 파티클의 수명에 따라 커졌다 작아졌다를 조절할 수 있다. 

---

### ♦️ Set Color Over Life | 수명에 따른 색상/투명도 변화
파티클이 태어나서 죽어가는 동안의 색 변화를 어떻게 할 것인가에 대한 기능이다. 

- 파티클의 색과 알파값(투명도)을 0~1 구간의 그래프로 조절.
- 예:
  - 처음엔 알파=0 → 점점 뚜렷해짐 → 색이 변함 → 다시 사라짐.
  - 불꽃: 노란색 → 붉은색 → 투명.
  - 연기: 회색 → 옅은 회색 → 사라짐.
  
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3a2899631742d88b.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8d686de135403b5f.png)

---

여기서 아래부분은 컬러에 대한 내용
윗부분은 알파 값에 대한 내용이다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3c6a836810d59c98.png)

---
예를 들어 사진과 같이 설정했다면 
처음에는 알파 값이 0에서 서서히 눈에 띄기 시작한다. 
그 값이 빨간색으로 바뀔 때 쯤에 가장 잘 보이다가 이후로는 다시 보이지 않기 시작한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e62e593bd193b267.png)


---
### ♦️ Compile

변경한 내용이 있다면 상단 메뉴바에서 Compile 눌러주기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/61410a846d6dfa8d.png)


---
## 5️⃣ 추가로 알아두면 좋은 것들

- **Update Context**: 파티클이 살아있는 동안 매 프레임마다 계산. (중력, 회전, 위치 변환 등 넣는 곳)
- **Sub Graphs**: 반복적으로 쓰는 노드 묶음을 모듈화해 재사용 가능.
- **GPU** 기반이라 **Shuriken** 파티클 시스템보다 훨씬 많은 파티클을 다룰 수 있음.



이런 과정들을 통해 파티클이 생성되며, 이때 파티클의 죽음 시 자연스러운 크기와 알파 값 등을 조절할 수 있게 된다. 

이 부분은 매우 중요한 부분이며, 비주얼의 질감을 새롭게 바꾸고 싶을 때 이를 조정하는 것은 좋은 아이디어가 될 수 있다. 

---

### 📌 정리
- Spawn → 언제/얼마나 만들까?
- Initialize → 태어날 때 속성 (위치, 속도, 수명, 크기)
- Update/Output → 살면서 바뀌는 값 (크기 변화, 색 변화, 카메라 방향)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f1d6ca1f8a94f38a.png)
**Toolbar** : compile, save 등의 패널들로 이루어짐
**Node Workspace** : VFX그래프를 편집하는 작업 공간
**Blackboard** : 프로퍼티나 변수를 저장/노출하고 사용하기 위한 공간
**VFX Control Panel** : Gameobject에 할당된 이펙트의 재생제어를 위한 패널