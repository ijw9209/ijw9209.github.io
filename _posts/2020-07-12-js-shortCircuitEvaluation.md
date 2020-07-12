---
title: "[JS] 단축 평가 논리 계산법(short-circuit evaluation)"
excerpt: "[JS] 단축 평가 논리 계산법(short-circuit evaluation)"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-07-12T08:06:00-05:00
---

# 단축 평가 논리 계산법(short-circuit evaluation)

단축 평가 논리 계산법은 논리 연산자를 조금 더 유용하가게 사용하는 방법이다
우리는 연산자를 다음과 같이 사용하였다

```js
true && true // true
true && false // false
true || false // true 
false || true // true 

```
논리 연산자를 사용할 때 무조건 우리는 true or false의 값을 사용해야 되는 것은아니다. 문자, 숫자, 객체를 사용 할 수 잇고, 해당 값이 Truthy 하나 Falsy 하냐에 따라 결과가 달라질 수 있다

예를 들어 다음과 같은 코드가 있다고 가정하면

```js
const dog = {
    name = '멍멍이';
};

function getName(animal) {
    return animal.name;
}

const name = getName(dog);
console.log(name); //멍멍이

```

그런데 만일 getName의 파라미터에 제대로된 객체가 주어지지 않으면 어떻게 될까?


```js
const dog = {
    name : '멍멍이'
};

function getName(animal) {
    return animal.name;
}

const name = getName();
console.log(name);
```

animal 객체가 undefined 이기 때문에, undefined 에서 name 값을 조회 할 수 없어서 에러가 난다.
그렇다면, 만일 함수에서 animal 값이 제대로 주어졌을 때만 name을 조회하고, 그렇지 않을때는 그냥 undefind를 반환하게 하고 싶으면 어떻게 해야할까?


```js
const dog = {
    name : '멍멍이'
};

function getName(animal) {
    if(animal) {
        return animal.name;
    }
    return undefined;
}

const name = getName();
console.log(name);

```

이렇게 하면 animal 값이 주어지지 않아도, 에러가 발생하지 않게 된다.
이러한 코드를 논리 연산자를 사용하면 코드를 단축시킬 수 있다.

## && 연산자로 코드 단축시키기

이렇게 코드를 작성해 보면

```js
const dog = {
    name : '멍멍이'
};

function getName(animal){
    return animal && animal.name;
}

const name = getName();
console.log(name) //undefined

```

아까 위의 코드와 똑같이 작동하는 코드이다. 한번 다음과같이 파라미터를 넣어 호출도 해보면


```js
const dog = {
    name = '멍멍이'
};

function getName(animal){
    return animal && animal.name;
}

const name = getName(dog);
console.log(name);  // 멍멍이

```

이렇게 작동하는 이유는 A && B 연산자를 사용하게 될 때에는 A 가 Truthy 한 값이라면 , B가 결과값이 된다. 반면
A 가 Falsy 한 값이라면 결과는 A가 된다.

다음의 예시들을 보면

```js
console.log(true && 'hello'); // hello
console.log(false && 'hello'); // false
console.log('hello' && 'bye'); //bye
console.log(null && 'hello'); // null
console.log(undefined && 'hello'); //undefined
console.log('' && 'hello'); // ''
console.log(0 && 'hello'); // 0
console.log(1 && 'hello'); //hello
console.log(1 && 1 ); // 1

```

이러한 속성을 잘 알아두면, 특정 값이 유효할 때에만 어떤 값을 조회하는 작업을 해야할때 매우 유용하다


## || 연산자로 코드 단축시키기

|| 연산자는 만약 어떤 값이 Falsy 하다면 대채로 사용 할 값을 지정해줄 때 매우 유용하게 사용할 수 있다.

예를 들어 다음과 같은 코드가 있다고 가정해보면

```js
const namelessDog = {
    name : ''
};

function getName(animal) {
    const name = animal && animal.name;
    if(!name) {
        return '이름이 없는 동물입니다';
    }
    return name;
}

const name = getName(namelessDog);
console.log(name); // 이름이 없는 동물입니다.

```

위 코드는 || 연산자를 사용하면 다음과 같이 단축 시킬수 있다.

```js
const namelessDog = {
    name : ''
};


function getName(animal) {
    const name = animal && animal.name;
    return name || '이름이 없는 동물입니다';
}

const name = getName(namelessDog);
console.log(name); //이름이 없는 동물입니다.

```

A || B 는 만약 A 가 Truthy 할 경우 결과는 A가 됩니다. 반면, A가 Falsy 하다면 결과는 B가 된다. 

출처 : 

+ [https://learnjs.vlpt.us/useful/03-short-circuiting.html](https://learnjs.vlpt.us/useful/03-short-circuiting.html)