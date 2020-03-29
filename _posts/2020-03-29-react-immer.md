---
title: "[React] immer"
excerpt: "immer"
toc: true
toc_sticky: true

categories:
  - React
tags:
  - React
last_modified_at: 2020-03-29T08:06:00-05:00
---


# React - Immer

## Immer 란? 

immer는 불변의 상태를 더 편리한 방법으로 작업하게 할수있는 작은 패키지이다.
copy-on-write 메커니즘을 베이스로 한다.

기본 아이디어는 모든 변경 사항을 currentState의 프록시인 임시 draftState에 적용하는 것이다. 모든 mutations이 완료되면 immer는 초안 상테에 대한 mutations 을 기반으로 nextState를 생성.
즉 변경불가능한 데이터의 모든 이점을 유지하면서 데이터를 간단히 수정하여 데이터와 상호작용가능

![image](https://immerjs.github.io/immer/img/immer.png)

```js
import produce from "immer"

const baseState = [
    {
        todo: "Learn typescript",
        done: true
    },
    {
        todo: "Try immer",
        done: false
    }
]

const nextState = produce(baseState, draftState => {
    draftState.push({todo: "Tweet about it"})
    draftState[1].done = true
})
```

immer에서 오직 신경써야 할 것은 produce 함수이다. 
이 함수는 두가지 파라미터를 받아오는데 , 첫번째는 수정시키고 싶은 객체를 전달하고 두번째는 업데이터 함수를 전달해줌 업데이터 함수에서 파라미터로 받은 draftState를 불변성에 대해서 신경쓰지않고 일반 자바스크립트로 다루듯이 바로 업데이트를 해주면,immer가 나머지 작업을 처리해준다.