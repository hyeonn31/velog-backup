---
title: "[3ds max] 단축키 정리"
date: 2025-01-01T08:54:46.197Z
tags: ["3ds Max", "단축키"]
velog_slug: 3ds-max-단축키-정리
---
### View Control

상하좌우 이동: 마우스 휠

크게 이동: Ctrl + 휠

회전: Alt + 휠

확대: 휠 드래그

디테일한 확대: Alt+Ctrl+휠 상하 드래그

​

뷰포트 전환: Alt+W

(뷰포트 우측 탭 늘리면 메뉴 보기 편함)

뷰포트 우측 상단 뷰큐브를 조작해서 시점 조절 가능.

​
### View Shortcut

F=Front

T=Top

B=Bottom

L=Left

​

F3: 와이어프레임 보기/ 다시 누르면 셰이더 보기

F4: 셰이더, 와이어프레임 둘다 보기/ 다시 누르면 와이어프레임 껐다 켰다 가능

​

### Viewport 좌측 상단 메뉴

[+] : 뷰포트 관련 설정, 시점 바꾸기 가능

- Show grid: 뷰포트에 그리드 껐다 켰다 가능 [G]

- Configure Viewport: 뷰포트로 가져온 이미지 해상도 설정 바꿀 수 있음. 

-> Display Performance> Texture Maps 수치를 2048과 같은 고해상도로 올리면 이미지 해상도 좋아짐.

7을 누르면 뷰포트 왼쪽 상단에 폴리곤, 버텍스 카운트가 뜨는데 Configure Viewport의 Stastics 탭에서 더 필요한 것들로 바꿔줄 수 있음. 

->게임에서 더 많이 쓰는 Triangle Count, Total + Selection만 체크. OK

-> 그러면 현재 선택한 어셋의 트라이 갯수와 총 트라이 갯수 확인 가능.

​

[Perspective] : 뷰포트 시점 설정, 카메라 설정.

- Cameras: 카메라를 꺼낸 상태에서 선택하면 카메라 시점으로 화면이 보임.

- Show Safe Frames: 간혹 shift F 실수로 누르면 뷰포트가 잘리는데 다시 눌러서 다시 해제 가능.

- Viewport Clipping: 작은 크기의 어셋을 가까이서 볼때 속이 뚫려보이는 현상이 있는데, 이 기능을 키면 오른쪽에 노란 선과 함께 화살표가 뜸. 여기서 아래 화살표를 살짝 내리면 뚫려보이는게 정상적으로 보임. 상단의 화살표를 위쪽으로 올리면 멀리 있는게 잘 보이게 됨.

​

[Standard], [Default Shading] 이 둘은 셰이더 설정과 관련있음.

​

[Standard]: 보통 Standard로 작업하는데 [High Quilty]로 선택하면 그림자도 생기고 좀 더 고해상도로 작업 가능. 그대신 좀 느려짐.

​

[Default Shading]: 다양한 셰이더들 있음

- Facets: 스무스를 없애고 면들이 깎인 것 처럼 보임.

- Bounding Box: 박스 모양으로 보임.

- Flat Color: 베이스 컬러만 보고 싶을 때 사용. 셰이더가 빠지고 베이스 컬러만 보임.

- Viewport Background: 뷰포트 배경이 기본 Gradient로 되어 있는데 단일 색으로 하고 싶으면 Solid를 선택하기도 함. 배경 관련 옵션.

- Viewport Preferences: [Standard]의 Active Viewport Settings와 동일한 옵션인데, Preferences 탭에서 POV(Perspective Field of View) 수치를 조절할 수 있음. 

POV는 시야각(원근감) 조절하는 옵션인데, 간혹 엔진에서 특정 시야각이 정해져 있을 때 그 수치를 동일하게 맞춰줄 때 사용. 

———————————————————

​

복제: Shift + 드래그

​

### 상단 메뉴(맨 상단 툴바)

#### Group

- 오브젝트를 여러개 선택 후 클릭하면 그룹 이름도 지정할 수 있고 그룹이 됨.

- Ungroup: 그룹 해제

- Open: 그룹 유지한 상태로, 개별로 위치 변경. 

​

#### Customize

- Preferences > General > Scene Undo: 언두할 수 있는 갯수 설정 가능.

>Files: Autobackup 설정가능. 오토백업 파일 몇개로 설정할 건지, 백업 간격 등 원하는대로 설정.

>Viewports > Selection/Preview Highlights : 오브젝트 위에 커서 올릴 때 표시를 해줄지 말지 설정해주는 건데, 약간 거슬려서 끄는 걸 추천

>Gizmos: 여기서 설정할 건 없고, 키보드 +, -로  뷰포트에서 기즈모 크기 조절 가능

​

#### Scripting

-Open Script, Run Script를 클릭해서 스크립트를 가져와서 사용 가능

———————————————————

​

### 메인 툴바(상단 두 번째 줄)

1. <-: Undo [Ctrl+ Z]

2. ->: Redo [Ctrl+Y]

3. Link : 자식이 될 오브젝트들을 선택한 상태로 링크 아이콘 클릭, 부모가 될 오브젝트에 드래그하면 부모-자식 관계로 링크가 됨. 
자식 오브젝트들은 따로 컨트롤 가능하고, 부모 오브젝트를 움직이면 자식은 같이 움직임.

4. Unlink : 링크된 부모-자식 오브젝트를 한번에 드래그로 선택 후 언링크를 누르면 링크가 해제됨.

	* Schematic View (메인툴바 중 오른쪽에서 11번째 아이콘 (=사이에 화살표 있는 모양) 클릭하면 표가 나오는데 여기서 도식으로 링크 확인 가능. 여기서도 상단의 링크, 언링크 아이콘으로 링크를 끊거나 연결 가능.

5. Bind to space warp(물결 링크) : 오브젝트에 Bend, Twist 등을 링크해서 오브젝트를 변형할 수 있음. 

	- 오브젝트 꺼내고, 우측 +(create)탭에 ~~~물결 세개 아이콘 클릭하면 Bend가 있음.

	- bend 꺼내서 오브젝트 크기에 맞춰서 바운딩 박스를 만들고, 오브젝트 선택한 상태에서 상단 물결 링크 아이콘 누르고, 바운딩 박스로 드래그해서 링크.

	- +(create)탭 바로 옆 탭(modify) 클릭하고 아래에 파라미터의 Angle을 조절해보면 밴드가 적용되서 모양 변형 확인 가능.

6. All : 선택 관련 옵션. 드래그 해서 선택할 때 All로 되어 있으면 모두 다 선택되고, Light로 되어 있으면 라이트만 선택, 카메라로 되어 있으면 카메라만 선택할 수 있는 기능.

7. Select Object: 오브젝트 선택시에 사용. [Q]

8. Select By Name: 클릭하면 오브젝트 리스트가 뜨는데 여기서 이름을 클릭하여 선택.

9. Rectangular Selection Region: 드래그해서 선택할 때 모양 지정 가능. 기본 네모 모양 사용. 

10. Window/Crossing

	- 네모가 점선 바깥에 걸쳐 있는 모양: 오브젝트의 일부만 드래그해도 전체가 선택됨.

	- 네모가 점선 안에 있는 모양: 오브젝트의 모든 영역을 포함해서 드래그해야 선택됨.

11. Move: 오브젝트 움직이기. [W]

12. Rotate: 오브젝트 회전. [E]

13. Scale: 오브젝트 크기조절. [R]

14. Reference Coordinate System: 기즈모 설정

	- View: 기본, 기즈모 보여주는 상태

	- Screen: 현재 시점을 기준으로 기즈모 고정. 오브젝트를 회전해도 내 시점으로 고정되어 기즈모가 움직이지 않음.

	- Local: 기즈모의 축이 오브젝트와 수직으로 고정됨. 자주 사용.

15. Use Pivot Point Center: 오브젝트 여러개 선택시 피봇의 위치를 어디 기준으로 할 건지 설정.

	1) 오브젝트마다 피봇이 각각 존재. 여러개를 선택해서 크기를 키우면 각각의 피봇에 맞게 따로따로 크기가 커지고, 회전을 할때도 따로따로 회전함.

	2) 여러개 선택시 오즈젝트들의 중심에 피봇이 하나가 생기고 그 피봇을 기준으로 다같이 크기를 키우거나 회전할 수 있음.

	3) 오브젝트 기준이 아닌 그리드의 정중앙(0.0)에 피봇이 생김.
    
​
(19~22 자석 아이콘: 스냅 기능)

19. Snaps Toggle: 그리드 포인트 등 다양한 기준으로 스냅을 걸 수 있음. [S] 

20. Angle Snap Toggle: 회전 시 설정한 각도 기준으로 스냅 걸림. 기본 5도로 설정. [A] 

21. Percent Snap Toggle: 크기 조절시 설정한 퍼센트 기준으로 크기 조절 가능. 기본 10퍼센트로 설정.

	* Grid and Snap Settings: 스냅 세팅 옵션창. 스냅 아이콘들을 우클릭하면 나옴. 

**Snaps>** 그리드 포인트 기준으로 스냅할 건지, 피봇 기준으로 스냅할 건지 버텍스 기준으로 스냅할 건지 등

정해줄 수 있음

**Options>** 여기서 스냅할 때 각도나 크기를 얼마정도로 설정할 건지 수치 조절 가능. Angle은 회전각, Percent는 크기 퍼센트 수치 설정할 수 있음.

**Shape Creation>** Enable Shape Angle Constraints 체크 해제하면 버텍스 스냅할 때 Z축으로 이동하기 더 편하다고 함.

​
25. Mirror: 오브젝트를 대칭 시키는 기능.

- 물체가 대칭되는 걸 잘 볼 수 있도록 오브젝트 축을 옆으로 옮겨줄 거임. 우측 Hierachy탭에서 Affect Pivot Only를 선택하면 피봇 위치를 옮길 수 있음. 피봇 위치를 옮기고 Affect Pivot Only를 끄기. 

- 반사 시킬 오브젝트 선택하고 Mirror 아이콘 누르면 옵션 창이 뜨면서 반사가 됨. 

- 이 창에서 어느 축을 기준으로 반사할건지 정할 수 있고, 반사된 오브젝트를 복제하고 싶으면 copy 체크.

- 상단의 Geometry를 체크하면 오른쪽 Modifer List에 Mirror 스택이 뜨면서 뷰포트에 주황색으로 표시가 됨.

26. Allign: 원하는 오브젝트의 위치로 다른 오브젝트를 정렬 시킬 수 있음.

- 큰 오브젝트와 작은 오브젝트가 서로 다른 위치에 있고, 작은 오브젝트를 큰 오브젝트의 중심축에 맞게 위치를 옮기고 싶음. 그럴 때 작은거 선택한 상태로 Allign 클릭, 큰 오브젝트 선택하면 그 위치로 정렬됨. 창이 뜨는데 여기서 Pivot Point가 기본으로 설정돼 있는데 중심축 기준으로 맞춰주는 거임. Center는 오브젝트의 중앙이 기준. 아래에 Match Scale을 다 체크하면 오브젝트의 크기도 동일하게 맞춰줌. 

—————————————————

​

### 우측 Modify 탭

​

> ModiFier List

우클릭, Show Buttons 체크-> Selection 옵션들 나옴

또 우클릭, Configure Modifier Sets 여기서 자주 사용하는 기능들을 커스텀할 수 있는 창이 뜸. 

여기서 모디파이어의 갯수를 늘릴 수 있고, 추가할 수 있음. 이 수정사항이 Modifier List에 그대로 반영됨.

​

- Edit Poly: 노말이 뒤집혀 보인다던가 스무딩 그룹이 깨져보인다던가 하는 메쉬가 이상하게 보일 때, 근데 실제로 문제가 없는데 이상하게 보이고 수정이 안된다 싶을 때 이 기능을 사용하면 해결될 때가 있음.

- Bend: 오브젝트를 구부릴 수 있음.

- Shell: 오브젝트의 두께 조절 가능.

- Push: 노말 방향으로 부피를 늘리거나 줄이는 기능

- Symmetry: 오브젝트를 대칭 시켜주면서 Weld(결합)까지 시켜줄 수 있는 기능

   *우측 Symmetry의 스택 안의 Mirror 위치를 옮겨보면 모양을 대칭된 상태로 줄이거나 늘릴 수 있음.(합쳐진 상태로)

 *Mirror Axis에서 기준 축 설정 가능.

- FFD: 전체실루엣 수정 시 전체 메쉬에 바운딩 박스를 씌워두고 수정하는 기능.

  *2x2x2, 3x3x3, 4x4x4로 갈수록 바운딩 박스의 면이 잘게 나눠져서 세부적인 모양 수정이 가능.

- FFD(box): Set Number of Points를 클릭하여 얼만큼 면을 나눌 건지 정할 수 있음.

- ProOptimizer: Calculate를 누르면 메쉬를 계산해주고,메쉬의 면수를 조절하며 최적화할 수 있음.

 그냥 계산하면 적용한 텍스처가 사라짐. 텍스처를 유지하고 싶을 때 우측의 Keep Textures를 체크한 상태로 계산해야함.

 Optimization Level의 Vertex %, Vertex Count의 수치를 조정해서 메쉬 수를 줄이거나 늘리며 최적화할 수 있다.

—————————————————

​

### 단축키 설정 

Customize> Hotkey Editor



​

### Shortcut


-Undo: [Ctrl+Z]

-Redo: [Ctrl+Y]

​

-Remove: [Ctrl+E] 점, 선을 지울 때 사용. [Backspace]

- Convert To Editable Poly: [F5] 폴리곤 편집 모드로 전환

- Display Selected with Edged Faces: [D] F4번 눌러서 와이어프레임이 다같이 꺼져 있을 때, D를 누르면 선택한 오브젝트의 와이어프레임만 보여줌. 토폴로지 제작할 때 하이폴리곤과 로우폴리곤이 겹쳐 있으면, 하이폴리곤 와이어프레임 너무 복잡하게 보여서 방해가 되는데, 선택한 로우폴리곤 폴리만 보고 싶을 때 사용함.

- Export Selected: [Ctrl+2]

- Import File: [Ctrl+3]

- Reset Xform: [Shift+ ' ] 오브젝트의 축을 월드축 기준으로 다시 맞춰주는 기능. 오브젝트를 기울였을 때, 기즈모가 Local 상태면 오브젝트의 최초 축으로 고정되어 있을 거임. 엑스폼을 적용하면 기즈모를 월드축 기준으로 바꿔줌.

- Swift Loop: [Shift+W] 클릭으로 선을 한번에 둘러주는 기능.

- 반투명 모드: [Alt+X] 오브젝트를 반투명하게 볼 수 있음.

​

### *Unwrap

- Unwrap UVW 창 켜기

Modify탭의 Modifier List에 Unwrap UVW 클릭, 아래에 Open UV Editor클릭하면 유브 에디터 창이 뜸.

- 축 가운데로 정렬: [Shift+4 예정](플러그인 사용) 

우측 Hierachy 탭의 Pivot> Affect Pivot Only 클릭, Center to Object 클릭하면 됨. 

​

- 전체 선택: [Ctrl+A]

- 반전 선택: [Ctrl+I] 선택한 오브젝트 외의 것들을 선택해줌.

- Hide Selected: [Alt+H] 선택한 엘리멘트나 면을 숨겨줌.

- Unhide All: [Alt+U] 모두 숨김 해제.

- Hide Unselected: [Alt+I] 선택한 오브젝트 제외한 모든 오브젝트 숨김.

**위 하이드 옵션들은 우측 모디파이의 Edit Geometry에 버튼으로 있음. 

——————————————————————

​

(https://blog.naver.com/antodanfdy/222260298222)

​

### Convert to Editable Polygon(폴리곤 편집 모드)

- Vertex, Edge, Border, Polygon, Element를 기준으로 메쉬를 편집할 수 있는 기능.

​

- 오브젝트 선택 후 우클릭, Convert to:> Convert to Editable Polygon 선택, 우측에 Editable Poly 스택 생성됨.

-Vertex, Edge, Border, Polygon, Element

차례대로 단축키 1, 2, 3, 4, 5

​

**1. Vertex : 점을 선택해서 편집**

- Target Weld: 타겟 웰드 선택한 상태에서, 점을 선택하고 다른 점을 선택하면 점이 합쳐짐.

- Connect: 두 개 이상의 점을 선택해서 Connect를 누르면 점 사이를 연결하는 선이 생김.

(단축키 ctrl+shift+E -> C로 변경)

- Cut: 우측 Edit Geometry탭에 있음. 점 찍어서 면을 분할해줌.[Alt+C]

​

**단축키가 적용이 안되는 문제 발생!

-> Keyboard Shortcut Override Toggle (18번째 아이콘) : 현재 선택되어 있는 걸 기준으로 단축키 사용.

이거 켜주니까 단축키가 제대로 작동함.

​
**
2. Edge: 선을 선택해서 편집**

- Connect: 두 선을 선택하고 커넥트를 누르면, 두 선을 잇는 선이 생기면서 면 분할해줌. 

- Ring: 선을 하나 선택하고 링을 누르면 같은 선상의 방향을 가진 옆의 선들을 한번에 선택 가능. 

Ctrl 누른 상태로 옆의 선 선택하면 Ring 기능 사용 가능.

*Connect 버튼 옆 네모버튼 누르면 속성창 뜨는데, 분할할 선 갯수, 선 간격, 위치를 결정할 수 있다.

​

**선 지울 때 [Backspace]로 지울 수 있음.

선과 함께 점도 같이 지우려면 [Ctrl+Backspace]

​

**3. Border: 면이 뚫린 상태에서 뚫린 면의 선들을 한번에 선택해줌.**

뚫린 면의 선들을 한번에 선택해서 길이 늘릴 때 주로 사용.

- Cap: 뚫린 면 채워서 막을때 사용.

​

**4. Polygon: 면을 선택해서 편집**

- Extrude: 면을 잡고 뽑아서 늘리는 기능.

위로 좌클릭 드래그하면 순방향으로 늘어나고 아래로 드래그하면 역방향으로 들어감.

- Bevel: 면을 잡아 뽑아낸 다음, 면의 면적을 늘리거나 줄여서 경사를 만들어줌.

위로 드래그해서 길이 늘리고, 아래로 드래그할수록 면적 줄어듬. 

- Inset: 면 안에 면을 만들어줌.

면 안에 면 만든 다음에 Extrude 눌러서 뽑아주며 형태 만들어 줄 수 있음.

- Bridge: 면과 면을 연결해주는 기능.

두 오브젝트가 있고 각각의 면을 다리처럼 연결해줄 때 사용.

우선, Selection이 선택 안 되어 있는 상태에서 Modifier에서 Attach를 사용해 두 오브젝트를 합쳐줘야 함. 

그 상태에서 연결해줄 각 면 선택하고 Bridge누르면 연결됨.

​

**Extrude 할때, 정육면체의 옆면을 이루는 네면을 동시에 선택하고 각 면이 바라보는 방향으로 Extrude를 적용하고 싶을 때! (그냥 익스트루드 하면 이상하게 옆으로만 뽑아짐)**

Extrude의 네모 버튼으로 세팅창 열고, 맨 위의 옵션을 group에서 Local Nomal로 변경하면 됨. 그러면 각 면이 바라보는 방향으로 면이 뽑아짐!

​

**면을 두르는 Edge를 간단하게 생성하는 법!**

(선을 선택하고 Connect를 적용하는 법도 있지만)

Editable Poly상태에서 상단의 모델링 옵션들을 보면 Swift Loop라는게 있음. 선택 상태로 간단하게 원하는 위치에 면을 두르는 엣지 생성 가능.

​
[출처] 3ds Max 인터페이스, 단축키 정리|작성자 하동