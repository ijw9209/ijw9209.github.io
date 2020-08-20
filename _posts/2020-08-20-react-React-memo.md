---
title: "React.memo 를 사용한 컴포넌트 리렌더링 방지"
excerpt: "React.memo 를 사용한 컴포넌트 리렌더링 방지"
toc: true
toc_sticky: true

categories:
  - React
tags:
  - React
last_modified_at: 2020-08-20T08:06:00-05:00
---

# React.memo 를 사용한 컴포넌트 리렌더링 방지

React.memo라는 함수를 사용하면, 컴포넌트에서 리렌더링이 필요한 상황에서만 리렌더링을 하도록 설정해줄 수 있다.
사용법은 간단하다 그냥 감싸주면된다.

## 예시

```js

import React from 'react';

const CreateUser = ({ username, email, onChange, onCreate }) => {
  return (
    <div>
      <input
        name="username"
        placeholder="계정명"
        onChange={onChange}
        value={username}
      />
      <input
        name="email"
        placeholder="이메일"
        onChange={onChange}
        value={email}
      />
      <button onClick={onCreate}>등록</button>
    </div>
  );
};

export default React.memo(CreateUser);


```


```js

import React from 'react';

const User = React.memo(function User({ user, onRemove, onToggle }) {
  return (
    <div>
      <b
        style={{
          cursor: 'pointer',
          color: user.active ? 'green' : 'black'
        }}
        onClick={() => onToggle(user.id)}
      >
        {user.username}
      </b>
      &nbsp;
      <span>({user.email})</span>
      <button onClick={() => onRemove(user.id)}>삭제</button>
    </div>
  );
});

function UserList({ users, onRemove, onToggle }) {
  return (
    <div>
      {users.map(user => (
        <User
          user={user}
          key={user.id}
          onRemove={onRemove}
          onToggle={onToggle}
        />
      ))}
    </div>
  );
}

export default React.memo(UserList);

```

이런식으로 적용 후 input 수정시 리렌더링이 되지않는것을 확인해주면됨!

또한 `deps`를 최적화하고 싶을때는 `deps`내부에 있는 배열을 지우고, 함수들에서 현재 `useState`로 관리하는 
`users`를 참조하지 않게 하는 것이다.

즉, 함수형 업데이트를 하면된다. 함수형 업데이트를 하게되면, `setUsers`에 등록하는 콜백함수의 파라미터에서 최신 `users`를 참조 할 수 있기 때문에 `deps`에 배열을 넣지 않아도 된다.


### 예시 (전체 코드)

```js

import React, { useRef, useState, useMemo, useCallback } from 'react';
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
  const onChange = useCallback(e => {
    const { name, value } = e.target;
    setInputs(inputs => ({
      ...inputs,
      [name]: value
    }));
  }, []);
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
  const onCreate = useCallback(() => {
    const user = {
      id: nextId.current,
      username,
      email
    };
    setUsers(users => users.concat(user));

    setInputs({
      username: '',
      email: ''
    });
    nextId.current += 1;
  }, [username, email]);

  const onRemove = useCallback(id => {
    // user.id 가 파라미터로 일치하지 않는 원소만 추출해서 새로운 배열을 만듬
    // = user.id 가 id 인 것을 제거함
    setUsers(users => users.filter(user => user.id !== id));
  }, []);
  const onToggle = useCallback(id => {
    setUsers(users =>
      users.map(user =>
        user.id === id ? { ...user, active: !user.active } : user
      )
    );
  }, []);
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

위처럼 해주면 특정 항목을 수정할 때 해당 항목만 리렌더링 된다.
+ 리액트 개발자 도구의 버그인지는 모르겠지만, 제대로 적용하였는데 React.memo가 적용이 안된다면 실제 console.log()를 찍어 확인해보면 된다.

리액트 개발 시 `useCallback`, ``useMemo`, `React.memo`는 컴포넌트의 성능을 실제로 개선 할 수 있는 상황에서만 하는게 좋다.

추가적으로, 렌더링 최적화하지 않을 컴포넌트에 React.memo를 사용하는 것은, 불필요한 props 비교만 ㅏ는 것이기 때문에 실제로 렌더링을 방지할수 있는 상황이 있는 경우에만 사용하는걸 권장함.

React.memo 에서 두번째 파라미터에 `propsAreEqual` 이라는 함수를 사용하여 특정값들만 비교를 하는 것도 가능함

```js
export default React.memo(
  UserList,
  (prevProps, nextProps) => prevProps.users === nextProps.users
);

```

하지만, 잘못사용한다면 버그들이 발생하기 쉬움 예를 들어 함수형업데이트로 전환을 안했는데 이렇게 users만 비교를 한다면, onToggle과 onRemove 에서 최신 users 배열을 참조하지 않으므로 심각한 오류가 발생할 수 있음

출처 

+ [https://react.vlpt.us/basic/19-React.memo.html](https://react.vlpt.us/basic/19-React.memo.html)