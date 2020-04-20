---
title: "[React] LifeCycle"
excerpt: "LifeCycle 정리"
toc: true
toc_sticky: true

categories:
  - React
tags:
  - React
last_modified_at: 2020-04-20T08:06:00-05:00
---

# React LifeCycle

리액트 컴포넌트 라이프 사이클 단계

React의 라이프사이클은 크게 세 단계로 나뉜다
마운트 - 업데이트 - 언마운트

이중 자주 쓰이는 것들은

+ render
+ componentDidMount
+ shouldComponentUpdate
+ componentDidUpdate
+ componentWillUnmount

등이 사용된다.

![image](https://react-nodejs-tutor.github.io/taling4th-coursebook/assets/life%20cycle.png)


## 마운트 단계


### constructor

```js
constructor(props){
    super(props);
}

```

`constructor`는 컴포넌트가 브라우저에 나타나기전에 호출된다. render()전에 호출이됨

초기 마운트단계에서 실행이되는 메소드이다.


### componentDidMount 

```js
componentDidMount() {
    //외부 라이브러리 연동 : slick , masonry 등
    //외부 api 호출, DOM에 관련된 작업 등
}

```

`componentDidMount()` 는 컴포넌트가 마운트된 직후, 즉 트리에 삽입된 직후에 호출된다. 
DOM 노드가 있어야하는 초기화 작업은 이 메서드에서 이루어지면된다. 또한 외부라이브러리와 연동에 axios나 fetch등을 이용하여 호출하는 작업도 주로 여기서 한다.



## 업데이트 단계

### shoudComponentsUpdate

```js
shouldComponentUpdate(nextProps, nextState){
    // return false 하면 업데이트를 안함
    return true;
    // 기본적으로 true를 반환
}

```

이 메서드는 컴포넌트를 최적화하기위해 많이 사용된다. 
리액트는 변화가 발생하는 부분만 업데이트를 해주기때문에 성능이 좋은편이다.
하지만 변화가 발생한 부분만 감지해내기 위해서는 Virtual DOM에 먼저 그린다.
컴포넌트에 무수히 렌더링된다면 부담이 커질수 있다. 그래서 Virtual DOM에 그려주는것 마저 줄여주기위해 이메서드를 사용한다.

### componentDidUpdate 

```js
componentDidupdate(prevProps, prevState, snapshot) {

}

```

이 API는 컴포넌트에서 render()를 호출하고 난 뒤에 발생한다.
이 시점에선 this.props와 this.state가 바뀌어있다.
그리고 파라미터를 통해 이전의 값 prevProps 와 prevState를 조회할 수 있다.

또한, `getSnapshotBeforeUpdate` 에서 반환한 snapshot 값은 세번째 값으로 받아온다.


## 언마운트 단계

### componentWillUnmount 

```js

componentWillUnmount() {
    // 이벤트 및 연동된 외부 라이브러리 제거
}

```

여기서는 주로 등록했었던 이벤트 및 연관 라이브러리 호출등을 제거한다. 




출처 : 
+ [https://ko.reactjs.org/docs/react-component.html#componentdidmount](https://ko.reactjs.org/docs/react-component.html#componentdidmount)
+ [https://react-nodejs-tutor.github.io/](https://react-nodejs-tutor.github.io/taling4th-coursebook/1d68c-cc28/lifecycle-api.html)
