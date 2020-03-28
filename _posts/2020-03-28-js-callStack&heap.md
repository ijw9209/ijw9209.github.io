---
title: "JS Callstack & heap"
excerpt: "JS 콜스택과 힙"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-28T08:06:00-05:00
---


# 콜 스택(Call stack)과 힙(Heap)

JS엔진이 JS를 실행할 때 원시 타입 및 참조 타입을 저장하는 메모리 구조로 콜 스택과 힙을 가짐

+ 콜 스택 : 원시타입 값 과 함수 호출의 실행 컨텍스트(Execution Context)를 저장하는공간
+ 힙 : 객체, 배열, 함수와 같이 크기가 동적으로 변할 수 있는 참조타입의 값

## 동작원리

```js
let a = 10;
let b = 35;
let arr = [];
function func() {
    const c = a + b;
    const obj = { d: c};
    return obj;
}
let o = func();

```

제일 처음 , GEC(Global Execution Context)가 생성 , 원시값은 콜 스택에 , 참조값은 힙영역에 저장

![image](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/memory1.png)

그 다음 함수 func()를 실행하게 되고 새로운 FEC(Function Execution Context)를 생성하게 되며 동일한 원시값은 스택에 , 참조 값은 힙에 저장된다.


![image1](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/memory2.png)

이후, 함수 func()가 객체 obj를 리턴해서 o에 저장된다.
리턴하기 때문에 FEC는 콜 스택에서 제거됨.

![image2](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/memory3.png)

전체 코드가 실행이 끝나고 GEC가 콜 스택에서 제거되면 , 힙의 객체를 참조하는 스택의 값이 없기 때문에 가비지 컬렉터(Garbage Colllector , GC)에 의해 제거됨

출처 : 
+ [https://github.com/baeharam/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/stack-heap.md)