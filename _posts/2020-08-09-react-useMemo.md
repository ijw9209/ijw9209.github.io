---
title: "[React-hooks] useMemo"
excerpt: "useMemo"
toc: true
toc_sticky: true

categories:
  - React
tags:
  - React
last_modified_at: 2020-08-09T08:06:00-05:00
---

# useMemo

## useMemo 

useMemo는 **memoized**(메모이제이션)된 값을 반환함.

+ memoized : 컴퓨터 프로그램이 동일한 계산을 반복 해야할때 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게하는 기술. **메모아이제이션**이라고도 함.

`useMemo`는 의존성이 변경되었을 때에만 메모이제이션도니 값만 다시 계산함, 이 최적화는 모든 렌더링 시의 고비용 계산을 방지하게 해줌.

+ `useMemo`로 전달된 함수는 렌더링 중에 실행된다. 통상적으로 렌더링 중에는 하지 않는 것을 이 함수 내에서 하지않아야함. 예를들어 사이드 이펙트(side effct)는 `useEffect`에서 하는 일이지 `useMemo`에서 하는일이 아님

+ 배열이 없는 경우 매 렌더링 때마다 새 값을 계산함.

+ **useMemo**는 성능 최적화를 위해 사용할 수는 있지만 의미상으로 보장이 있다고 생각하면 안됨. 

## 사용법

전체 코드중 부분..

```js

import React, { useRef, useState, useMemo } from 'react';
import UserList from './UserList';
import CreateUser from './CreateUser';

function countActiveUsers(users) {
  console.log('활성 사용자 수를 세는중...');
  return users.filter(user => user.active).length;
}

function App() {
  const [inputs, setInputs] = useState({
    username: '',
    email: ''
  });
  const { username, email } = inputs;
  const onChange = e => {
    const { name, value } = e.target;
    setInputs({
      ...inputs,
      [name]: value
    });
  };
  const [users, setUsers] = useState([
    {
      id: 1,
      username: 'velopert',
      email: 'public.velopert@gmail.com',
      active: true
    },
    {
      id: 2,
      username: 'tester',
      email: 'tester@example.com',
      active: false
    },
    {
      id: 3,
      username: 'liz',
      email: 'liz@example.com',
      active: false
    }
  ]);

  const nextId = useRef(4);
  const onCreate = () => {
    const user = {
      id: nextId.current,
      username,
      email
    };
    setUsers(users.concat(user));

    setInputs({
      username: '',
      email: ''
    });
    nextId.current += 1;
  };

  const onRemove = id => {
    // user.id 가 파라미터로 일치하지 않는 원소만 추출해서 새로운 배열을 만듬
    // = user.id 가 id 인 것을 제거함
    setUsers(users.filter(user => user.id !== id));
  };
  const onToggle = id => {
    setUsers(
      users.map(user =>
        user.id === id ? { ...user, active: !user.active } : user
      )
    );
  };
  
  //useMemo
  const count = useMemo(() => countActiveUsers(users), [users]);


  return (
    <>
      <CreateUser
        username={username}
        email={email}
        onChange={onChange}
        onCreate={onCreate}
      />
      <UserList users={users} onRemove={onRemove} onToggle={onToggle} />
      <div>활성사용자 수 : {count}</div>
    </>
  );
}

export default App;


```

`useMemo`의 첫번째 파라미터에는 어떻게 연산할지 정의하는 함수를 넣어주고 두번째 파라미턴에는 deps 배열을 넣어주면 되는데, 이 배열의 내용이 바뀌면 등록한 함수를 호출해서 값을 연산 해주고, 만약 내용이 바뀌지 않았다면 이전에 연산한 값을 재사용하게 됨. 

출처

+ [react공식문서](https://ko.reactjs.org/docs/hooks-reference.html#usememo)
+ [https://react.vlpt.us/basic/17-useMemo.html](https://react.vlpt.us/basic/17-useMemo.html)
