---
title: "JS 이벤트루프"
excerpt: "JS 이벤트루프"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-30T08:06:00-05:00
---

# 이벤트 루프(Event loop)

## 이벤트 루프

자바스크립트는 단일 스레드(Single-threaded) 기반 언어로, 자바스크립트 엔진이 단일 콜 스택을 갖는다. 이말은 요청이 동기적으로 처리된다는 것을 의미한다. 비동기요청은 어떻게 처리될까 ? 그부분은 자바스크립트를 실행하는 환경인 브라우저나 Node.js가 담당한다. 자바스크립트 엔진과 그 실행환경을 상호 연동 시켜주는 장치가 이벤트 루프 이다. 따라서 이벤트 루프는 자바스크립트 엔진에 있지 않고 그 환경에 속한다


## 태스크 큐(Tsak queue)와 마이크로 태스크 큐(Microtask queue)

자바스크립트의 실행 환경은 2가지의 큐를 가지고 있으며,스크립트 실행 , 이벤트 핸들러 ,콜백함수등의 태스크(task)가 담겨져있다. 태스크가 콜백함수라면, 그 종류에 따라 다른 큐에 담기며 대표적인 예는 다음과같다

+ 태스크 큐
 - `setTimeout()` , `setInterval()` , UI렌더링 , `requestAnimationFrame()`
+ 마이크로태스크 큐
 - Promise, MutationObserver

이벤트 루프는 2개의 큐를 감시하고 있다가 콜 스택이 비게되면, 콜백함수를 꺼내와서 실행한다. 이 때 마이크로태스크 큐의 콜백 함수가 우선순위를 가지기 때문에 마이크로태스크 큐의 콜백함수를 전부 실행하고 나서 태스크 큐의 콜백함수들을 실행한다. (단, UI 렌더링이 태스크 큐에 속하기 때문에 마이크로태스크 큐의 태스크가 많으면 렌더링이 지연될 수 있다.)


### 예시

```js
console.log('콜 스택!');
setTimeout(() => console.log('태스크 큐!'), 0);
Promise.resolve().then(() => console.log('마이크로태스크 큐!'));

// 콜 스택!
// 마이크로태스크 큐!
// 태스크 큐!
```
처음 스크립트가 로드될 때 "스크립트 실행" 이라는 태스크가 먼저 태스크 큐에 들어간다. 그리고 나서 이벤트 루프가 테스크 큐에서 해당 태스크를 가져와 콜 스택을 실행하는 것이다. 콜스택에서는 이미 GEC(Global Execution Context)가 생성되있는 상태에서 "스크립트 실행" 이라는 태스크를 실행하게 되면 그제서야 GEC에 속한 코드가 실행되는 방식이다.

![IMAGE](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task0.png)

"스크립트 실행" 태스크가 태스크 큐에 들어가게된다.

![IMAGE2](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task1.png)

이후, 이벤트 루프가 그 태스크를 가져와 로드된 스크립트를 실행시킨다. 따라서 맨처음에 console.log가 실행된다.

![image3](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task2.png)

그 다음 setTimeout() 이 콜 스택으로 가고 브라우저가 이를 받아 타이머를 동작시킨다.

![image4](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task3.png)

타이머가 끝나면 setTimeout()의 콜백함수를 태스크 큐에 넣는다.

![image5](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task4.png)

promise가 콜 스택으로 가고 콜백함수를 마이크로태스크 큐에 넣는다.

![image6](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task5.png)

이벤트 루프는 마이크로태스크 큐에서 제일 오래된 태스크인 promise의 콜백 함수를 가져와 콜 스택에 넣는다.

![image7](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task6.png)

promise의 콜백 함수가 끝나고 태스크 큐에서 제일 오래된 태스크인 setTimeout()의 콜백함수를 가져와 콜 스택에 넣는다. 

![image8](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/task7.png)

setTimeout()의 콜백함수가 끝나면 콜 스택이 비게되고 프로그램이 종료된다.


출처 : 
+ [https://github.com/baeharam](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/event-loop.md)