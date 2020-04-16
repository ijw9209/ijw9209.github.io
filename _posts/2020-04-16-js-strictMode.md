---
title: "JS Strict mode"
excerpt: "JS Strict mode"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-04-16T08:06:00-05:00
---

# 엄격모드 (Strict mode)

ES5 부터 도입된 기능으로 기존의 무시되던 에러들로 하여금 에러를 발생시키게 한다. 파일 전체에 적용시킬수도 있고 함수 스코프에 적용시킬 수 있지만 블록 스코프는 불가능하다.

```js
"use strict";  // 파일 전체에 적용

 function f() {
     "use strict"; //함수 스코프에 적용
 }

```
이를 통해 실수를 잡아낼 수 있고 안전한지 않은 것들을 예방할 수 있다. 다음과 같은 특징을 갖는다

+ `var`가 생략된 변수를 전역객체에 바인딩 하지 않는다
+ `Nan = 5` 같은 할당 구문은 불가능하다
+ 제거할 수 없는 프로퍼티를 제거할 수 없다 (`delete Object.prototype`)
+ 함수의 매개변수 이름은 중복될 수 없다.(`function sum(x,x){}`)
+ `with` 키워드 사용할 수 없다.
+ 일반 변수를 삭제할 수 없다.(`delete x`)
+ `arguments.callee`를 사용할 수 없다.
+ `arguments` 객체는 항상 원본 인자를 저장한다. 즉 매개변수를 바꿔도 `arguments`의 값은 바뀌지 않는다
+ 8진수를 사용할 수 없다.(var a = 013)
+ `eval`은 새로운 변수를 스코프에 추가하지 않는다

JSLint나 ESLint와 같은 린터(Linter)를 사용할 수 있으면 사용하되 사용할 수 없으면 엄격모드를 사용하는 것이 좋다.

출처 : 
+ [https://github.com/baeharam/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/strict-mode.md)