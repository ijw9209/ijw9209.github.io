---
title: "[React-hooks] useEffect를 사용하여 마운트/언마운트/업데이트"
excerpt: "# useEffect를 사용하여 마운트/언마운트/업데이트시 할 작업 설정"
toc: true
toc_sticky: true

categories:
  - React
tags:
  - React
last_modified_at: 2020-08-02T08:06:00-05:00
---

# useEffect를 사용하여 마운트/언마운트/업데이트시 할 작업 설정

useEffect라는 hook을 사용하여 classComponent 에서 사용하였던 componentDidMount() 와 componentWillUnmount() 의 기능 들을 사용할 수 있다.
또한 update 될때 props가 바뀌었을때 특정 작업을 처리하는 방법을 정리한다.

## 마운트 / 언마운트

### UserList.js


```js
import React , { useEffect} from 'react';

function User({ user , onRemove , onToggle }){
    useEffect{() => {
        console.log('컴포넌트가 화면에 나타남');
        return () => {
            console.log('컴포넌트가 화면에서 사라짐');
        };
    }, []};
    return (
        // 내용
    )
}


```

`useEffect`를 사용할 때 는 첫번째 파라미터에는 함수, 두번째파라미터에는 의존값이 들어가 있는 배열 (`deps`)를 넣음, 만약 `deps`를 비우게 된다면 , 컴포넌트가 처음 나타날때만 `useEffect`에 등록한 함수가 호출된다.

그리고, `useEffect` 에서는 함수를 반환 할 수 있는데 이를 `cleanup`함수라고한다. `cleanup`함수는 `useEffect`에 대한 뒷정리를 해준다고 이해하면 되는데 , `deps`가 비어있는 경우에는 컴포넌트가 사라질때 `cleanup` 함수가 호출된다. 

주로, 마운트 시에 하는 작업들은 다음과 같은 사항들이 있다.

+ `props` 로 받은 값을 컴포넌트의 로컬 상태로 설정
+ 외부 API 요청 (REST API등)
+ 라이브러리 사용 (D3, Video.js 등...)
+ setInterval을 통한 반복작업 혹은 setTimeout 을 통한 작업 예약

그리고 언마운트 시에 하는 작업들은 다음과 같은 사항이 있다.

+ setInterval , setTimeout을 사용하여 등록한 작업들 clear 하기 (clearInterval , clearTimeout)
+ 라이브러리 인스턴스 제거


## deps 에 특정 값 넣기

deps에 특정 값을 넣으면 컴포넌트가 처음 마운트 될때에 호출이 되고, 지정한 값이 바뀔때에도 호출이 된다. 그리고 , deps안에 특정 값이 있다면 언마운트시에도 호출이되고, 값이 바뀌기 직전에도 호출이 된다. 


```js

import React , { useEffect} from 'react';

function User({ user , onRemove , onToggle }){
    useEffect{() => {
        console.log('user 값이 설정됨');
        console.log(user);
        return () => {
            console.log('user가 바뀌기전...');
            console.log(user);
        };
    }, [user]};
    return (
        // 내용
    )
}

```

`useEffect` 안에서 사용하는 상태나 , props 가 있다면 , `useEffect`의 `deps`에 넣어주어야 한다. 그렇게 하는게 규칙임

만약 `useEffect`안에서 사용하는 상태나 props 를 `deps`에 넣지 않게 된다면 `useEffect`에 등록한 함수가 실행 될때 최신 props/ 상태를 가르키지 않게됨

### deps 파라미터를 생략하기

`deps` 파라미터를 생략한다면 , 컴포넌트가 리렌더링 될 때마다 호출이 됨 

```js
import React, { useEffect } from 'react';

function User({ user, onRemove, onToggle }) {
  useEffect(() => {
    console.log(user);
  });
  return (
      //내용
  )

```

참고로 리액트 컴포넌트는 기본적으로 부모컴포넌트가 리렌더링되면 자식 컴포넌트도 리렌더링됨. 바뀐 내용이 없다 할 지리도 렌더링된다

물론 실제 DOM에 변화가 반영되는 것은 바뀐 내용이 있는 컴포넌트만 해당함 하지만 Virtual DOM에는 모든걸 다 렌더링 하고 있다는 것이다


출처
+ [https://react.vlpt.us/basic/16-useEffect.html](https://react.vlpt.us/basic/16-useEffect.html)