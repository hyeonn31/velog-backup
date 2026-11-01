---
title: "[Blender]  옷 리깅 쉽게하기 | Transfer Mesh Data"
date: 2025-10-02T01:39:28.600Z
tags: ["blender"]
velog_slug: Blender-옷-리깅-쉽게하기-Transfer-Mesh-Data
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/495cbccb36ae3c12.png)

**Transfer Mesh Data** 기능은 한 메쉬에서 다른 메쉬로 속성 데이터(예: UV, Vertex Group, Vertex Color, Normal 등)를 복사하는 기능이다.
주로 비슷한 구조의 메쉬끼리 데이터를 공유할 때 많이 사용한다. 

그래서 몸에 이미 weight값이 들어가 있다면 
이 방법을 활용해서 쉽게 옷 리깅을 할 수 있다. 


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ac60deb5d4445a7d.png)
1. 우선 리깅을 원하는 옷을 클릭하고 속성데이터를 복사하고 싶은 몸을 그 뒤에 같이 클릭한다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a93a84a097598591.png)
2. F3키를 누르고 Transfer Mesh Data를 검색한다. 


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f229201ec7a0512e.png)
3. 그 후 나온 창에서 Vertex Group을 선택한다. 



![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/303ca5968f7369b6.png)
4. 그럼 좌측 하단에 이러한 창이 발생된다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f05e5e18ba895c0c.png)
5. 해당 부분을 All Layers로 체크한다. 

그 이후에 그럼에도 움직임이 자연스럽지 않은 경우엔 Weighted Paint로 직접 작업이 필요하다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7b23dde57db6387d.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/015533f1ee577075.png)
6. 자동으로 웨이트 값이 들어간 것을 확인 할 수 있다.

여기서 이상한 부분은 2차수정을 진행한다.   
        
  
> 출처 : https://www.youtube.com/watch?v=THt5Wqqo6mk 
