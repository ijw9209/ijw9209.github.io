---
title: "JS ProtoType"
excerpt: "JS ProtoType"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-06T08:50:00
---


# 프로토 타입

JAVA , C++ 와 같은 클래스 기반 객체지향 프로그래밍 언어와 달리 JAVASCRIPT는 프로토타입 기반 객체지향언어이다.

클래스 기반 객체지향 프로그래밍 언어는 객체생성 이전에 클래스를 정의하고 이를 통해 객체(인스턴스)를 생성한다.
하지만 프로토타입기반 객체지향 프로그래밍 언어는 클래스없이도 객체를 생성할수 있다

## 1. 프로토 타입 ?

프로토타입(prototype)을 검색해보니 "원형"이라고 나온다.
말그대로 "객체의 원형"이라 할수있는데
생성자로 함수를 생성하면 1개의 생성자당 1개의 프로토타입이 생긴다.

풀어 얘기하면
생성자함수 > 하나의 객체 > 객체는 property를 가질수있음 > property중 하나가 Prototype

Constructor <ㅡㅡㅡㅡㅡㅡ> prototype    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(아빠/남편)      ㅣ         (엄마/아내)   <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;           ㅣ                       <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                 ㅣ                       <br/>    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                (자식)                   <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;              instance                   <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;          var o = new Child();           <br/>

예제와 위의 그림(?)을 보면 생성자(남편)과 프로토타입(아내)는 1명의 아빠가 있으면 1명의 아내를 가질 수 있다

예를 들어 Object 객체를 예를 들면
Object가 아빠가되고 Object는 객체이기때문에 Object.prototype 이라는 엄마의 속성도 가지고있다.

Constructor(아빠)가 존재하고 prototype(엄마)에게 .title이라는 프로퍼티가 있다고 가정해보자
instance(자식)은 prototype이라는 엄마의 속성으로 인해 .title 이라는 속성을 사용가능하다.

아래 예제로 보자면

```js
function AAA() {}
AAA.prototype.ParentProp = "안녕";

function BBB() {}
BBB.prototype = new AAA();

var o = new BBB();
document.write(o.ParentProp);  //result : 안녕
```

AAA() 라는 생성자 함수가 생겼고 거기에는 prototype이라는 아내가 있다

var o 라는 자식(isntance)가 prototype(엄마의) 속성을 이용하여 값을 가져올 수 있다.
그렇게 접근 가능한 이유는 BBB와 AAA가 연결 되어 있기 때문이다. 내부적으로는 이러한 방식으로 구동된다

- 1. 객체 o에서 ParentProp을 찾음
- 2. 없다면 BBB.prototype.ParentProp를 찾음
- 3. 없다면 AAA.prototype.ParentProp를 찾음

prototype은 객체와 객체를 연결하는 체인의 역할을 하고, 이러한 관계를 **prototype chain** 이라고 한다.

결론적으로 자바스크립트는 prototype을 통해서 상속을 제공하고 객체와 객체를 연결하고 ,객체의 변수 , 함수에 대한 정보를 prototype이라는 속성에 저장한다. 상속에서 부모 객체의 복제본을 만들어 그것을 상속하고 그것을 통해서 자식 객체의 내용을 바꾸면 부모와 자식간 내용이 달라진다.

- 나의 생각 : 맨처음엔 이해가 안가서 한참 찾았는데 설명들을 보다보니 적어도 어느정도는 이해가 갔다.
  하지만 지금은 큰틀만 이해한것같고 좀더 자세히 공부하여 내용을 좀더 보충해야 겠다.

참고자료

- 1. 생활코딩 [https://opentutorials.org/course/743/6573](https://opentutorials.org/course/743/6573)<br/>
- 2. 바닐라 코딩[https://www.youtube.com/watch?v=yXnbvyl04V4](https://www.youtube.com/watch?v=yXnbvyl04V4)
- 3. [http://www.nextree.co.kr/p7323/](http://www.nextree.co.kr/p7323/)
