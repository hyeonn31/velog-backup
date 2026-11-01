---
title: "[Unity 3D/VR] XR Interaction Toolkit "
date: 2024-12-27T07:18:38.181Z
tags: ["Unity", "xr", "개발", "게임"]
velog_slug: Unity-3DVR-XR-Interaction-Toolkit-BACTERIAL-LASER-프로젝트
---
XR Interaction Toolkit을 활용한 게임 제작 프로젝트를 진행하였다. 
# 개요
**XR Interaction Toolkit은 Unity에서 제작한 Unity XR 기반의 플러그인이다. **
- 유니티의 공식 플러그인 → 지원 및 업데이트가 보장될 것이라는 장점
모든 VR 플러그인 중 수명이 가장 김
**VR의 일반적인 기능을 스크립트 없이 편하게 구현할 수 있음**
- Teleportation이나 Interaction 등
- 스크립트 작성량이 가장 적음
**유니티에서 지원하는 다양한 VR장비들을 모바일과 PC에 손쉽게 연동 가능**
- PC/Mobile VR 장비에 모두 대응 가능
**AR Foundation을 연동하면 AR 콘텐츠 제작해도 활용 가능**
 

## XR Interaction ToolKit 주요 기능
아래의 항목들을 컴포넌트만으로도 사용 가능

- VR 디바이스의 HMD와 컨트롤러의 위치와 방향을 연동 가능
- 오브젝트와 컨트롤러의 직접적인 상호 작용
- 레이저 광선을 이용한 간접적인 상호 작용
- 상호작용이 가능한지 시각적인 피드백
- Unity UI와의 상호작용
- 상황에 맞는 오디오 재생 및 햅틱(진동) 피드백 지원 가능
- Unity Event 기반의 이벤트 연결
	- Hover, Select, Active 등
- AR Foundation 연동을 통해 AR 오브젝트 배치 및 조작 가능
	- Translate, Rotate, Scale
    
## 세팅방법
- 유니티 허브에서 3D(URP)를 선택
- 필수 패키지 설치 ( window -> Package Manager)
- Drop down에서 Unity Registry 선택 
### 패키지 목록
- Input System
설치 도중 중간에 유니티 에디터가 꺼졌다 켜짐
- 1. XR Plugin Management
- 2. Oculus XR Plugin
오큘러스 VR 기기 사용할 시 설치(시뮬레이터 쓸 거면 다운 안 해도 됨)
- 3. XR Interaction Toolkit
- 4. Universal RP
### 프로젝트 설정
- DEdit -> Project Settings -> XR Plug-in Management -> Oculus 체크
(PC 버전이나 시뮬레이터로만 진행할 사람은 체크 안해도 무방)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d0f381ac4106480b.png)
- Project Settings -> Player -> Run in Background 체크
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5ecf0ebb3100e2d7.png)
(시뮬레이터를 실행 시 발생할 수 있는 오작동 방지)

#### Preset Manager에서 왼손 오른손 구분
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4adc89fd5afe68eb.png)

Project Setting → Preset Manager를 가면 자동으로 연결되어 있는 것을 확인 가능
컨트롤러는 왼손과 오른손이 구분됨으로, 이름을 지어줘서 이를 구분해 준다.

- 다시 Package Manager로 가서 설치했던 XR Interaction Toolkit에서 두가지 Samples 설치
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/02ea3f3df679c72d.png)



    
### 주의
Mac에서 오큘러서(Meta Quest2)기기연동을 하려면 오큘러스 공식 홈페이지에서 프로그램을 다운로드 해야한다. 
(Mac용 프로그램은 없음 -> Mac은 기기 연동을 할 수 없음)
-> 그래서 Unity에서 시뮬레이터로 개발하고 Windiw로 빌드해야한다. 




