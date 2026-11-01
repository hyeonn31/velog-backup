---
title: "JSX의 장점이 뭘까"
date: 2023-05-03T13:55:57.067Z
tags: ["JSX", "React", "프론트앤드"]
velog_slug: JSX의-장점이-뭘까
---
## 😊장점
- 코드가 간결 
- 가독성이 향상
- 버그를 발견하기 쉬움!

```jsx
//JSX 사용
<div>Hello,{name}</div>

//JSX 사용X
React.createElement('div',null,'Hello, ${name}');
```
- Injection Attacks 방어 (입력창에 문자나 숫자같은 일반적인 소스코드를 입력하여 해당코드를 실행하게 만드는 해킹 방법이다.)
```jsx
const title = response.potentiallyMaliciousInput;

//이 코드는 안전합니다. 
const element = <h1>{title}</h1>; //jsx코드는 괄호를 통해 title변수를 삽입,인베딩한다. 명시적으로 선언되지 않은 값은 괄호 안에 들어 갈 수 없기 때문에 방어할 수 있다.
```

## JSX사용법
- XML/HTML코드 사이에 JavaScript코드를 사용하고 싶으면 JavaScript코드를 {중괄호}안에 넣어 추가할 수 있다. 
즉 JSX에 중괄호가 나오면 무조건 JavaScript!!!라고 생각할 수 있다. 

### 태그의 속성(attribute)에 값을 넣는 방법
```jsx
//큰 따옴표 사이에 문자열을 넣거나
const element = <div tabIndex="0"></div>

//중괄호 사이에 자바스크립트 코드를 넣으면 됨!
const element = <img src={user.avatarUrl}></img>
```

### 자식(children)을 정의하는 방법
```jsx
const element = (
  <div> //div tag의 자식은 h1, h2이다. 
    <h1>안녕하세요?</h1>
    <h2>열심히 리액트를 공부해 봅시다!</h2>
  </div>
);
```