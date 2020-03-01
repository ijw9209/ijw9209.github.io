---
title:  "JS ArrowFunction"
excerpt: "JS ArrowFunction"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-02-28T08:06:00-05:00
---

# ArrowFunction 



## 1.화살표 함수의 선언

Arrows(화살표) 함수는 => 문법을 사용하는 축약형 함수이다. 하지만 모든 경우 화살표 함수를 사용할수 있는것은 아니다. 기본문법은 아래와 같다

* 매개변수 지정방법
    1. () =>{ ... } 매개변수가 없을경우
    2. X => { ... } 매개변수가 한개인경우 () 생략가능
    3. (X,Y) => { ... } 매개변수 여러개인경우 , () 생략 불가

* 함수 몸체 지정방법
    + x => { return x * x} // single line block
    + x => x * x           // 함수 몸체가 한줄의 구문이라면 중괄호를 생략할수 있으며 암묵적으로    리턴된다 위의 표현과 동일하다         

    + () => {return { a: 1}; }
    + () => ({ a:1 })  // 위 표현과 동일하다 . 객체반환시 소괄호를 사용한다.

``` js
    () => {                 // multi line block.
        const x = 10;
        return x * x;
    };
```
## 2.화살표 함수의 호출
 -------------
 화살표 함수는 익명 함수로만 사용할수 있다. 따라서 화살표 함수를 호출하기 위해서는 함수 표현식을 사용한다

 ```js
// ES5
var pow = function (x) {return x * x; };
console.log(pow(10));   //100



// ES6
const pow = x => x * x;
console.log(pow(10));   //100 
 
 ```

또는 콜백 함수로 사용할 수 있다. 이경우 일반적인 함수 표현식보다 간결하다.

```js
// ES5
var arr = [1, 2, 3];
var pow = arr.map(function (x){ // x는 요소값
    return x * x;
});

console.log(pow);   // [1, 4, 9]


// ES6

var arr = [1, 2, 3];
var pow = arr.map(x => x * x);

console.log(pow); // [1, 4 ,9]

```

## 3.this
 -------------

 function 키워드로 생성한 일반 함수와 화살표 함수의 가장 큰 차이점은 this다

## 3-1 일반 함수의 this

 자바스크립트의 경우 함수 호출방식에 의해 this에 바인딩할 어떤 객체가 동적으로 결정된다. 다시말해 함수를 선언할때 this에 바인딩할 객체가 정적으로 결정되는것이 아니고, 함수를 호출할 때 함수가 어떻게 호출 되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다

 콜백 함수 내부의 this는 전역 객체 window를 가리킨다.

```js
function Prefixer(prefix) {
    this.prefix = prefix;
}

Prefixer.prototype.prefixArray = function (arr) {
    // (A)
    return arr.map(function (x) {
        return this.prefix + ' ' + x; // (B)
    });
};

var pre = new Prefixer('Hi');
console.log(pre.prerfixArray(['Lee','Kim']));

```

 (A) 지점에서의 this는 생성자 함수 Prefixer가 생성한 객체 , 즉 생성자 함수의 인스턴스 (위 예제의 경우 pre)이다.

 (B) 지점에서 사용한 this는 아마도 생성자 함수  Prefixer가 생성한 객체(위 예제의 경우 pre)일것으로 기대하겠지만, 이곳에서 this는 전역객체 window를 가리킨다. 이는 생성자 함수와 객체의 메소드를 제외한 모든 함수 (내부함수 , 콜백함수 포함) 내부의 this는 전역 객체를 가리키기 때문이다. 

콜백 함수 내부의 this가 메소드를 호출한 객체(생성자 함수의 인스턴스)를 가리키게 하려면 아래의 3가지 방법이 있다.

```js
 // Solution 1: that = this
 function Prefixer(prefix) {
     this.prefix = prefix;
 }
 
 Prefixer.prototype.prefixArray = function (arr) {
     var that = this; // this : Prefixer 생성자 함수의 인스턴스
     return arr.map(funtion (x) {
         return that.prefix + ' ' + x;
     });
 };

 var pre = new Prefixer('Hi');
 console.log(pre.prefixArray(['Lee','Kim']));

 ```

 ```js

 // Solution 2 : map (func , this)
 function Prefixer(prefix) {
     this.prefix = prefix;
 }

Prefixer.prototype.prefixArray = function (arr) {
    return arr.map(function (x) {
        return this.prefix + ' ' + x;
    }, this);   // this : Prefixer 생성자 함수의 인스턴스
};

var pre = new Prefixer('Hi');
console.log(pre.prefixArray(['Lee','Kim']));

```

ES5에 추가된 Function.prototype.bind()로 this를 바인딩한다.

```js
// Solution 3: bind(this)
function Prefixer(prefix) {
  this.prefix = prefix;
}

Prefixer.prototype.prefixArray = function (arr) {
    return arr.map(function (x) {
        return this.prefix + ' ' + x;
    }.bind(this));  // this : Prefixer 생성자 함수의 인스턴스
}

var pre = new Prefixer('Hi');
console.log(pre.prefixArray(['Lee', 'Kim']));

```

## 3-2 화살표 함수의 this

일반 함수는 함수를 선언할때 this에 바인딩할 객체가 정적으로 결정되는 것이 아니고 함수를 호출할때 어떻게 호출되었는지에 따라 this에 바인딩할 객체가 동적으로 결정된다고 하였다.

화살표함수는 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정된다. 동적으로 결정되는 일반함수와는 달리 **화살표함수의 this는 언제나 상위 스코프의 this를 가리킨다.** 이를 **Lexical this**라 한다. 화살표 함수는 앞서 살펴본 Solution 3의 Syntactic sugar이다.