---
title: "[Adobe After Effects] 객체 없애기, 분리하기"
date: 2024-03-18T06:15:40.949Z
tags: ["After Effects", "adobe"]
velog_slug: Adobe-After-Effects-객체-없애기-분리하기
---
1. 레이어를 선택 한다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/85e40d92d8e9c936.png)


2. 펜툴을 이용하여 객체를 따준다. 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7e14fb19178cae97.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/989aa9a4172bf914.png)
완성된 모습.




3.
Mask Feather 값을 1.0,1.0 plxels로 변경,
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/fddb4f262169ce1c.png)

4. 레이어 복사하기 (ctrl+d) 후 복사한 레이어 속성을 subtract으로 변경
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/54a05eb0684dbb10.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2ac170f035dd40f2.png)
하단 레이어(복사한 레이어)는 배경만 남고
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e9654e87cff0c88f.png)
상단에 레이어는 강아지만 남는다. 

5. 하단 레이어의 마스크 영역을 약간 확장시켜준다. (화면에서 잘 보이게 하기 위해 10.0 plxels로 했지만 원래는 누끼 딴 그림이 안보일 정도로만 넓혀주면 된다.)

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7b99dea8513c2c59.png)


6. 해당 버튼 클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/33adb7476fb8372d.png)


7. Content-Aware Fill클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/1ded8f3161347969.png)


8. wark aware bar를 1프레임만 남겨두고 앞으로 옮기기 
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/b71cf0d62b71cf2f.png)


9. surface로 변경
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2ae9dd822456ed72.png)


10. Generate Fill Layer클릭
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/7e6c58497d293958.png)
(선이 살짝 남을 경우 ctrl+z 후에 마스크 영역을 좀 더 확장시켜주고 다시 적용시키면 된다. )


11. 생겨난 Fill [0-0].png파일을 중앙에 배치해준다.  
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/cef18b79c39b297a.png)

12. 레이어 선택후 오른쪽 마우스 클릭 - time - freeze frame
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/e3826b5f79647d81.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/6b79351b0c8d8a94.png)
이 상태로 드레그 하면 원하는대로 늘릴 수 있다. 

13. 만들어낸 두 레이어를 같이 선택하고 오른쪽 마우스 클릭 - Pre-compose선택 - OK
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/55b8d69cf8756459.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/a5d31c1eb4949148.png)
pre compose된 그룹 이름을 background로 바꾸기

14. Position줘보기
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/96a3d1f6c8d97578.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/60751afd10b36e8a.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/53267954d8e94078.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/2f3306687dcd433d.png)
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/eedb85600387c86a.png)
마우스 천천히 움직이기