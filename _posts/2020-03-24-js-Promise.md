---
title: "JS Promise"
excerpt: "Promise"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-24T08:06:00-05:00
---


# Promise


Promise는 비동기 연산이 종료된 이후의 결과값이나 실패 이유를 처리하기위한 처리기로 연결 해줌, 프로미스를 사용하면 비동기 메서드에서 마치 동기 메소드 처럼 값 반환 가능, 다만 최종 결과를 반환하지는 않고, 대신 Promise를 반환



![image](https://mdn.mozillademos.org/files/8633/promises.png)



```js

var _promise = function (param) {
    return new Promise(function (resolve, reject) {

        //비동기를 표현하기 위해 setTimeout 함수를 사용
        window.setTimeout(function () {

            //파라메터가 참이면
            if (param) {
                //성공했다면 resolve에 객체를 넣어줌
                resolve("해결완료");
            }

            //파라메터가 거짓이면,
            else {

                //실패하면 error를 발생하여 reject 객체에 넣어줌 
                reject(Error("실패"));
            }


        }, 3000);
    })
}

//promise 실행
_promise(true)
    .then(function (text) {
        //성공시
        console.log(text);
    }, function (error) {
        //실패시
        console.error(error);
    });

```

Promise는 다음 중 하나의 상태를 가짐.

+ 대기(pending): 이행하거나 거부되지 않은 초기 상태.
+ 이행(fulfilled): 연산이 성공적으로 완료됨.
+ 거부(rejected): 연산이 실패함.
+ settled : 연산을 성공하든 실패하든 일단 결론이 난 상태


**promise 선언부**

```js

var _promise = function (param) {
    return new Promise(function (resolve, reject) {

        //비동기를 표현하기 위해 setTimeout 함수를 사용
        window.setTimeout(function () {

            //파라메터가 참이면
            if (param) {
                //성공했다면 resolve호출
                resolve("해결완료");
            }

            //파라메터가 거짓이면,
            else {

                //실패하면 error를 발생하여 reject호출
                reject(Error("실패"));
            }


        }, 3000);
    })
}

```

위의 Promise 선언부를 보면 , 나중에 Promise 객체를 생성하기 위해 Promise 객체를 리턴하도록 함수를 감싸고 있다. Promise 객체만 보면 파라메터로 익명함수를 담고있고, 익명함수는 resolve 와 reject를 파라메터로 받고있다.

new Promise로 Promise가 생성되는 직후부터 resolve나 reject가 호출되기 전까지의 순간을 pending 상태라 한다.
이후 비동기 작업을 마친뒤 결과물을 성공적으로 수행했으면 resolve함수를 호출하고
실패했다면 reject를 호출하는것이 promise의 주요 개념이다.

위의 예제는 비동기 작업을 시뮬레이션 하기위해 setTimeout함수를 사용함


**promise 실행부**

```js
_promise(true)
.then(function(text){
    //성공시
    console.log(text);
}, function(error){
    //실패시
    console.error(error);
})

```

실행부는 더욱 심플 _promise()를 호출하면 Promise객체가 리턴된다. Promise 객체에는 정상적으로 비동기 작업이 완료 되었을때 호출하는 then 이라는 API가 존재.
위의 예제는 하나의 then API를 호출해서 비동기 작업이 완료되면 결과에 따라 성공 혹은 실패 메세지를 콘솔로그로 찍어줌

then API는 첫번째 파라메터에 성공시 호출할 함수 , 두번째 파라메터에 실패시 호출할 함수를 선언하면 Promise의 상태에 따라 수행


### 에러를 잡는 Promise.catch API

만약 체이닝형태로 연결된 상태에서 비동기 작업이 중간에 에러가 나면 어떻게 처리할까?
그때를 위해 존재하는 API가 catch API이다. .then(null ,function(){}) 을 메서드 형태로 바꾼거라 생각해도 좋다.

```js
_promise(true)
    .then(JSON.parse)
    .catch(function (){
        window.alert('체이닝 중간에 에러가!!');
    })
    .then(function(text)){
        console.log(text)
    });

```

위의 예제는 성공 혹은 실패시 JSON 객체가 아닌 String을 리턴하므로 JSON.parse 에서 에러가 나게된다. 그래서 다음 then으로 이동하지 못하고 catch에 잡히게된다 
catch는 이러하게 에러를 잡아주는 역할을한다.