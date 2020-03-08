---
title: "[ES6] Rest_parameter"
excerpt: "Rest_parameter"
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


# REST 파라미터

Rest 파라미터는 매개변수 이름앞에 세개의 점(...)을 붙여 정의한 매개변수를 의미
Rest 파라미터의 특징은 특정 인수의 갯수를 지정할 필요없이
들어온 인수를 배열로 바꿔 전달받을 수 있다는점이다.

```js
function example(...rest){
    console.log(rest);
}

example(1,2,3,4,5,6);
// [1,2,3,4,5,6]

```

함수에 전달된 인수들은 순서대로 파라미터와 rest 파라미터에 할당된다.

```js
function example(param1 . param2 , ...rest){
    console.log(param1);
    console.log(param2);
    console.log(rest);
}
example(1,2,3,4,5,6,7);
// 1
// 2
// (4) [3,4,5,6]
```


```js

// ES6 : 처음부터 배열이므로 변환의 필요성이 없음

function sum(...args) {
    console.log(arguments); [1,2,3,4,5]
    console.log(Array.isArray(args));   //true
    return args.reduce((pre , cur) => pre + cur);
}

console.log(sum(1,2,3,4,5));        //15

// ES5 

function sum() {
    var array = Array.prototype.slice.call(arguments);
    return array.reduce(function (pre , cur) {
        return pre + cur;
    });
}

console.log(sum(1,2,3,4,5));    //15

```

+ 출처 : [https://mber.tistory.com/14](https://mber.tistory.com/14)