---
title: "JS 이벤트 위임"
excerpt: "JS 이벤트 위임"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-04-09T08:06:00-05:00
---


# 이벤트 위임

## 이벤트 버블링과 캡쳐링

이벤트 위임을 알기 위해선 선수지식으로 이벤트 버블링과 캡쳐링의 동작방식을 알아야 한다. 

이벤트 버블링 : 하위 엘리먼트에 이벤트가 발생할 때 그 엘리먼트부터 시작해서 상위요소까지 이벤트가 전달되는 방식을 말한다.

이벤트 캡쳐링 : 하위 엘리먼트에 이벤트 핸들러가 있을 때 상위 엘리먼트부터 이벤트가 발생하여 하위까지 이벤트가 전달되는 방식을 말한다.

```html
<div>
    <ul>
        <li>예시</li>
    </ul>
</div>
```

```js
document.querySelector('li').addEventListener('click',() => console.log('li클릭!'));
document.querySelector('ul').addEventListener('click',() => console.log('ul클릭!'));
document.querySelector('div').addEventListener('click',() => console.log('div클릭!'));

//li 클릭
//ul 클릭
//div 클릭
```

li태그를 클릭해보면 콘솔이 위와 같이 찍힌다

기본적으론 동작방식이 "이벤트 버블링"이다. 이방식을 이벤트 캡쳐링으로 바꾸기 위해선 `addEventListener()`의 마지막 인자로 `{capture : true}`를 전달해 주면된다. 이렇게 하면 클릭한 엘리먼트의 상위 요소중 이벤트 캡쳐링이 적용된 엘리먼트부터 콘솔에 찍히고 그 다음 부터는 다시 "이벤트 버블링" 방식을 동작한다. `ul`에 이벤트 캡쳐링을 적용해보자

```js
document.querySelector('ul').addEventListener('click' , () => console.log('ul클릭'), {capture : true});

//ul 클릭
//li 클릭
//div 클릭
```

`li` 부터는 다시 "이벤트 버블링"이 동작해서 `div`에 이벤트가 발생하는 것이다.


## 이벤트 위임

이벤트 위임 : 하위 엘리먼트들이 여러개 있을 때, 하위 엘리먼트들에 각각 이벤트 핸들러를 달지 않고 상위 엘리먼트에 이벤트 핸들러를 달아 하위 엘리먼트들을 제어하는 방식이다. 이 패턴으로 얻는 이점은 다음과 같다.

+ 동적으로 엘리먼트를 추가할 때마다 핸들러를 고려할 필요가 없다.
+ 상위 엘리먼트에 하나의 이벤트 핸들러만 추가하면 되기 때문에 코드가 훨씬 깔끔하다.
+ 메모리에 있게되는 이벤트 핸들러가 적어지기 때문에 퍼포먼스 측면에서 이점이 있다.

```js
<ul onClick="alert(event.type + '!')">
    <li>첫번째</li>
    <li>두번째</li>
    <li>세번째</li>
</ul>
```

`li`에 각각 핸들러를 달지 않고 상위 엘리먼트인 `ul`에만 달았다는걸 확인할 수 있다. 무조건 이벤트 위임이 좋은건 아니기때문에 상황에 맞게 잘 사용하자.

출처 : 

+ [https://github.com/baeharam/Must-Know-About-Frontend/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/event-delegation.md)