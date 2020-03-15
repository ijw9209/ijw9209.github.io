---
title:  "JS 호이스팅(Hoisting)"
excerpt: "JS 호이스팅(Hoisting)"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-15T08:06:00-05:00
---

# hoisting(호이스팅)

## hoisting(호이스팅)?

호이스트란 변수의 정의가 그 범위에 따라 선언(declaration) / 초기화(initialization) / 
할당 분리 되는 것을 의미한다

쉽게 말하면 변수가 함수내에서 정의되었을경우 함수의 최상위로, 함수 바깥에서 정의 되었을 경우는 전역 컨텍스트의 최상위로 변경됨.

예제

```js
const hoisting = () => {
    console.log("First-Name:" , name);
    var name = "Marcus";
    console.log("Last-Name:",name);
}

hoisting();

//First Name : undefind
//Last Name : Marcus
```
First Name 이 undefined인 이유는 지역변수 name이 호이스트 되었기 때문이다.

위 hoisting이라는 함수는 자바스크립트로 이해하면 다음과 같다

```js
const hoisting = () => {
    var name;   // name 변수는 호이스트 됨 , 할당은 이후에 발생하기때문에 이시점의 name의 값은 undefiend이다.
    console.log("First name: " + name); //first name : undefind
    name = "Marcus";
    console.log("Last name : " + name); //Last name : Marcus

}

```

그럼 여기서 궁금한점은 let과 const에는 호이스팅이 될까?

위에서 작성한 예제를 let으로 바꿔보자

```js
const hoisting = () => {
    console.log("Name" ,name);
    let name = "Marcus";
}

hoisting();
// ReferenceError: name is not defined   
```

왜 let으로 했을때는 name is not defined에러가 발생할까?
앞서서는 **변수가 함수내에서 정의되었을 경우 선언이 함수의 최상위로, 함수 바깥에서 정의 되었을 경우는 전역 컨텍스트의 최상위로 변경된다** 라고 설명했다

위의 코드에서 let 변수에 접근이 불가능한 이유는 **Temporal Dead Zone(TDZ)**때문이다.

**즉, let과 const는 블록의 시작부터 초기화가 실행되기 전까지 TDZ에 존재하게 된다는것 TDZ에 존재하면 위와같이 접근을 할 수 없다.**

```js
//const TDZ를 실행하기전에 TDZ에 접근하면 , TDZ에 의해 ReferenceError 발생
console.log(TDZ);
//output : ReferenceError : TDZ is not defined

const TDZ = 'Temporal Dead Zone';
//위 코드 실행이후 TDZ에 접근가능
console.log(TDZ)
//output : Temporal Dead Zone

```

let/const 변수는 호이스팅 되지않는것이 아닌, 스코프에 진입할때 변수가 만들어지고, TDZ가 생성되지만 코드실행이 변수가 있는 실제위치까지 액세스할 수 없게됨.
let/const변수가 선언된 시점에서 제어흐름은 TDZ를 떠난상태가 되며, 변수를 사용할수 있음

출처 
+ [https://velog.io/@marcus/Javascript-Hoisting](https://velog.io/@marcus/Javascript-Hoisting)
+ [https://kimcoder.github.io/javascript/2018/09/17/tdz.html](https://kimcoder.github.io/javascript/2018/09/17/tdz.html)