---
title: "[Adobe illustrater] 입체 글씨 만들기(blend)"
date: 2024-11-27T02:32:10.215Z
tags: ["illustrater"]
velog_slug: Adobe-illustrater-입체-글씨-만들기blend
---
## 입체 글씨 만들기 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b878bdd6be799f0b.png)

텍스트를 입력하고 폰트를 선택 한 후 blend를 사용하려고 했을 때 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c03a574525f99b21.png)

### object -> Blend -> Make가 활성화 되어있지 않을 수 있다. 
그 이유는 선택된 객체의 조건 미충족 때문이다.
Blend 기능은 최소 두 개 이상의 객체를 선택해야 작동한다.
선택한 객체들이 벡터 객체(패스 또는 도형)가 아니거나, 텍스트 객체인 경우에는 제대로 작동하지 않을 수 있다.


### 문제 확인:

#### 1. 두 개 이상의 벡터 객체를 선택했는지 확인
텍스트 객체인 경우, 텍스트를 "Create Outlines"로 벡터화 (텍스트를 선택하고 Object > Expand 또는 Type > Create Outlines 사용)
#### 2. 그룹화된 객체 문제
객체가 그룹화되어 있거나 클리핑 마스크 안에 있을 경우, Blend 기능이 제대로 작동하지 않을 수 있다.
##### 해결 방법 : 
그룹화된 객체를 선택한 후 Object > Ungroup를 사용하여 그룹을 해제
클리핑 마스크를 해제하려면 Object > Clipping Mask > Release를 사용
#### 3. 선택 상태 확인
Blend를 사용하려면 대상 객체를 정확히 선택해야 함. 화면에서 선택이 제대로 되었는지 확인

##### 해결 방법:

Selection Tool(V)이나 Direct Selection Tool(A)을 사용해 두 개 이상의 객체를 클릭하여 선택
선택 후 상태 표시줄이나 속성 패널에서 선택된 객체의 상태를 확인
#### 4. Illustrator 버그 또는 파일 문제
일부 Illustrator 버전에서 버그나 파일 자체의 문제로 Blend 기능이 비활성화될 수 있음

##### 해결 방법:

Illustrator를 재시작하거나 파일을 새로 저장 후 다시 시도
최신 업데이트가 설치되어 있는지 확인
위의 방법을 적용해보고 여전히 문제가 해결되지 않으면, 선택된 객체의 상태나 파일을 구체적으로 확인해볼 필요 있음

-----
작성자는 "Create Outlines"로 벡터화를 진행하니 해결되었다!


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9b349b37e15c6f9b.png)

이렇게 튀어나올 위치에 배치 해준 후
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/45fb3f5323d884ca.png)

"FANTAGE" 폰트 두개를 잡고, object - blend - make를 사용해준 모습이다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/d6f25b7029a22c2f.png)


그 후 블렌드 모드 더블클릭 ->
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8eafa7736ade0c5e.png)


specified steps 로 변경 후 원하는 만큼 갯수 늘려주기

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b8b6b200c2826bab.png)


짠


