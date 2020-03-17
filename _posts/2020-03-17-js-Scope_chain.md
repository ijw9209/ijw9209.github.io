---
title:  "JS 스코프 체인"
excerpt: "JS 스코프 체인과 렉시컬스코프"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-17T08:06:00-05:00
---



# 스코프 체인

**스코프 체인(scpoe chain)**은 전역변수와 지역변수의 관계에서 나온다.

내부함수에서는 외부함수의 변수에 접근 가능하지만, 외부함수에서는 내부함수의 변수에 접근 할 수 없다. 
아래 enemy는 undefined

```js
var name = 'zero';
function outer() {
    console.log('외부' , name);
    function inner(){
        var enemy = 'nero';
        console.log('내부' , name);
    }
    inner();
}
outer();
console.log(enemy); //undefiend
```

inner 함수는 name변수를 찾기위해 자기자신의 스코프에서 찾고, 없으면 한단계 올라가서 outer스코프에서 찾고, 없으면 다시올라가 전역 스코프에서 찾는다. 다행히 전역스코프에서 name변수를 찾아 'zero'라는 값을 얻었다. 만약 전역스코프에도 없다면 변수를 찾지못했다는 에러가 발생한다.
이렇게 꼬리를 물고 계속 범위를 넓히면서 찾는 관계를 **스코프 체인**이라고 한다.

## 렉시컬 스코핑(lexical scoping)

**렉시컬 스코프는 함수를 어디서 호출하는지가 아니라 어디에 선언했는지에 따라 결정**

```js
var  x = 'global';

function foo() {
    var x = 'local';
    bar();
}

function bar() {
    console.log(x);
}

foo();  //global
bar();  //global

```

위 예제의 실행 결과는 함수 bar의 상위 스코프가 무엇인지따라 결정.
첫번째는 함수를 어디서 **호출** 하였는지따라 상위 스코프를 결정하는것이다
첫번째 방식으로 함수의 상위 스코프를 결정한다면 함수 bar의 상위 스코프는 함수 foo의 전역일 것이다

두번째는 함수를 어디서 **선언**하였는지에 따라 상위스코프를 결정,
두번째 방식으로 함수의 스코프를 결정한다면 함수 bar의 스코프는 전역일것이다

프로그래밍 언어는 이 두가지 방식중 하나의 방식으로 함수의 상위 스코프를 결정한다.
첫번째 방식을 **동적스코프** 두번째 방식을 **랙시컬스코프** 또는 **정적 스코프**라 한다.
자바스크립트를 비롯한 대부분의 프로그래밍 언어는 렉시컬 스코프를 따른다.

**렉시컬 스코프는 함수를 어디서 호출하였는지가 아니라 어디에 선언하였는지에 따라 결정된다**
자바스크립트는  렉시컬 스코프를 따르므로 함수를 선언한 시점에 상위 스코프가 결정된다.
함수를 어디에서 호출하였는지는 스코프결정에 아무런 의미를 주지않는다. 위 예제의 함수 bar는 전역에 설정되었다. 따라서 함수 bar의 상위스코프는 전역스코프이고 위 예제는 전역변수 x의 값 global을 두번출력한다.


+ [https://www.zerocho.com/category/Javascript](https://www.zerocho.com/category/Javascript/post/5740531574288ebc5f2ba97e)

+ [https://poiemaweb.com/js-scope](https://poiemaweb.com/js-scope)