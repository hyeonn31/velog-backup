---
title: "JAVA Script 간단개념"
date: 2023-05-02T04:26:13.796Z
tags: ["JavaScript", "script", "자료형", "프론트앤드"]
velog_slug: JAVA-Script-간단개념
---
## JavaScript 문법 알아보자

### 자료형(Data Type)

> 프로그래밍언어에서 데이터를 다루기 위해 미리 정해놓은 데이터의 유형
> 

변수를 선언 하지 않고 -> 대입되는 시점(동적 타이핑방식)

```jsx
//number type
let n1 = 1234;
let n2 = 5.678;

//String type
let s1 = "Hello";
let s2 = "World";

//Boolean type
let b1 = true;
let b2 = False;

//Null type
let n = null;

//Undefined type
let u1;
let u2 = undefined;

//Array type
let arr=[1,2,3,4];

//object type
let obj = {a: "apple", b: "banana", c:"acrrot"};

```

### JavaScript에서 배열을 사용한 예제 + 인덱스를 통해 배열에 접근한 예제

```jsx
//Number 타입으로만 이루어진 배열
let arr1 = [1,2,3,4,5];

//String 타입으로만 이루어진 배열
let arr2 = ["h","e","l","l","o"];

//Number 타입과 String 타입을 함께 사용한 배열
let arr3 = [1,"h",2,"i"];

//다양한 자료형들을 함께 사용한 배열
let arr4 = [true,1,undefined,false,"h",2,null,"i"];

console.log(arr1[0]);
//출력결과 : 1

console.log(arr2[1]);
//출력결과 : e

console.log(arr3[2]);
//출력결과 : 2

console.log(arr4[3]);
//출력결과 : false
```

```jsx
//값으로 String 타입만을 사용한 객체
let obj1 = {a: "apple", b: "banana", c: "carrot"};

//값으로 Number 타입만을 사용한 객체
let obj2 = {a:1, b:2, c:2};

//값으로 다양한 자료형들을 함께 사용한 객체
let obj3 = {a : "hello", b: 100, c:[1,2,3,4]}

//값으로 객체를 사용한 객체
let obj4 ={
	a:{a1: 1, a2: 2},
	b:{b1: 3, b2: 4},
	c:{c1: 5, c2: 6}
};

console.log(obj1['a']);
//출력결과 apple

console.log(obj2.a);
//출력결과 1

console.log(obj3['c']);
//출력결과 [1,2,3,4]

console.log(obj4.c.c2);
//출력결과 6 
```

