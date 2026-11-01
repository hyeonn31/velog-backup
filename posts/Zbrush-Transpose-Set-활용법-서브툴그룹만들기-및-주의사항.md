---
title: "[Zbrush] Transpose Set 활용법 서브툴그룹만들기 및 주의사항"
date: 2025-01-17T06:46:51.142Z
tags: ["Transepose set", "Zbrush", "서브툴", "트렌스포즈 세트"]
velog_slug: Zbrush-Transpose-Set-활용법-서브툴그룹만들기-및-주의사항
---
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7b2e69dd83059187.png)
지브러쉬로 작업을 하다보면 서브툴 여러개를 안꺼번에 움직이거나 크기를 조정하는 경우가 생긴다. 그럴 때마다 서브툴을 다 하나씩 합치고 움직이고 또 다시 분리하고, ,하면 너무 번거롭기 때문에 그럴때 그룹을 묶어 사용하는 방법에 대해 포스팅 해보겠다. 
### 1. New Folder 클릭 -> 이름 지정
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/dd4bd06b35f99f23.png)
### 2. 그룹으로 움직일 서브툴 드래그 하여 폴더 안으로 넣기

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ca8a0da2841f84cd.png)
### 3.폴더의 톱니바퀴 클릭 후 -> Transpose Set 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e199333b56c9f10d.png)
 
 ![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/f038f4c0cee5a4b9.png)
그러면 다른부분은 Transform Gizmo가 적용을 받지 않고 ,
폴더 안에 있었던 오브젝트들만 영향을 받는 것을 볼 수 있다. 
Move나 Scale도 가능하다. 

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fa238cb74f50819f.png)
원하는 조정이 끝났다면 우측상단 체크 클릭해서 빠져 나오면 된다. 



----------
## 주의사항
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5b57edece526e767.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/06f9dee62c3f5090.png)

이렇게 이동을 시켰는데 오브젝트들이 뭉게지고 모형이 변형되는 경우가 있다. 
이 경우를 처음봐서 애를 먹었다...

처음 시도 방법은 Focal Shift를 -100으로 조정하여 다시 시도해봤다. 
> Focal Shift:  브러시 중심에서 외부측에 대한 영향의 감쇠도를 조절
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e9418125a64e4a5d.png)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/ea8d30cec0943581.png)
네.. 그러하다.. 여전히 망가졌다...

2번째 해결방법은 바로 마스킹 확인이었다. 

모든 서브툴에 마스킹이 되어있는지 다시 확인하고 지웠더니

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/eeb3ce130f824427.png)

해결되었다는! 
도움주신 강사님 너무 감사를 표하며,,, 
같은 질문을 하지 않도록 벨로그에 기록해두도록 한다!