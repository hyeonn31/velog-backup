---
title: "[Zbrush] 합집합 차집합"
date: 2024-08-12T06:25:19.647Z
tags: ["Zbrush"]
velog_slug: Zbrush-합집합-차집합
---
## 1. 합집합편
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/c26e35faca60c701.png)
이렇게 두 도형을 합치려면
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5856301a7961bb0b.png)
아래로 통합을 누르면 합쳐진다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5da1c0c95bad12a1.png)
하지만 잘라보면 이렇게 기둥부분이 살아있는 것을 볼 수 있다.

이렇게 두면 면수가 많아지는 것 뿐만아니라 3D적용을 할 때 뭉개지거나 겹쳐지게 표현될 수 있다. 그래서 이 "다이나메쉬" 작업을 해줘야 한다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f35d977d88157875.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/9d584c0e0ab5b1df.png)
밀도 조정 후 다이나 메쉬 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/8859bd84bcdde321.png)
짠 이렇게 합쳐진 모습이다.
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/36fb900fc576b8e6.png)
그 후 아까와 같이 잘라보면 이렇게 기둥부분이 사라진  모습을 볼 수 있다.

이렇듯 모델링을 할 때에는 속안이 비어있어야 꼬이지 않는다. 꼭 참고

-------------------------------

## 2. 차집합편

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/66982fc87d48004e.png)
이번엔 아까 합집합으로 합친 도형에 추가로 저 부분을 차집합해보겠다.

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/98e6806e4588f520.png)
서브툴에서 도형을 나란히 두고
항상 빼는 부분이 밑으로 가게 둔다.
그리고 빼는 부분은 도형을 초승달모형(2번째)로 클릭해서 바꿔준 후 합집합처럼 아래로 통합(머지다운)을 진행한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/4c83c004806023ca.png)
그 다음 지오메트리 - 다이나메쉬가 켜져있는지 확인 후 ctrl+빈곳 드래그 해주면 빠진 모습을 볼 수 있다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/063503e12b712237.png)
짠
