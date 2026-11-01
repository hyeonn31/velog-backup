---
title: "처음이세요? HTML부터"
date: 2023-03-24T07:25:33.958Z
tags: ["html", "프론트앤드"]
velog_slug: HTML-hwxk4t0b
---
# HTML에 대해 알아보자

- 웹을 이루는 가장 기본적인 빌딩블럭
- 웹 컨텐츠의 구조와 의미를 결정함
- 웹 페이지에서 사용하는 다양한 요소를 정의함
- 이미지, 비디오, 텍스트 등 다양한 형태의 컨텐츠를 포함할 수 있음
- 웹 페이지를 보는 사용자들이 실제로 보게 될 컨텐츠를 정의하는 데 사용됨
- HTML(Hypertext Markup Language) : 웹 브라우저 상에서 보여지도록 디자인 된 문서를 뜻함
- 표준화 된 Markup language를 사용
    - 마크업 언어는 태그가 시작되고 끝나는 구조를 가지고 있음

## 가장 기본적인 HTML 구조

```html
<!DOCTYPE html> //DOCTYPE은 html이다.
<html> //thml태그는 가장 상위에 있는 태그이다.
	<head>
		<meta charset="stf-8"> //글자의 포멧이 utf-8을 사용함(모든 언어 지원)
		<meta name="viewport" content="width=device-width"> //device 스크린 너비를 모두 쓰겠다.
		<title>JS Bin</title> //브라우저 검색 및 북마크 추가 시 보여지는 타이틀
	</head>

	<body>
		<h1>Heading1</h1>
		<h2>Heading2</h2>
		<button>Click Me!</button>
	</body>
</html>

```

html 태그 안에는 <head>와 <body>로 나누어져 있는 것을 알 수 있다. 

- **head**
    - UI적인 요소가 전혀 없음
    - 구글에서 검색할 때 나오는 타이틀, 부가설명, 북마크추가할 때 나오는 제목이나 아이콘들이 정의되어 있음
    - CSS파일을 연결하는 것도 head파트에서 진행됨
    - 사용자에게 보여지는 정보가 없고, 메타데이터만 있음
- **body**
    - 사용자에게 보여주는 가장 중요한 최상의 컨테이너(유저한테 보여지는 것)

### tag

- h1: 제일 큰 헤딩 언어
- h2 : 두번째로 큰 헤딩 언어
- button : 클릭이 가능하게 표시됨

> 지원 가능한 정의 된 tag들은 어디서 볼 수 있나요?
> 
<a href="https://developer.mozilla.org/ko/docs/Learn/Getting_started_with_the_web/HTML_basics" target=_blank>MDN HTML</a>

moz://a에서 만든 웹사이트로 전세계 많은 웹 개발자들이 정보를 확인함

(가장 빨리 최신 정보가 업로드 됨)

> 사용한 tag가 error가 있는지 확인하는 법
> 
  <a href="https://validator.w3.org/" target=_blank>Markup Validation Service (W3C)</a>

<aside>
💡 웹사이트를 조각조각 나누는 연습을 해보자

</aside>

![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/be8b0e56129ee4c0.png)


# 웹사이트의 구조
![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/3bfc7e4d9880ef64.png)


![](https://cdn.jsdelivr.net/gh/hyeonn31/velog-backup@main/assets/5421fffe4cdfc39e.png)

- 웹사이트 디자인마다 모든 세션이 필수로 들어가는 것은 아니다.
- main도 section으로 나눌 수 있는데, section안에 article로 나눌 수 있다.
    - article : 여러가지 아이템들을 그룹화하여 재사용 가능한 아이들이 모아져 있는 것을 말함

# Tag의 종류

## BOX

- sectioning
    
    header
    
    footer
    
    nav
    
    aside
    
    main
    
- section
    
    section
    
    article : 재사용 가능한 아이들 그룹화
    
    div : 아무곳에서나 쓸 수 있는 / 텍스트 버튼 묶기 등 
    
    span 
    
    form
    

## ITEM (사용자에게 보여짐)

- a
- button
- input
- label
- img
- video
- audio
- map
- canvas
- table


> 참고
> 

[HTML 기초, React 할때 꼭 필요한 팁! 쉽다고 무시하면 안돼요 | 프론트엔드 개발자 입문편: HTML, CSS, Javascript](https://www.youtube.com/watch?v=i0FN-OwJ7QI&list=PLv2d7VI9OotQ1F92Jp9Ce7ovHEsuRQB3Y&index=9)

[HTML 태그 완성, 웹 포트폴리오 만들기 전에 꼭 보세요  | 프론트엔드 개발자 입문편: HTML, CSS, Javascript](https://www.youtube.com/watch?v=OoA70D2TE0A&list=RDLVi0FN-OwJ7QI&index=2)