---
title: "JSX의 정의"
date: 2023-05-03T13:37:47.747Z
tags: ["JSX", "React", "프론트앤드"]
velog_slug: JSX의-정의
---
## JSX가 뭔가요?
JavaScript를 우리는 줄여서 JS라고 많이 부른다.
관련 라이브러리도 JS를 넣어서 알아볼 수 있도록 하여 부르곤 한다. 
그래서 JSX또한 JavaScript와 연관이 있어보이는데..
JSX는 무엇일까? 영어로는 A syntax extension to JavaScript.
->자바스크립트의 확장 문법이라는 뜻
> JavaScript + XML/HTML = JSX이다. 

간단한 JSX예제코드를 보겠다.
```jsx
const element = <h1>Hello, world!</h1>;
```
대입연산자 '=' 이 나온다. 왼쪽에 나오는 자료형 const와 변수명 element까지는 우리가 흔히 사용하는 자바스크립트 문법이지만
특이하게, 오른쪽은 HTML코드가 나온다. 
결과적으로 이 코드는 JavaScript 코드와 HTML코드가 합쳐진 것이다. 
즉, h1으로 둘러쌓인 문자열을 element라는 변수에 저장하는 것이다. 
JSX코드를 모르는 상태로 보면 무척이나 이상한 문법이라고 생각이 들 것이다. 

## JSX의 역할?
JSX는 내부적으로 XML과 HTML을 JavaScript로 바꿔주는 역할을 한다. 

**JSX코드를 JavaScript로 변환해주는역할**
```jsx
//createElement의 파라미터를 나타내보자
React.createElement(
  type, //유형, 타입 react컴포넌트나 HTML등의 문법이 들어올 수 있다. 
  [props], //속성
  [...children] //현재 element가 포함하고 있는 자식element
  )
```
예시를 살펴보자.
```jsx
#JSX를 사용한 코드

class Hello extends React.Component { //Hello라는 이름을 가진 React.Component
  render() {
    return <div>Hello {this.props.toWhat}</div>;
  }
}
//componet코드안에서 javascript와 html이 혼합된 jsx코드인 것을 볼 수있음

ReactDOM.render( // 이렇게 만들어진 component를 ReactDOM에 render함수를 사용해서 화면에 랜더링한다.
  <Hello toWhat="World" />,
  document.getElementById('root')
);
```

```jsx
#JSX를 사용하지 않은 코드

class Hello extends React.Component { 
  render() {
    return React.createElement('div',null,'Hello ${this.props.toWhat}');//Hello Component내부에서 jsx를 사용했던 부분이
  }
}

ReactDOM.render( 
  React.createElement(Hello, { toWhat: 'World'},null),// react.createElement로 대체된 것을 알 수 있다.
  document.getElementById('root')
```
결국 jsx문법을 사용하면 react에는 내부적으로 모두 creatElement라는 함수를 사용하도록 변환하게 되는 것이다. 

최종적으로 creatElement함수로 호출한 결과로 JavaScript객체가 나오게 된다. 

```jsx

//JSX를 사용한 코드
const element = (
  <h1 className="greeting">
    Hello, world!
    </h1> 
)

//JSX를 사용하지 않은 코드
const element = React.createElement(
  'h1',
  {className: 'greeting' },
  'Hello, world!'
)

```

즉. React에서 반드시 JSX를 사용해야하는 것은 아니다!
creatElement를 사용해서 다 변형할 수 있기 때문이다. 

하지만 JSX를 사용하면 장점이 많고 편리하다!