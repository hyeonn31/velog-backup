---
title: "[Unity] Visual Effect | 파도치는 듯한 파티클 만들기"
date: 2025-09-28T12:34:26.167Z
tags: ["Unity"]
velog_slug: Unity-Visual-Effect-파도치는-듯한-파티클-만들기
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/80b4c0ece15af83e.gif)


# 🔎 전체 구조 요약

이 그래프는 입자(Particle) 시스템을 만들고,

- Spawn → 파티클 생성

- Initialize → 기본값 (위치, 크기, 색상) 세팅
  - 색상 적용 → (랜덤 / 이미지 기반)
- Update → 시간에 따라 위치·크기 변화
  - Roation → 랜덤 회전 부여
- Output → 메쉬로 최종 표시
  - 발광효과 → 색상 보정/강조

이런 흐름으로 진행된다.

---

## 📕 Spawn System (생성 단계)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/63fb6a8120a3b454.png)

Spawn 노드 → 파티클 몇 개를 만들지 결정.

Duration : 20000 (즉, 20,000 프레임 동안 지속됨)

 **➡️ "얼마나 많은 파티클을 언제 생성할지" 설정하는 단계.**
                 
   ---
                 
## 📕 Initialize Particle (초기화 단계)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a5fd212e58430c75.png)

### ♦️ Initialize Particle

여기서 파티클이 생겼을 때의 기본 속성을 설정

- Capacity : 30000 → 파티클 최대 개수 설정
- Set Position : 시작 위치
- Set Lifetime Random : 수명을 랜덤으로 

### 📂 Ration(비율)노드

#### **1) Ratio 노드**
Ratio는 비율 값(x, y) 을 출력한다. 보통 0~1 범위의 값이다.
이 값은 어떤 영역에서의 상대 위치나 UV 비율일 가능성이 높다(예: 텍스처에서 추출한 좌표).
 
####  **2) Random Number 노드 (X용 / Y용 각각 하나씩)**
각 노드는 Min = -1, Max = 1 으로 설정되어 있다. 
따라서 출력은 -1 ~ +1 범위의 랜덤 값이다.
두 개의 Random 노드에 서로 다른 Seed(23, 34) 가 설정되어 있다. → X와 Y의 랜덤 시퀀스가 서로 다르게 나온다. 이때 Seed 값은 동일한 값이 아니면 아무 값이나 상관 없다. 

**Ratio.x / Ratio.y** 가 이 Random 노드의 입력(시드 또는 인덱스)에 연결되어 있다.
→ 같은 Ratio 값을 가진 파티클 그룹은 같은 랜덤 패턴을 갖게 된다. (즉, 공간적으로 연관된 파티클은 비슷한 랜덤 결과를 가질 수 있다.)

#### **3) Multiply 노드 (스케일링)**

Random 출력값을 → Multiply 노드로 혼합
X 쪽 Multiply의 B 값 = 2 → 출력 범위 becomes -2 ~ +2
Y 쪽 Multiply의 B 값 = 1 → 출력 범위 remains -1 ~ +1
즉, X 방향으로는 Y보다 두 배 넓게 퍼지도록 스케일을 준 것이다.

** 4) Initialize Particle → Set Position**
Multiply 결과가 Initialize Particle의 Set Position X, Y 입력으로 연결된다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3c7e3cd36119393e.png)


Z 값은 0으로 고정되어 있으니, 파티클은 XY 평면에서 랜덤하게 퍼져서 시작한다.

요약:
- pos.x = RandomX(-1..1) * 2
- pos.y = RandomY(-1..1) * 1
- pos.z = 0

#### **5) Set Lifetime Random (Per-component)**
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0c7d0b262b418a07.png)

Set Lifetime Random (Per-component) 의 A=1, B=2 설정은 수명(lifetime)을 1~2 사이의 랜덤 값으로 준다는 뜻이다.
→ 파티클 하나하나의 수명이 달라진다.

#### **6) 왜 Seed와 Ratio를 같이 쓰는가?**

Seed(23, 34)는 X/Y 랜덤 시퀀스를 서로 다르게 유지하기 위해 고정값으로 넣어둔 것.

Ratio를 Random에 연결하면, 공간(또는 텍스처)의 비율 값에 따라 랜덤 결과가 결정되므로 이미지 패턴을 따르는 분포를 만들 수 있다.
(예: 텍스처의 같은 픽셀 영역에 속하는 파티클들은 비슷한 랜덤 오프셋을 가질 수 있음)

#### **7) 실제 동작 예 (의사코드)**
```
for each particle:
  seedX = Ratio.x + 23
  rX = random_uniform(-1, 1, seed=seedX)
  pos.x = rX * 2

  seedY = Ratio.y + 34
  rY = random_uniform(-1, 1, seed=seedY)
  pos.y = rY * 1

  pos.z = 0

  lifetime = random_uniform(1, 2)
```

#### 8) 디버그 / 조절 팁

Multiply의 B 값을 바꾸면 퍼짐 정도(분산)를 바로 볼 수 있다.

Seed 값을 바꾸면 전체 패턴이 달라진다.


 **➡️ 파티클이 태어날 때 “어떤 상태”로 시작할지 정의.**

---

### 📂 색상 적용 방식 (두 가지 방법)

이 부분은 크게 두 가지 색상 세팅방법에 대해 기록하겠다. 

#### **(1) 방법1: 두 가지 색 랜덤 적용**
Random Number → Lerp (보간) → 색상 두 개 사이에서 랜덤 선택
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2875d501ab92e719.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3cf156c6cdbc0645.png)

Set Color에 연결 



**➡️ "랜덤으로 두 가지 색 중 하나를 선택"하는 구조.**


#### (2) 방법2: 이미지 텍스처 기반 색상 적용
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3751a1eabc64ebc8.png)

- Sample Texture2D → UV 좌표로 픽셀 색상을 읽어옴
- Get Attribute (position) → 파티클 위치를 가져옴


그걸 기반으로 텍스처 좌표를 매핑 → 해당 위치의 색상을 파티클 색으로 지정

**➡️ "이미지 색상 그대로 입자에 적용"하는 방식.**

즉, 파티클이 모여서 원본 이미지를 표현할 수 있음.




## 📕 Update Particle (업데이트 단계) | 랜덤한 회전값을 주는 노드
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/70fe7e266388cd81.png)

### 📂 랜덤한 회전값을 주는 노드

- Total Time (VFX) : 현재 시간(초)을 줌.

- Multiply (float) : time * 속도(스피드). 이 값이 커지면 사인이 더 빨리 돈다.
  - 위쪽 Multiply B = 0.05 (느리게)
  - 아래 Multiply B = 0.2 (좀 더 빠르게)
- Sine(float) : -1 ~ +1 범위의 진동값을 만듦.
- Remap(float) : 사인의 -1..1을 원하는 범위로 바꿔줌. (Clamp 체크되어 있음)
  - 위쪽 Remap → 1 .. 2 (크게 흔들림)
  - 아래쪽 Remap → 0.05 .. 0.1 (작은 값, 보통 주파수/스케일 용)

이 결과들이 Update Particle의 Turbulence(필드) 입력에 연결됨.



**➡️ 파티클이 그냥 정지하지 않고 “살아 움직이는 것처럼” 보이게 만듦.**




## 📕 Output Particle (출력 단계)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/75878b341abaaf87.png)

### 📂 발광효과노드
**➡️ 파티클의 최종 색상, 특히 발광(Emissive) 색상과 강도를 계산하는 로직임.
이 계산 결과는 우측 Output Particle HDRP Lit Mesh 블록의 Emissive Color 입력에 연결**

- 파티클의 기본 색상을 가져와 (Get Attribute: color)
- 일정한 계수(0.91)로 밝기를 조정한 다음,
- 파티클의 생명주기에 따라 변하는 밝기/투명도(Sample Gradient)와 통합하여,
- **발광 색상 (Emissive Color)**으로 출력한다. (Vector4에는 색상과 알파 정보가 모두 포함됨)

### ♦️ Output Particle HDRP Lit Mesh
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/80f998e910ff8902.png)

이 설정은 HDRP를 사용하여 원통(Cylinder) 형태의 파티클을 렌더링하며, 이 파티클은 카메라를 바라보고(Face Camera Plane), **속도 방향으로 정렬(Along Velocity)**된다.
파티클의 크기는 생명주기 동안 변화하며 전체적으로 작게 조정했다.
또한, 왼쪽 노드 그래프의 계산 결과에 따라 파티클은 **발광 효과(Emissive Color)**를 가지며, 그 밝기는 파티클마다 다르며 생명주기에 따라 변화한다.


---


# 🎬 정리

- Spawn → 파티클 생성

- Initialize → 기본값 (위치, 크기, 색상) 세팅
  - 색상 적용 → (랜덤 / 이미지 기반)
- Update → 시간에 따라 위치·크기 변화
  - Roation → 랜덤 회전 부여
- Output → 메쉬로 최종 표시
  - 발광효과 → 색상 보정/강조


즉, 이 그래프는
👉 이미지 색상을 기반으로 파티클을 배치하고, 랜덤 회전과 색상 변화를 주면서 업데이트되다가 최종적으로 메쉬 파티클로 출력되는 구조이다.

