---
title: "[JS] == vs === "
excerpt: "[JS] == vs ===)"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-09-06T08:06:00-05:00
---

# == vs === 

둘다 동일한 비교를 하지만 엄격한 동등 비교 연산자(===)의 경우, **타입변환(Type conversion)**이 일어나지 않으며 타입이 일치 해야한다.


```js   
'' ==  0    //false
0 == ''     //true
0 == '0'    //true

false == 'false'    //false
false == '0'        //true

false == undefineed  //false
false == null        //false
null == undefined    //true 

' \t\r\n ' == 0 //true

```
위 경우를 보면, 동등 비교 연산자(==)를 사용해서 여러가지 원시타입을 비교해보았는데, 타입변환이 발생함을 볼 수 있다.

단, 객체/배열의 경우는 참조타입이기 때문에 두 연산자 모두 동일하게 동작한다


```js
var a = {}
var b = {}

a == b  //false
a === b //false 

var c = []; 
var b = [];

c == d  //false
c === d //false 

```

문자열의 경우는 좀 특별한데, 자바스크립트에서 문자열은 원시타입이지만 객체로도 만들 수 있기때문에 그 동등 비교가 다르다.

```js
var a = "string"
var b = new String("string")
a == b  //true
a === b //false

```

퍼포먼스 측면에서는 아주 미묘한 차이가 있기 때문에 신경 쓸 바가 못됨, 
**안전한 타입체크와 더 좋은코드를 위해 비교 연산자(===)를 사용하는것이 바람직하다.**


+ 출처 [https://github.com/baeharam/Must-Know-About-Frontend/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/identity-equal.md)