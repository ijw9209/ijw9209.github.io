---
title:  "JS Data Types"
excerpt: "JS Data Types"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-02-28T08:06:00-05:00
---


#  JavaScript Data Types

 data types: numbers, strings, objects and more

```js
var length = 16;                               // Number
var lastName = "Johnson";                      // String
var x = {firstName:"John", lastName:"Doe"};    // Object
```


숫자와 문자열을 추가 할 때, 자바 스크립트 문자열로 숫자를 처리함.


```js
var x = 16 + "Volvo";   //16Volvo
var y = "Volvo" + 16;   //Volvo16

var a = 16 + 4 + "Volvo";      //20Volvo
var b = "Volvo" + 16 + 4;      //Volvo164
```

##  1. 자바스크립트 유형은 동적

자바스크립트는 동적유형. 동일한 변수가 서로 다른 데이터 유형을 유지하도록 사용될수 있음

```js
var x;           // Now x is undefined
x = 5;           // Now x is a Number
x = "John";      // Now x is a String
```

##  2. 자바스크립트 문자열

문자열 (또는 텍스트 문자열) "홍길동"와 같은 일련의 문자.

문자열은 따옴표로 기록됩니다. 당신은 작은 따옴표 나 큰 따옴표를 사용할 수 있음

```js
var carName1 = "Volvo XC60";   // Using double quotes
var carName2 = 'Volvo XC60';   // Using single quotes
```

인용구사용할때 안에 따옴표 사용할 수 있음


```js
var answer1 = "It's alright";             // Single quote inside double quotes
var answer2 = "He is called 'Johnny'";    // Single quotes inside double quotes
var answer3 = 'He is called "Johnny"';    // Double quotes inside single quotes
```

## 3. 자바스크립트 Numbers

자바 스크립트는 숫자의 한 유형이 있다.

숫자는 작성 또는 소수없이 할 수 있다.


```js
var x1 = 34.00;     // Written with decimals
var x2 = 34;        // Written without decimals
```

매우 큰숫자 혹은 작은숫자를 지수로 표기할수도 있음

```js
var y = 123e5;      // 12300000
var z = 123e-5;     // 0.00123
```

## 4. 자바스크립트 booleans

booleans 는  두 개의 값을 가질 수 있다 **true**나 **false**.

```js
var x = 5;
var y = 5;
var z = 6;
(x == y)       // Returns true
(x == z)       // Returns false
```

## 5. 자바스크립트 Array

자바 스크립트 배열은 대괄호로 기록.
다음은 배열 선언 코드 이다

```js
var cars = ["Saab", "Volvo", "BMW"];
```

배열 인덱스는 제 [1] 등과 첫 번째 항목 [0]을 의미하는 0부터 시작된다.

## 6. 자바스크립트 Object 

자바 스크립트 Object는 중괄호로 작성됩니다 {}.

쉼표로 구분 된 값 쌍 : 개체 속성은 이름으로 기록

```js
var person = {firstName : "lee" , lastName : "Jae Woong" , age :29 , eyeColor : "black"}
```

이 예에서 Object(person) 은 4개의 특성을 가짐


## 7. typeof 연산자

자바스크립트 변수의 유형을 찾을때 사용

```js
typeof ""             // Returns "string"
typeof "John"         // Returns "string"
typeof "John Doe"     // Returns "string"

typeof 0              // Returns "number"
typeof 314            // Returns "number"
typeof 3.14           // Returns "number"
typeof (3)            // Returns "number"
typeof (3 + 4)        // Returns "number"
```

## 8. Undefined

값없이 변수의 값만 가지면 **Undefined**

```js
var car;    // Value is undefined, type is undefined

car = undefined;    // Value is undefined, type is undefined
```

## 9. 빈 값

```js
var car = "";    // The value is "", the typeof is "string"
```

## 10. Null

**null**은 아무것도 없는 빈값

**null**로 설정하여 객체를 비울 수 있음

```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
person = null;    // Now value is null, but type is still an object
```

또한 **undefined** 로도 객체를 비울 수 있음

```js
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
person = undefined;   // Now both value and type is undefined
```

단)**undefined**는 데이터 타입도 변함

**undefined** 와 **null**의 차이점

```js
typeof undefined           // undefined
typeof null                // object

null === undefined         // false
null == undefined          // true
```


## 11. Primitive Data

기본 데이터는 값 추가 속성 및 메소드 단일 간단한 데이터 값이다.

**typeof**는 이러한 원시적 유형 중 하나를 반환 할 수 있다

+ **stirng**
+ **number**
+ **boolean**
+ **undefined**

```js
typeof "John"              // Returns "string"
typeof 3.14                // Returns "number"
typeof true                // Returns "boolean"
typeof false               // Returns "boolean"
typeof x                   // Returns "undefined" (if x has no value)
```


## 12. Complex Data

**typeof**는이 개 복잡한 유형 중 하나를 반환 할 수 있다

+ **function** 
+ **object**

The **typeof** operator returns "object" for objects, arrays, and null.

The **typeof** operator does not return "object" for functions.

```js
typeof {name:'John', age:34} // Returns "object"
typeof [1,2,3,4]             // Returns "object" (not "array", see note below)
typeof null                  // Returns "object"
typeof function myFunc(){}   // Returns "function"
```