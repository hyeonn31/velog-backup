---
title: "[Unity] Visual Effect를 활용하여 3D 모델링을 이용한 모핑 효과 만들기 "
date: 2025-10-20T07:08:24.997Z
tags: ["Unity"]
velog_slug: Unity-Visual-Effect를-활용하여-3D-모델링을-이용한-모핑-효과-만들기
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3729f7fe9b912bf5.png)


# 요약
- 조명의 영향을 받지 않는  Unlit Type(빛(Light)의 영향을 받지 않는 셰이더 타입)으로 아웃풋 설정
- 연속 생성 방식
- 랜덤생성방식으로 파티클 위치를 가져오는 것은 = 포인트 캐시 데이터를 사용함.
## 📕 Initialize Particle
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e36f5206cffa72ae.png)

### Point cache
미리 계산된 점(포인트)들의 모음(데이터 파일)이다.
보통 3D 모델의 애니메이션된 정점(버텍스) 위치를 시간별로 저장한 것들이 들어있다.
> 이 박스 안 항목들:
Point Count: 포인트(점)의 총 개수.
AttributeMap : position: 각 포인트의 위치(벡터).
AttributeMap : normal: 각 포인트의 법선(표면 방향).
AttributeMap : uv: 각 포인트에 대응되는 UV 좌표(텍스처 좌표).



요약: 이 파일에서 파티클을 배치할 위치, 방향, UV를 가져온다.

우선 포인트 캐시를 굽기 위해선
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/195674b95e6bb371.png)
Window - Visual Effect - Utilites - Point Cache Bake Tool을 사용해야 한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e01842bab5f3e78f.png)
그럼 이런 창이 하나 뜨는데, 원하는 FBX 파일을 유니티에 가져온 후에 사용하면 된다. 
이때 Point Count는 컴퓨터 성능에 따라 갯수를 입력해줘야 한다. 갯수가 많을수록, 더 디테일하게 포지션을 확인 할 수 있다.  나는 우선 100만개로 진행했다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/cc074ffcc1533a64.png)
또한 Export UVs 체크하여 텍스쳐를 가져올 수 있도록 한다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9d49a65a2fb71b06.png)
로 저장

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/175bad6f02e2d51e.png)
그 다음 point cache에 투입

그 후 position값을 Set Position from Map의 Attribute Map에 연결시켜주면 된다 .
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c212408e3eb6fe5d.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/510bea5451ec4b9e.png)


---

### Initialize Particle 상단 부분 항목
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7d43087851d02396.png)

- Capacity:
  - 이 VFX 시스템에서 동시에 다룰 수 있는 최대 파티클 수.
  - 예: 500000 → 최대 50만 개까지 메모리와 성능 허용하면 생성할 수 있음.
  - 너무 크게 하면 메모리/프레임 드랍 생김.

- Bounds Mode (Recorded 등)
  - 파티클들이 어느 공간(박스) 안에 있어야 카메라에 보이는지 결정.
  - Recorded: 미리 계산된 경계 사용 등. Bounds를 잘 설정 안하면 파티클이 카메라에서 잘리지 않거나 보이지 않을 수 있음.

- Bounds / Bounds Padding
  - 파티클이 움직일 때 여분으로 허용할 크기(x,y,z).
  - 예: x 0.5 y 0.5 z 0.5 라면 경계에서 반 유닛 더 허용.
  
  ---
  
### Set Position
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e41ac24c01d5a997.png)

- Set Position 체크박스가 켜져 있으면 파티클의 기본 위치를 직접 값으로 줄 수 있다.
- 옆에 Position x y z 입력란: (0,0,0) 같은 숫자로 위치를 고정
- 보통 여기선 기본값(원점)을 두고, 아래의 Set Position from Map으로 세부 배치를 한다.


---

### Set Position from Map | 이미지의 중간 섹션
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/81b2cff1ebd943ba.png)

이 섹션은 Point Cache(또는 다른 Attribute Map) 에서 위치 데이터를 뽑아서 파티클의 시작 위치를 정하는 곳이다.

- **Sample Mode (샘플 모드)**

  - 이 드롭다운은 "Point Cache에서 어떻게 샘플(뽑기)할까?"를 정한다.
  - 예시로 보이는 Random Constant Per Particle 설명:
    - Random Constant Per Particle: 각 파티클마다 Point Cache에서 무작위 하나의 포인트를 뽑아서 그 파티클에 항상 같은 값을 사용함. (파티클이 계속 같은 위치/브이값을 유지함)

    - 다른 가능한 모드들(설정에 따라 다름):

    - Sequential: 포인트를 순서대로 하나씩 사용.

    - Random Per Frame: 매 프레임마다 무작위로 다시 샘플.

    - Direct Index: 인덱스(숫자)로 특정 포인트를 지정.

요약: 대부분 "각 파티클에 고정된 랜덤 포인트를 할당"하려면 Random Constant Per Particle을 사용해.

- **Attribute Map (어트리뷰트 맵)**

  - 드롭다운에서 어떤 어트리뷰트를 쓸지 고른다.

  - 여기선 position이 선택되어 있어 → Point Cache의 위치 데이터를 사용하겠다는 뜻.

  - 선택 가능한 것들: position, normal, uv 등. (Point Cache에 저장된 항목들 중에서)

  - 예: uv 선택하면 텍스처 좌표(0~1 범위)를 뽑아올 수 있음.

- **Seed (시드)**

  - 랜덤을 제어하는 숫자. 같은 시드값이면 랜덤 결과가 재현됨(같은 패턴).

  - 예: Seed = 0 과 Seed = 123 은 다른 배치. 디버깅할 때 바꿔보면 유용.

- **Value Bias (값 바이어스)**

  - 샘플한 값에 더해지는(shift) 값. (벡터의 각 축별로 더함)

  - 예: position의 값에 Value Bias x=1 y=0 z=0 넣으면, 모든 샘플 위치가 x축으로 +1 이동함.

- **Value Scale (값 스케일)**
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/878d502a1f7b7fc3.png)

  - 샘플한 값에 곱하는(scale) 값. (벡터의 각 축별 배율)

  - 예: position의 Value Scale x=2 y=2 z=2 넣으면, 샘플 위치들이 2배 커짐(원점에서 더 멀어짐).
  이를 통해 모델링이 잘 보이는 구간을 직접 값을 바꿔가며 찾아줘야 한다. 

정리: 실제 파티클 시작 위치 = (샘플된 position) * ValueScale + ValueBias

---

### Set Direction from Map (파티클 방향 설정)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d89ee65cfc2000b7.png)

이 섹션은 파티클의 초기 방향(벡터) 을 어트리뷰트에서 가져오는 곳이다.

- 항목 구조는 Set Position from Map과 거의 동일:

  - Sample Mode: Random Constant Per Particle 등. 각 파티클에 대해 방향을 어떻게 샘플할지 정함.

  - Attribute Map: 여기선 uv가 선택되어 보임(이미지 기준). 즉 UV 값을 그 파티클의 방향(또는 어떤 속성)으로 사용하겠다는 뜻.

  - Seed / Value Bias / Value Scale: 위치와 같은 방식으로 동작.

- 주의: uv는 보통 (0..1, 0..1) 범위라서 방향으로 쓰려면 Value Scale로 -1..1 범위로 변환하거나, Multiply/Add로 보정해야 한다.

  - 예: uv * 2 - 1 → uv(0~1)을 (-1~1) 범위로 바꿔 방향 벡터처럼 사용 가능.
  
  ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/640b4ba5198e589f.png)
포인트캐시의 uv를 연결한다. 

 
 
 ---
  
### Modeling Size
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1d6dfa3ebbf50682.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2d339fd294086158.png)

Modeling Size라는 Exposed Parameter(인스펙터에서 조절 가능한 값)가 Value Scale 또는 다른 입력과 연결되어 있다.

이 값은 파티클의 크기 조정이나 샘플 위치의 스케일로 사용될 수 있다.

예: Modeling Size현재 10 = 5로 변경 → ValueScale에 연결되면 전반적으로 파티클 분포 범위가 절반으로 줄어듦.

---

## 📕 Output Particle Quad

### Orient:Face Camera Position(Orientation)
모델링을 돌리면 안보이는 구간이 생긴다. 그 이유는 구성하고 있는 파티클이 쿼드이기 때문이다. (대량의 파티클의 경우 메쉬로 구성되어있으면 과부하가 크다.)
쿼드는 플레인 형태인데, 카메라와 수직으로 위치하게 되면 안 보이게 된다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b3fcd79c04a38077.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2101713f1189e302.png)
을 적용하면 항상 카메라를 쳐다보는 플레인 형태의 파티클로 할당된다. 

### Multiply Size
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/81138fe30f64f0b9.png)
파티클 입자 크기를 조절할 수 있다. 



---

## 📕 Update Particle
비주얼 이펙트 그래프는 자체적으로 UV데이터가 없어서 
아까 포인트캐시를 만들 때 UV를 체크했었다. 그것을 활용할 것이다. 

현재 나는 유니티 21.3.9f1 버전을 사용하고 있는데, 이 버전에서는 맵으로부터 UV를 가져오는 노드가 없다. 이유는 정확히 모르겠다. 
### FBX UV 텍스쳐(음영) 가져오기
 밖에 get attribute: direction와 Sample Texture2D를 생성한다. 
  ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bf704bfff9211ddb.png)
   
   ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ca5dd524bb89fb17.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/07aa597677576350.png)
그 다음 texture를 클릭하여 해당 fbx의 uv텍스쳐를 찾아 선택한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7dd662b27b437308.png)
x,y 연결한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/caac490df12b05e3.png)
Update Particle 박스 안에 set color를 생성하여 연결해준다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2d72dd33da7aaa6e.png)
이때 파티클이 너무 어둡거나 밝다면 Multiply를 사용하면 밝기를 조절 할 수 있다. 

---

### 다른 텍스쳐(컬러) 추가하기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a5996741f60fe303.png)
만든 노드를 복사 붙여넣기 한 후
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a7589f26b5bda6d1.png)
원하는 이미지로 변경한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5e88fcdf9505b3ff.png)
Lerp노드를 추가하여 x,y에 연결해준다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f068ff15f68f9f83.png)
float 노드를 추가하여 오른쪽 마우스 - Convert to Property를 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f2ddea14cc91e266.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f6cd35e044aea292.png)
Lerp s에 연결
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fb34424edb61966a.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fa1c04717d517a8f.png)
Backboard에서 float이름을 AnimationValue로 변경하고, 노출되도록 Exposed를 체크한다. 
그 다음 레인지를 0에서 1사이로 조정하면 외부인스펙터에서 쉽게 컨트롤할 수 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/bbf326b8d480a201.png)

이 컬러 맵 텍스쳐의 맵핑이 더 오밀조밀하면 좋겠다고 생각한다면 x와 y에 일정한 값을 곱하고 더해 타일링할 수 있다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/209c75249520f8c2.png)

---

### + 입힌 컬러 텍스쳐에 음영감 넣기
애니메이션 밸류가 0이 됐을 때 위에 있는 음영 텍스처가 적용된다. 그리고 애니메이션 밸류가 1이 됐을 때 아래에 있는 컬러 텍스쳐가 적용되는 것인데 이때 문제점은 컬러텍스쳐 부분에서는 2D 처럼 음영 값이 잘 보이지 않게 된다. 

즉 단순히 컬러 텍스쳐만 추가하게 되면 컬러가 반영될 땐 음영 데이터가 보이지 않게 된다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/49ce5baa520ccc47.png)
이를 보완하기 위해 처음에 만들었던 FBX UV 텍스쳐(음영)을 한번 더 복사 붙여넣기 한다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/443e797a9da2d673.png)
컬러텍스쳐 추가한 노드에 방금 복붙한 음영 노드를 multiply로 곱해준 후 다시 Lerp에 연결한다.


# 📘 완성된  Visual Effect Graph



![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/05300dc780445cab.png)


이번에 다루는 방식을 잘 알아두면 나중에 모델링 디자인을 마친 후 나만의 아트워크를 만들어 다양하게 만들 수 있다는 장점이 될 수 있기 때문에 유용하다. 