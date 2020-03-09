---
title: "[ES6] Spread_Syntax"
excerpt: "Spread_Syntax(전개 구문)"
toc: true
toc_sticky: true

categories:
  - js
  - ES6
tags:
  - js
  - ES6
last_modified_at: 2020-03-08T08:06:00-05:00
---

# Spread Syntax(전개 구문)

**Spread Syntax**는 피연산자를 개별적으로 분리하는 문법으로 , rest 파라미터는 이로 부터 나온다. 배열과 문자 set과 map은 iterable("반복적으로 셀 수 있는")이며 일반 객체는 spread문법의 대상이 될 수 없다.

```js
console.log(...[1,2,3]) // 1 2 3
console.log(...'Hello'); //H e l l o

console.log(...new Map([['a','1'],['b','2']])); // ['a' , '1'] ['b','2']
console.log(...new Set([1,2,3]));

// 이터러블이 아닌 일반 객체는 spread문법의 대상이 될 수 없다.
console.log(...{ a: 1 , b: 2})
//TypeError : Found non-callable @@iterator
```

## 1. Spread 문법의 사용방법

```js

// push

const arr1 = [1,2,3];
const arr2 = [4,5,6];

arr.push(...arr2);
console.log(arr1); // [1,2,3,4,5,6]


//slice(index , howmany , element1 , element2)

const arr1 = [1,2,3,6];
const arr2 = [4,5];

arr1.splice(3, 0, ...arr2);
console.log(arr1)  // [1 ,2 ,3 ,4 ,5 ,6]

```


+ 출처 : [https://mber.tistory.com/14](https://mber.tistory.com/14)
