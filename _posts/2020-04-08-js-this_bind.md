---
title: "JS this바인딩 우선순위"
excerpt: "this바인딩 우선순위"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-04-08T08:06:00-05:00
---



# this의 바인딩

EC(Execution Context)가 생성될때 마다 this의 바인딩이 일어나며 우선순위순으로 나열해보면 다음과 같다.

1. new 를 사용했을 때 해당 객체로 바인딩된다.

```js
var name = 'global';
function Func() {
    this.name = 'Func';
    this.print = function f() { console.log(this.name);}
}

var a = new Func();
a.print(); //Func

```

2. call, apply , bind 와 같은 명시적 바인딩을 사용했을 때 인자로 전달된 객체에 바인딩된다.

```js
function func() {
    console.log(this.name);
}

var obj = { name: 'obj name' };
func.call(obj);     // obj name
func.apply(obj);    // obj name
(func.bind(obj))();   // obj name
```

3. 객체의 메소드로 호출할 경우 해당 객체에 바인딩된다.

```js
var obj = {
    name : 'obj name',
    print: function p() { console.log(this.name);}
};

obj.print();    // obj name

```

4. 그 외의 경우

+ strict mode : `undefiend` 로 초기화된다.
+ 일반 : 브라우저라면 `window` 객체에 바인딩 된다.


출처 : 
+ [https://github.com/baeharam/Must-Know-About-Frontend/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/this.md)