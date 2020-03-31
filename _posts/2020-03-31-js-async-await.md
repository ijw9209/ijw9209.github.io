---
title: "JS 동기,비동기부터 ~ async-await까지"
excerpt: "JS 동기,비동기부터 ~ async-await까지"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-28T08:06:00-05:00
---

# 동기와 비동기

## 1. 동기와 비동기

동기란 코드가 위에서 아래로부터 자연스럽게 실행되는것
예시를 보면 순차적으로 위에서 아래로 작업이 끝날때마다 다음 작업을 실시한다.

```js
function sync1(){
    console.log(1);
}

function sync2(){
    console.log(2);
}

function sync3(){
    console.log(3);
}

sync1();
sync2();
sync3();
// 1
// 2
// 3
```

위 코드는 실행 순서대로 1, 2, 3을 출력합니다. 흐름이 위에서 아래로 동기적이다.

```js
function async1(){
    setTimeout(function(){
        console.log(1)
    }, 1000)
}

function sync2() {
    console.log(2)
}

function sync3(){
    console.log(3)
}

async1();
sync2();
sync3();
// 2
// 3
// 1

```

위의 예제는 async1을 먼저 실행해도 1이 마지막에 출력되고, 실행 흐름이 실행순서와 다르게 비동기적으로 실행됩니다. setTimeout함수가 1초 뒤로 실행을 지연시켰기 때문이다 

비동기는 서버에 요청을 주고 받을때나, 파일 입출력을 사용할때 실행된다.

## 2. 콜백 함수

아까 위의 예제를 순차적으로 1, 2, 3을 출력하게 하려면 초기 자바스크립트는 콜백 함수라는 방법을 사용했다


```js
function async1(cb){
    setTimeout(function () {
        console.log(1)
        cb()
    }, 1000)
}

function sync1(cb) {
    console.log(2)
    cb()
}

function sync2() {
    console.log(3)
}

async1(function(asyncResult) {
    sync1(function(syncReuslt) {
        sync2();
    })
})

// 1
// 2
// 3

```

콜백 함수를 받아서 비동기적 작업 이후 콜백함수를 실행하도록 했다. 
비동기 함수가 return 하는 값이 있다면, 콜백함수의 파라미터로 전달된다.


## 3. callback hell

콜백 함수는 문제점이 있는데 비동기적인 작업이 길어질수록 콜백이 깊어진다.
또한 콜백 내 if문 분기와 에러 핸들링을 어렵게 한다


```js
function async1(cb) {
    setTimeout(function(){
        console.log(1)
        cb()
    },100)
}

// 중략

function async9(cb) {
    setTimeout(function(){
        console.log(9)
        cb()
    },100)
}

function async10(cb) {
    setTimeout(function(){
        console.log(10)
        cb()
    },100)
}

async1(function(result){
    async2(function(result){
        async3(function(result){
            async4(function(result){
                async5(function(result){
                    async6(function(result){
                        async7(function(result){
                            async8(function(result){
                                async9(function(result){
                                    async10(function(result){
    
                                    })
                                })
                            })
                        })
                    })  
                })                
            })
        })
    })
})
// 1 2 3 4 5 6 7 8 9 10
```

## 4. Promise

콜백 지옥을 해결하기위해 Promise 패턴이 등장했다. 비동기 작업을 콜백이 아닌 then으로 연결하고, catch로 에러 핸들링을 편하게 할 수 있다.

```js

function async1() {
    return new Promise(function (resolve) {
        setTimeout(function(){
            console.log(1)
            resolve();
        } , 300)
    })
}

function async2() {
    return new Promise(function (resolve) {
        setTimeout(function(){
            console.log(2)
            resolve();
        } , 100)
    })
}

function async3() {
    return new Promise(function (resolve) {
        setTimeout(function(){
            console.log(3)
            resolve();
        } , 100)
    })
}

async1();
async2();
async3();

//2 3 1
```

Promise 패턴을 사용하기 위해서는 return new Promise()로 Promise() 객체를 반환해야한다 Promise 객체는 then과 catch 함수를 가진다


```js
async1()
    .then(function(result) {
        return async2()
    })
    .then(function(result) {
        return async3()
    })
    .catch(function(error) {
        console.log(error) // promise 체이닝 과정중에 에러가 발생하면 catch에 잡힘
    })
    // 1 2 3 
```

Promise 객체는 then 함수를 가지고 있다. then을 이용해 콜백을 대체하고
콜백과 마찬가지로 then 함수의 파라미터로 결과값을 전달할 수 있다.

이처럼 Promise의 then 체이닝을 이용해 비동기 작업을 컨트롤 할 수 있다.


## 5. Promise hell


```js

async1() {
    .then(function(result) {
        if(result === 'A') {
            return asyncSuccess()
        }
        return async2()
    })
    .then(function() {
        return async3()
    })
    .then(function() {
        return async4()
    })
    .then(function() {
        return async5()
            .catch(function(specificError){
                console.log(specificError)
            })
    })
    .then(function() {
        return async6()
    })
    .then(function() {
        return async7()
    })
    .catch(function(error) {
        console.log(error)
    })
}


```

promise 패턴도 만능은 아니다. 잘못사용하면 then이 깊어지며 if문 분기와 특정 에러 핸들링은 여전히 어렵다. 또한 코드가 then 체이닝에 갇혀야 한다.

## 6. Async await

이를 해결하기위해 async await가 ES7에 등장했다

```js
async function async1() {   // 함수 앞에 async 키워드가 붙는다.
    return 1
}

console.log(async1() instanceof Promise) // async 함수는 무조건 Promise 객체를 반환한다
const asyncReturn = async1()
asyncReturn.then() // 따라서 async 함수의 리턴값에도 then이 있다

```

async 함수 내부에서 await를 사용할 수 있다.

```js
function async1() {
    return new Promise(function (resolve) {
        setTimeout(function() {
            resolve(111)
        } , 300)
    })
}

async function async1() {
    const result = await async1()
    //await 키워드로 다른 promise를 반환하는 함수의 실행 결과값을 변수에 담는다 
    console.log(result) // 111
}

async function async2() {
    let result
    try {
        result = await async1()
    } catch(error) {    // await에서 발생한 에러는 모두 아래 catch 블록에 걸린다
        console.log(error)
    }
    if(result === 'AAA'){   // if문 분기도 일반 동기함수처럼 작성가능
        doSomething()
    }
    return result
}

```

async 함수 내부에선 await를 사용해 마치 동기적으로 코드를 작성 할 수 있다.
에러 핸들링과 if문 분기 또한 동기적으로 작성가능 에러 스택 추적도 용이,
async 함수의 반환값은 항상 promise 객체이다.


출처 : 
+ [https://velog.io/](https://velog.io/@ashnamuh/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%9C%EB%B0%B1%EB%B6%80%ED%84%B0-async-await%EA%B9%8C%EC%A7%80-%EB%B9%84%EB%8F%99%EA%B8%B0-%EC%B2%98%EB%A6%AC)
