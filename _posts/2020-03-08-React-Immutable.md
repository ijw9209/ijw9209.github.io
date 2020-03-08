---
title: "[React] Immutable"
excerpt: "불변성이 중요한 이유"
toc: true
toc_sticky: true

categories:
  - React
tags:
  - React
last_modified_at: 2020-03-08T08:06:00-05:00
---

## 불변성이 중요한 이유?

기존 배열을 수정하는 것이 아니라 .slice() 연산자를 사용하여 배열의 사본만들기를 추천했음.
일반적으로 데이터 변경에는 두가지방법이 있다.
1. 데이터의 값을 직접변경
2. 원하는 변경값을 가진 새로운 사본으로 데이터를 교체

### 객체 변경을 통해 데이터 수정하기
```js
var player = {score: 1, name: 'Jeff'};
player.score = 2;
//이제 player는 {score : 2 , name: 'Jeff'} 이다.
```

### 객체 변경 없이 데이터 수정하기
```js
var player = {score: 1 , name: 'Jeff'};

var newPlayer = Object.assign({}, player, {score:2});
// 이제 player는 변하지 않았지만 newPlayer는 {score:2 , name: 'Jeff'}이다

// 만약 객체 spread 구문(전개구문)을 사용한다면 이렇게 쓸 수 있습니다.
// var newPlayer = {...player , score: 2};
```

+ 객체 변경이나 기본 데이터의 변경을 하지않는다면 이점
 - **복잡한 특징들을 단순하게**
   직접적인 데이터변이를 피함 이전버전의 이력을 유지하고 나중에 재사용
 - **변화를 감지**
   객체가 직접적으로 수정되기때문에 변화를 감지하는것은 어렵다
   감지는 복제가 가능한 객체를 이전 사본과 비교하고 전체 객체 트리를 돌아야함

   불변객체서 감지하는것은 상당히 쉽다.
 - **React에서 다시 렌더링하는 시기를 결정**  
   불변성의 가장 큰 장점은 React에서 순수 컴포넌트를 만드는데 도움을 준다.
   변하지않는 데이터의 변경이 이루어졌는지 쉽게 판단하고 컴퓨터가 다시 렌더링할지 결정함.

   그래서 **shouldComponentUpdate()** 를 이용하면 성능을 최적화할수있다.
