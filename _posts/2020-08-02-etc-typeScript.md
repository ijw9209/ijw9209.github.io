---
title: "[TS] 1.타입스크립트 개요"
excerpt: "타입스크립트"
toc: true
toc_sticky: true

categories:
  - etc
  - typeScript
tags:
  - etc
  - typeScript
last_modified_at: 2020-08-02T08:06:00-05:00
---


# 타입스크립트 ? 

타입스크립트는 자바스크립트의 슈퍼셋이다. 자바스크립트의 기능 + 타입체크 기능까지
추가했기 때문에 타입스크립트는 자바스크립트 보다 더 큰 범주라고 할 수 있다.

타입스크립트를 쓰는 이유는 자바스크립트에서 발생할 수 있는 에러를 미리 방지해주기 때문이다

```js
function add(a , b){
    return a + b;
}

```
를 했을 때

```js
console.log(add("5", "10"));
```
을 해버리면 우리는 15라는 값을 원했는데 510이라는 값이 출력 될 것이다.  저것을 제대로 계산하게 하려면


```js
function add(a,b){
    if(typeof a === "number" && typeof b === "number"){
        return a + b;
    }else {
        return +a + +b;
    }
}
```

이런식으로 해야 한다. 코드도 길어지고 별로 코드가 깔끔하지 못하다. 변수 앞에 +를 붙여주면 number 타입으로 바뀐다. 타입스크립트를 적용하면

```js
function add(a: number , b: number ): number {
    return a + b;
}

```
와 같이 사용할 수 있다. 만약 a와 b에 number가 아닌 다른 타입의 값을 넣어주게 되면 IDE나 트랜스파일할 때 에러라고 알려준다! 이 타입스크립트의 장점이 또 IDE에서 함수나 타입, 메소드 지원등이 잘 된다는 것이다. 그래서

```js
const s = [1,2,3,4];
```
하고 `s.` 을 하면 배열의 메서드 들이 무엇이 있는지를 잘 알려준다. ㅡ런데 함수를 해당 변수로 넣어주게 되면 그게 안된다. 상당히 불편함

```js
function addArray(array){
        return array.reduce((result, current) => result + current, 0);
}

```

위와 같은 함수를 작성할때 `Array.reduce()`함수의 사용법이 기억나지않아 ctrl + space를 하면 메서드들이 나오지않아 인터넷을 찾아보거나 다른 코드에서 찾아보게된다. 이럴때 타입스크립트로 작성을 하면 무슨 메서드들이 있는지 잘 추론해준다


```js
function addAraay(array : number[]): number {
    return array.reduce((result , current) => result + current, 0); 
}

```

그 외에도 객체에 있는 key들도 잘 추론해내게 된다

하지만 브러우저나 node는 typescirpt를 실행시키지 못함
트랜스파일 한 다음에 실행시켜야한다. index.html 파일에 ts를 넣으면 안되고 트랜스 파일한 js파일을 넣어주어야한다.

타입스크립트를 사용해서 코드양이 늘어나고 타입들을 작성을 해줘야 해서 귀찮고 시간도 더 오래 걸릴 수 있지만, IDE를 더 효율적으로 사용할 수 잇고, 자신의 실수를 줄일 수 있고, 다른사람이 작성 해놓은 함수나 변수를 제대로 된 용도로 사용할 수 있다. 만약

출처 
+ [https://velog.io/@ansrjsdn/Typescript-타입스크립트란](https://velog.io/@ansrjsdn/Typescript-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%9E%80)