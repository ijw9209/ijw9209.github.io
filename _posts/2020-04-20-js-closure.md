---
title: "[JS] Closure"
excerpt: "JS 클로져"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-04-20T08:06:00-05:00
---

# 클로져(Closure)

클로저란 함수가 속한 렉시컬 스코프를 기억하여 함수가 렉시컬 스코프 밖에서 실행될때 그 스코프에 접근 할
수 있게 하는 기능을 말한다.

```js

function outer() {
    var a = 2;
    function inner(){
        console.log(a);
    }
    return inner;
}

var func = outer();
func(); // 2

```

여기서 GC(Garbage Collector)가 `outer()` 의 참조를 없앨 것 같지만 내부함수인 `inner()` 가 해당 스코프의 변수인 a를 참조하고 있기 때문에 없애지 않는다 따라서 스코프 외부에서 `inner()`가 실행되도 해당 스코프를 기억하기 때문에 2를 출력하게된다. 즉, 여기서 클로저는 `inner()`가 되며 `func`에 담겨 밖에서도 실행되고 렉시컬 스코프를 기억한다.


## 예제 

클로저를 사용하는 대표적인 예제는 역시 "반복문 클로저"이다.

```js
function func() {
    for(var i = 1; i < 5; i++){
        setTimeout(function() { console.log(i);}, i*500);
    }
}
func(); // 5 5 5 5
```

코드의 의도한 바는 1부터 4까지 간격을 두고 출력하는 것이였지만 5가 4번 출력된다. 왜 이렇게 되는것일까/

`setTimeout()`을 반복문 안에서 돌리면 콜백함수가 계속해서 task queue에 쌓이게 되고 반복문이 끝나고 나서 call stack으로 돌아와서 실행된다. 콜백함수는 클로저이기 때문에 상위 스코프에게 `i`의 값을 물어보고 상위 스코프인 `func`의 스코프에선 `i`가 5까지 증가했기 때문에 5가 4번 출력된다.


## 해결방법

위 문제를 해결하기 위해서 2가지 방법이 있다

+ 새로운 함수 스코프로 해결하기
```js
function func() {
    for(var i=1; i<5; i++){
        (function(j){
            setTimeout(function() { console.log(j); }, j*500);
        })(i);
    }
}
func(); // 1 2 3 4
```

`setTimeout()`을 IIFE(Immediately Invoked Function Expression, 즉시실행함수 표현식)로 감싸게 되면, 새로운 스코프를 형성하고 나중에 콜백함수가 `j`를 참조할때 그 시점의 i값을 갖기때문에 원하는 결과를 얻을 수 있게 된다.

+ 블록 스코프로 해결하기

```js
function func() {
    for(let i = 1; i < 5; i++){
        setTimeout(function() {console.log(i);}, i*500);
    }
}
func(); // 1 2 3 4
```

출처 :
+ [https://github.com/baeharam/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/closure.md)