---
title: "[ES6] 구조 분해할당"
excerpt: "구조 분해 할당"
toc: true
toc_sticky: true

categories:
  - js
  - ES6
tags:
  - js
  - ES6
last_modified_at: 2020-03-23T08:06:00-05:00
---


# 구조분해할당

구조분해 할당 구문은 배열이나 객체의 속성을 해제하여 그 값을 개별 변수에 담을 수 있게하는 JavaScirpt 표현식이다.


```js
var a, b , rest;
[a , b] = [10 , 20];
console.log(a)  //10
console.log(b)  //20

[a, b, ...rest] = [10, 20 ,30, 40 ,50]
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40 ,50]

({ a, b} = { a: 10, b: 20});
console.log(a); //10
console.log(b); //2018

({a,b, ...rest} = {a:10 , b: 20,c:30,d:40});
console.log(a); //10
console.log(b); //20
console.log(rest);  //{c:30,d:40}
```

구조 분해 할당의 구문은 할당문의 좌변에 사용하여 , 원래 변수에서 어떤 값을 분해해 할당할지 정의한다.

```js
var x = [1,2,3,4,5];
var [y,z] = x;
console.log(y); //1
console.log(z); //2

```


## 배열 구조 분해

### 기본 변수 할당

```js
var foo = ["one","two","three"];

var [one,two,three] = foo;
console.log(one);   //one
console.log(two);   //two
console.log(three); //three
```

### 선언에서 분리한 할당

변수의 선언이 분리되어도 할당가능

```js
var a, b;

[a,b] = [1,2];
console.log(a); //1
console.log(b); //2

```

### 기본값 

변수의 기본값을 할당하면, 분해한 값이 undefined일때 그값을 사용가능하다

```js

var a, b;

[a=5 ,b=7] = [1];
console.log(a); //5
console.log(b); //7

```

### 변수 값 교환하기

하나의 구조 분해 표현식만으로 두 변수의 값을 교환가능

```js
var a = 1;
var b = 3;

[a, b] = [b ,a];
console.log(a); //3
console.log(b); //1

```

### 함수가 반환한 배열 

함수가 배열을 반환하고 구조분해를 사용하면 반환된 배열의 작업을 더 간결하게 수행할수있다.


```js
function f() {
    return [1,2];
}

var a,b;
[a,b] = f();
console.log(a); //1  
console.log(b); //2
```

### 일부 반환값 무시

필요없는 반환값을 무시 할 수 있다.

```js
function f(){
    return [1,2,3];
}

var [a , , b] = f();
console.log(a); // 1
console.log(b); // 3


//반환값을 모두 무시할 수도 있다. 
[,,]=f();
```

### 변수의 배열의 나머지 할당

나머지 구문을 이용해 분해하고 남은 부분을 하나의 변수에 할당 할 수 있다.

```js
var [a, ...b] = [1,2,3];

console.log(a); //1
console.log(b); //[2,3]

```

나머지 요소의 오른쪽 뒤에 쉼표가 있으면 **SyntaxError** 발생!

```js
var [a, ...b,] = [1,2,3];
// SyntaxError: rest element may not have a trailing comma
```


### 정규 표현식과 일치하는 값 해체

```js
function parseProtocol(url){
    var parsedURL = /^(\w+)\:\/\/([^\/]+)\/(.*)$/.exec(url);
    if(!parsedURL){
        return false;
    }
    console.log(parsedURL); // ["https://developer.mozilla.org/en-US/Web/JavaScript", "https", "developer.mozilla.org", "en-US/Web/JavaScript"]

    var [, protocol, fullhost , fullpath] = parsedURL;
    return protocol;
}

console.log(parseProtocol('https://developer.mozilla.org/en-US/Web/JavaScript');  // "https"

```


## 객체 구조 분해

### 기본 할당

```js
var o = {p:42 , q:true}
var {p,q} = o;

console.log(p); //42
console.log(q); //true

```
### 선언과 분리한 할당

```js
var a, b;

({a,b} = {a:1 , b:2});

```

### 새로운 변수 이름으로 할당하기

```js
var o = {p:42 , q:true}
var {p:foo, q:bar } = o;

console.log(foo);   // 42
console.log(bar);   // true

```

### 기본값

객체에도 기본값을 할당할 수 있다. 논쟁이

```js
var {a = 10,b = 5} = {a : 3};

console.log(a);     //3
console.log(b);     //5

```

### 기본값 갖는 새로운 이름의 변수에 할당하기

```js
var {a:aa = 10 , b : bb = 5} = {a :3};

console.log(aa); //3
console.log(bb);  //5

```


### 함수 매개변수의 기본값 설정하기

ES5
```js
function drawES5Chart(options){
    options = options === undefined ? {} : options;
    var size = options.size === undefined ? 'big' : options.size;
    var cords = options.cords === undefined ? {x: 0 , y: 0} :options.cords;
    var radius = options.radius === undefined ? 25 : options.radius;
    console.log(size , cords , radius);
}

drawES5Chart({
    cords: {x : 18, y: 30},
    radius: 30
});

```

ES2015

```js
function drawES2015Chart({size = 'big', cords= {x : 0 , y: 0},radius = 25} = {}) {
    console.log(size , cords, radius);
}

drawES2015Chart({
    cords: {x : 18, y: 30},
    radius: 30
});

```


### 중첩된 객체 및 배열의 구조 분해

```js
var metadata = {
    title: "Scratchpad",
    translations: [
       {
        locale: "de",
        localization_tags: [ ],
        last_edit: "2014-04-14T08:43:37",
        url: "/de/docs/Tools/Scratchpad",
        title: "JavaScript-Umgebung"
       }
    ],
    url: "/en-US/docs/Tools/Scratchpad"
};

var { title: englishTitle , translations: [{ title: localeTitle }] } = metadata;
console.log(englishTitle); // "Scratchpad"
console.log(localeTitle);  // "JavaScript-Umgebung"

```

### for of 반복문과 구조 분해


```js

var people = [
  {
    name: "Mike Smith",
    family: {
      mother: "Jane Smith",
      father: "Harry Smith",
      sister: "Samantha Smith"
    },
    age: 35
  },
  {
    name: "Tom Jones",
    family: {
      mother: "Norah Jones",
      father: "Richard Jones",
      brother: "Howard Jones"
    },
    age: 25
  }
];

for (var {name: n, family: { father: f } } of people) {
  console.log("Name: " + n + ", Father: " + f);
}

// "Name: Mike Smith, Father: Harry Smith"
// "Name: Tom Jones, Father: Richard Jones"

```


### 함수 매개변수로 전달된 객체에서 필드 해체하기


user 객체로부터 id, displayName 및 firstName 을 해체해 출력합니다.
```js

function userId({id}) {
  return id;
}

function whois({displayName: displayName, fullName: {firstName: name}}){
  console.log(displayName + " is " + name);
}

var user = {
  id: 42,
  displayName: "jdoe",
  fullName: {
      firstName: "John",
      lastName: "Doe"
  }
};

console.log("userId: " + userId(user)); // "userId: 42"
whois(user); // "jdoe is John"

```

### 계산된 속성 이름과 구조 분해


```js
let key = "z";
let { [key]: foo } = { z: "bar" };

console.log(foo); // "bar"

```

### 객체 구조 분해에서 Rest

```js

let {a, b, ...rest} = {a: 10, b: 20, c: 30, d: 40}
a; // 10 
b; // 20 
rest; // { c: 30, d: 40 }


```


출처 : [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)