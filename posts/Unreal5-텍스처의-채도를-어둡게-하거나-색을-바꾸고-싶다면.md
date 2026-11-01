---
title: "[Unreal5] 텍스처의 채도를 어둡게 하거나, 색을 바꾸고 싶다면?"
date: 2025-05-14T07:33:20.364Z
tags: ["Unreal Engine 5", "채도", "텍스쳐"]
velog_slug: Unreal5-텍스처의-채도를-어둡게-하거나-색을-바꾸고-싶다면
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/297b561e83969f67.png)

지금 사용 중인 WorldAlignedTexture 노드는 텍스처 오브젝트를 받아서 월드 기준 정렬된 텍스처를 출력하는데, 이 출력은 벡터 값 (RGB) 이라서 바로 색 정보를 사용할 수 있음.

### ✅ RGB 출력 확인 방법
WorldAlignedTexture 노드의 출력 핀
→ 이건 이미 RGB(색 정보) 를 담고 있다.
→ 이름은 따로 안 써 있지만, 이 출력은 기본적으로 Vector3 (R, G, B) 값임.

그냥 이 출력을 Base Color에 연결하면 색이 바로 반영됌

### 🎯 RGB를 조절하고 싶다면?
WorldAlignedTexture의 출력 핀을 다음과 같이 사용할 수 있다:

## ** Multiply로 색 어둡게**
WorldAlignedTexture 출력 → Multiply 노드 A

B에 (0.5, 0.5, 0.5) → 전체 색을 50% 어둡게

결과 → Base Color




------


## Tint 색 변경


Unreal에서는 Vector3 (Constant3Vector) 노드를 써서 만들 수 있음


#### 1. Constant3Vector 노드 추가
→ 값: R: 1, G: 0.5, B: 0 (주황)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6baa88039b83611d.png)



#### 2. Multiply 노드 사용
WorldAlignedTexture 출력 → Multiply의 A

Constant3Vector (주황) → Multiply의 B

Multiply 결과 → Base Color에 연결

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/0cebe5cc16582f9c.png)



### 📌 요약
WorldAlignedTexture 출력 자체가 RGB 값이야 (따로 분해 안 해도 됨)

원하는 조작은 Multiply, Desaturation, Lerp 같은 노드를 추가해서 하면 됨
