---
title: "JavaScript의 함수"
date: 2023-05-02T05:14:47.874Z
tags: ["JavaScript", "연산자", "프론트앤드"]
velog_slug: JavaScript의-함수
---
## 함수를 정의하는 방법
```jsx
// 1. function statement를 사용
function sum(a,b) {
  return a+b;
}

console.log(sum(10,20));
//출력결과 : 30

// 2. arrow function expression을 사용
const multiply = (a,b) => {
  return a*b;
}

console.log(multiply(10,20));
//출력결과: 200

```