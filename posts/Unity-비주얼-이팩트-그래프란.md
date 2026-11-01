---
title: "[Unity] 비주얼 이팩트 그래프란"
date: 2025-08-25T13:42:28.631Z
tags: ["Unity"]
velog_slug: Unity-비주얼-이팩트-그래프란
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0a6bfaa4d20e4e6c.png)

# 🎇 비주얼 이펙트 그래프(VFX Graph)란?

게임이나 영화에서 불꽃, 폭발, 연기, 마법 같은 특수 효과를 만들 때 사용하는 유니티(Unity)의 기능이다.



---

### 🧩 어떻게 쓰는 걸까?

하나 or 여럿의 파티클 시스템을 만들 수 있다 → 작은 점, 불꽃 조각, 빛 알갱이 같은 것들

거기에 **메쉬(3D 모델)**를 입히거나 **쉐이더(빛/재질 효과)**를 추가해서 더 멋지게 만들 수 있다.

단순히 눈에 보이게만 만드는 게 아니라,
C# 스크립트(코드)나 Timeline(애니메이션 시퀀스 도구)와 연결해서
"특정 타이밍에 폭발!", "캐릭터가 공격할 때 마법 효과!" 같은 이벤트도 줄 수 있다.

### 📦 SubGraph (서브그래프)
> SubGragh: 자주 사용되는 vfx 그래프나 노드는 SubGraph를 통해 라이브러리화하여 사용 가능

자주 쓰는 효과를 매번 새로 만들면 번거롭다
그래서 SubGraph라는 기능으로 "효과 조각"을 저장해두고, 필요할 때 불러와서 사용할 수 있다.
예를 들어 "불꽃 기본"이나 "연기 기본" 같은 걸 만들어 놓고 재활용하는 것을 말함.



### 🎨 파이프라인과 호환성

**1. URP (Universal Render Pipeline)** → 보통 모바일, 일반 PC 게임에서 씀

**2. HDRP (High Definition Render Pipeline) **→ 고화질, 리얼한 그래픽용 (하이엔드 PC/콘솔)

두 가지 모두에서 VFX Graph를 사용할 수 있다.

출력 방식도 빛 반사되는(Lit), 빛 반사 없는(Unlit), 2D 게임용 등 다양하게 지원한다.

🕒 Unity 2019.1 버전부터 사용가능


## 👉 한마디로 정리하면:
"VFX Graph는 유니티에서 불, 연기, 마법 같은 화려한 특수 효과를 시각적으로 쉽게 만들고, 코드나 애니메이션 타이밍에 맞춰 제어할 수 있는 도구" 라고 보면 된다.

**입자효과** = 작은 점들을 모아서 자연 현상(불, 연기, 눈 등)을 흉내내는 것
**VFX 그래프** = 그 입자들을 만드는 마법 도구

---

### 📌 Particle System vs VFX Graph

 **Particle System** : 유니티에서 오래전부터 있던 기본 입자 효과 시스템

**VFX Graph** : 새로 나온, 더 강력한 입자 효과 시스템 (GPU 사용)


### 📌 CPU vs GPU 차이 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/cc97546f002b6f91.png)


- **Particle System은 CPU**에서 계산됨 → 처리량이 **적음**

  -		입자 개수: 수천 개 (Thousands) 정도
  - 	시뮬레이션: 단순(Simple)

  - 	물리: 기본 물리 시스템 사용

  -		게임플레이와 상호작용: 가능(Yes)

- **VFX Graph는 GPU**에서 계산됨 → 훨씬 많은 입자를 빠르게 처리 가능

  -		입자 개수: 수백만 개 (Millions) 가능

  -		시뮬레이션: 복잡(Complex)

  -		장면 표현: 더 다양한 방식 지원 (구체, 박스, Signed Distance Field 등)

  -		게임플레이와 직접 연결은 제한적 (Depth buffer는 읽을 수 있지만, 물리 같은 부분은 약함)

### 결론

- **Particle System** → 가볍고 단순한 효과 (불꽃놀이, 간단한 불, 연기 등)

- **VFX Graph** → 수많은 입자가 필요한 멋진 효과 (마법, 폭발, 수천 개의 불꽃, 대규모 연기 등)

👉 "기존 Particle System은 CPU 기반이라 단순하고 입자가 적지만, VFX Graph는 GPU 기반이라 수백만 개 입자를 처리하며 훨씬 복잡하고 화려한 효과를 만들 수 있다" 