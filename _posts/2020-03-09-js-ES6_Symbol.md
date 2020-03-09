---
title: "[ES6] Symbol"
excerpt: "Symbol"
toc: true
toc_sticky: true

categories:
  - js
  - ES6
tags:
  - js
  - ES6
last_modified_at: 2020-03-09T08:06:00-05:00
---

# Symbol

심볼(symbol)은 ES6에서 새롭게 추가된 7번째 타입으로 변경 불가능한 원시 타입의 값이다. 심볼은 주로 이름의 충돌 위험이 없는 유일한 객체의 프로퍼티 키(property key)를 만들기 위해 사용한다.

-- Primitive Value --<br>

|데이터타입|참조형여부|
|------|---|
|String|x|
|number|x|
|boolean|x|
|null|x|
|undefined|x|
|**Symbol**|x| <<기본형 데이터에 새로추가



-- Reference Value  ---

|데이터타입|참조형여부|
|------|---|
|object|o|
|array|o|
|function|o|
|Map|o|
|Set|o|
|WeakMap|o| 
|WeakSet|o|
|TypedArray|o|
|ArrayBuffer|o| 

Symbol
+ Primitive Value == > 유일무이하고 고유한존재
+ 암묵적 형변환 불가
+ 기본적인 열거대상에서 제외

```js

//원래는 암묵적 형변환이가능하다
console.log('a' + 1)
// "a1"
console.log(true + 1)
// 2

//Symbol()은 형변환 불가!!
console.log(Symbol() + 1)

const a = Symbol()
const b = Symbol()

console.log(a === b)    //false
console.log(a == b)     //false
// 완전히 다른 값이라 비교자체가 불가

```
Symbol()에는 네이밍을 할당할 수 있는데 그렇게 해도 false가 나온다

```js
const a = Symbol('a')
const b = Symbol('a')

console.log(a)
//Symbol(a)

console.log(b)
//Symbol(a)

console.log(a === b)
//false

console.log(a == b)
//false
```

# Symbol 객체 접근 방법

```js
const x = () => {
    const a = Symbol('a');
    return {
        [a]: 10
    }
}
const y = x();

console.log(y);
// {Symbol(a) : 10}

// 이렇게는 Symbol(a)에 접근안됨
console.log(y.a)
console.log(y['a'])
console.log(y[Symbol('a')])

```

가능한 방법은 a라는 변수에 접근할수 있어야함

```js

const x = () => {
    const a = Symbol('a');
    return {
        [a]: 10,
        a: a
    }
}

console.log(y.a)
// Symbol(a)
console.log(y[y.a])
// 10


```

+ Symbol()은 new 연산자 사용불가

심벌을 객체의 프로퍼티에 키로할때는 대괄호표기법을 사용
```js
const NAME = Symbol('이름')
const GENDER = Symbol('성별')
const iu = {
    [NAME]: '아이유',
    [GENDER]: 'female',
    age: 26
}
const suzi = {
    [NAME]:'수지',
    [GENDER]:'female',
    age: 26
}
const jw = {
    [NAME]: '재웅',
    [GENDER]:'male',
    age : 29
}
console.log(iu ,suzi, jw)
//{age: 26 , Symbol(이름):"아이유" , Symbol(성별):"female"}
//{age: 26 , Symbol(이름):"수지" , Symbol(성별):"female"}
//{age: 29 , Symbol(이름):"재웅" , Symbol(성별):"male"}

console.log(iu[NAME], suzi[NAME],jw[NAME]);
// 아이유 수지 재웅

// for in 문을 돌린다면 
console.log(const prop in iu){
    console.log(prop, iu[prop])
}
// age만 나온다  > result age 26

// 그래서 세가지값 모두 접근할 수 있는 방법이 Reflect.ownKeys()
Reflect.ownKeys(iu).forEach(k => {
    console.lo(k , iu[k])
})
// age 26
// Symbol(이름) "아이유"
// Symbol(성별) "female"
```