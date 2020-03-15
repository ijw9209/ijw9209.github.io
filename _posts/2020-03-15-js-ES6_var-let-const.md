---
title: "[ES6] var,let,const 차이"
excerpt: "var,let,const의 차이"
toc: true
toc_sticky: true

categories:
  - js
  - ES6
tags:
  - js
  - ES6
last_modified_at: 2020-03-15T08:06:00-05:00
---

# var , let , const의 차이


## 변수 값의 변환

var를 사용하면 변수 선언의 경우 할당되는 값이 유동적으로 변경될 수 있다는 단점을 가지고 있다.


```js
var name = "Wonng";
console.log(name);

var name = "Jae";
console.log(name);

// woong
// Jae
```

다음과 같이 name이라는 변수를 2번 사용했는데도 에러가 나지 않고 각각 다른 값이
출력되는 것을 볼 수 있다.

하지만 ES6업데이트 이후 추가된 변수선언방식인 let , const는 var와 같은 선언방식을 막음

```js
let name = "Woong";
console.log(name);

let name = "Jae";
console.log(name);
// Identifier 'name' has already been declared
```
const도 마찬가지로 같은경우에는 오류가난다

let과 const의 차이점은 무엇일까?

let과 const의 차이점은 변수의 **immutable**여부이다.<br/>
let은 변수에 재할당이 가능하지만, const는 변수 재선언,재할당 모두 불가능하다

```js
//let
let test = 'test'   //output : test
let test = 'test2'  // Uncaught  SyntaxError: Identifier 'test' has already been declared
test = 'test3'  //output : test3
```


```js
//const
const test = 'test'   //output : test
const test = 'test2'  // Uncaught  SyntaxError: Identifier 'test' has already been declared
test = 'test3'  //output: Uncaught TypeError:Assignment to constant variable.
```

## 변수의 유효범위

var : function scope <br/>
let ,const : block scope


```js
//var 
var foo = "This is String.";
if(typeof foo === 'String'){
    var result = true;
}else{
    var result = false;
}

console.log(result);    //result : true
```



```js
//let,const
var foo = "This is String";
if(typeof foo === 'String'){
    const result = true;
} else {
    const result = false;
}

console.log(result);    //result : result is not defined

```

## hosisting 

호이스팅은 아래의 경로로
[http://ijw9209.github.io/js/js-Hoisting/](http://ijw9209.github.io/js/js-Hoisting/)