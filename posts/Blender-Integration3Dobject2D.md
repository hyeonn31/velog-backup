---
title: "[Blender] Integration(3Dobject+2D)"
date: 2024-12-23T07:17:51.002Z
tags: ["blender"]
velog_slug: Blender-Integration3Dobject2D
---
📖2024-04-30

## 목표 : 
3D 오브젝트와 사진과의 통합.

## 도전과제 :
자연스러워야 한다!

### Tip:
선택한 혹은 직접 촬영한 이미지의 빛/그림자/분위기/질감 등을 분석,관찰 하여 제작한 3D오브젝트에 적용시켜본다. 

### 규칙 :  
photoshop 사용 허용하나 마무리작업 때 필요시에 제한적( 20%미만 )으로 사용해야한다.

모델링/빛/질감에 대해 공부할 수 있는 이미지를 의도적으로 선택.

제출할 렌더이미지 좌측상단에 이름 작게 넣기.( 7-8pt, 고딕체 )

### Render Settings : 

- jpeg 혹은 png, 100dpi(포토샵에서 후반 보정을 한 경우)
- 해상도: 사용한 이미지 사이즈(이미지 사이즈가 크다면 50%로 조정)
- Render Engine: Cycles
- Render : 렌더 결과이미지를 보며 Max Sample을 조정하여 결정(주의: 불필요하게 높이지 않을 것)
- Noise Threshold, Denoise 체크

#### Step 1

컨셉잡기. ( 선택사항 )

사용할 배경 이미지 찾기. 참고할 조각품 이미지 검색.

이미지에 넣을 3D 오브젝트(조각물) 제작.

#### Step 2

카메라 뷰 생성 _

방법 1. 기본 카메라에 사용할 이미지 추가하고, 3D 오브젝트를 시점, 원근법, 위치, 사이즈등등 이미지와의 관계를 고려하여 카메라 뷰 set. (영상학습자료 참고)

방법 2.https://fspy.io/ 에서 소실점(vanishing point),축(axis)등을 조정하여 추출하여 블렌더에 불러오기.  (블렌더 add-on에 설치 _https://github.com/stuffmatic/fSpy-Blender)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/eeded6dda13eb2af.png)

이미지 속의 빛/질감/분위기를 분석하여 적용 _

방법 1. 조명의 위치 속성 등을 직접 조정 (영상학습자료 참고)

방법 2.  적절한 hdri 이미지 찾아 활용해보기 ( https://polyhaven.com/ )
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/43b7e0ca7c558ebd.png)

분석한 것들을 3D 오브젝트에 적용하기. _ 조명 조절: Node를 활용.

#### Step 3

렌더 및 컴포지팅

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e78be95d7631478f.png)

#### Step 4

저장하여 필요시 (포토샵에서)후반보정. 


### 결과물

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e9c6e17edd98753c.jpg)
