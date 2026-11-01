---
title: "[HTML] 메타 데이터 삽입"
date: 2024-03-22T06:52:49.345Z
tags: ["html"]
velog_slug: HTML-메타-데이터-삽입
---
> 메타데이터란?
: 데이터를 설명하는 데이터

사진 데이터의 메타데이터 : 사진 찍은 장소나 시간
이미지 데이터 : 이미지의 폭, 높이, 컬러 해상도
오디오 데이터 : 재생 시간, 채널 수, 샘플링 주파수

HTML 페이지에 대한 메타 데이터를 담기 위한 태그들은 뭐가 있을까?
<span style="color:red"><base\>, <link\>, <script\>, <title\>, <meta\></span>

  
> 메타 태그들은 <head\> 태그 안에 작성한다. 
>>```
<head>
  <base href="http://www.mysite.com/score/">
</head>
```
- <script\>는 <body\> 내에도 작성이 가능하다.

<hr><br>

###   base 태그<br>
  -	웹 페이지들의 기본 URL과 페이지가 출력될 윈도우 지정
  - 사용 예
  <small>*math.html이나 science.html 웹페이지가 모두 http://www.mysite.com/score/에 있는 경우 </small>
  
  ```
  <a href="http://www.mysite.com/score/math.html">수학</a>
  <a href="http://www.mysite.com/score/science.html">과학</a>
 ```
 위의 HTML 소스를 <base\> 태그를 이용하여 수정하면
  ```
<head>
  	<base href=http://www.mysite.com/score/>
</head>
<body>
  	<a href="math.html">수학</a>
  	<a href="science.html">과학</a>
  </body>
  
 ```
  
 <hr><br>
 
###   link 태그와 meta 태그
  
  -	<link\> 태그는 외부 자원 연결에 사용한다.
  예 : mystyle.css에 저장된 스타일 시트를 불러오도록 지시
```
  <head>
    <link type="text/css" rel="stylesheet" href="mystyle.css">
  </head>
```
  
  - <meta\> 태그는 다양한 메타 데이터를 표현한다. 
  	- 웹 페이지의 저작자, 문자 인코딩 방식, 내용 등
  
>웹 페이지의 저작자가 "황기태"임을 표기하는 사례
>>```
<meta name="author" content="황기태">
  ```
  
>웹 페이지의 내용 설명
>>```
<meta name="description" content="입학 요령에 대한 자세한 사항">
```
  
>웹 페이지의 키워드(검색 엔진에 의해 검색되게 하기 위함)
  >>```
<meta name="keywords" content="컴퓨터, 소프트웨어, 스마트폰">
```

>charset 속성으로 웹 페이지에 사용하는 문자 코드 지정
  >>```
<meta charset="UTF-8">
```