---
title: "[React] Redux"
excerpt: "Redux"
toc: true
toc_sticky: true

categories:
  - React
tags:
  - React
last_modified_at: 2020-03-21T08:06:00-05:00
---

# Redux

Redux란 ? 예측가능한 상태의 저장소 
상태를 중앙에서 관리하는것을 통해 데이터가 예측하지 않은대로 변형될 가능성을 낮춤,
개발의 복잡성을 낮춘다.


![image](https://miro.medium.com/max/625/1*zTXY3OfZm5nreThL4lnu4A.png)


react는 컴포넌트별로 만들어진 사회와 비슷,필요없는 렌더함수가 호출되어 효율이 떨어지고, 연결이 되어있어야함.
react-redux는 모든 정보는 redux가 가지고 있다. store에 요청을 하여 정보를 가져올수 있다.

특징 
+ (Single Source of Truth) 하나의 상태(=객체)를 갖는다. 하나의 객체안에 모든 데이터를 모아놓는다.


![image1](https://s3-ap-northeast-2.amazonaws.com/opentutorials-user-file/module/4078/11034.png)


+ store : 은행이라고 비유 , 정보가 저장되는 곳
 - state : state실제 정보가 저장됨. 절대로 state에 직접 접속하면안됨.
 - reducer : 함수를 만들어주어서 공급해줘야됨 , state를 입력값으로 받고 action을 참조해서 새로운 state값을 만들어서 리턴하는 새로운 가공자
 
```js
function reducer(oldState , action) {
    //....
}
var store = Redux.createStroe(reducer);
```
 - getState : state값을 가져옴

```js
function render() {
                //state값을 가져옴
var state = store.getState();
//...
document.querySelector('#app').innerHTML = <h1>WEB</h1>
}
```
 - subscribe : state값이 바뀔때마다 render함수를 호출하여 UI가 새롭개 갱신
 
```js 
store.subscribe(render);
```
+ render : UI를 만들어주는 역할을하는 우리가짜는 코드


 - dispatch : reducer를 호출(두개의 값을 전달 현재state , action data(객체))를 전달하여 state값을 바꿈, 작업이 끝난뒤 subscribe를 이용해 render함수를 호출

```js
<form onSubmit="
                    //여기있는 객체가 action >> dispatch에게 전달
    store.dispatch({type:'create',payload:{title:title ,desc:desc })
">
```    



내가생각하는 redux를 사용하는 이유 : 기존의 react구조는 부모와 자식컴포넌트들간의 연결이 되어있어야하는데
redux는 store라는 저장소로 연결되어있어서 코드의 복잡성이 낮아지고 , 중앙에서 관리하여 유지보수가 용이하게만듬




출처 :

+ [생활코딩](https://opentutorials.org/module/4078/24935)