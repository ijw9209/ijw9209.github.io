---
title: "[ES6] spread 와 rest"
excerpt: "spread 와 rest"
toc: true
toc_sticky: true

categories:
  - js
  - ES6
tags:
  - js
  - ES6
last_modified_at: 2020-04-01T08:06:00-05:00
---

# spread 와 rest


## spread 

spread 문법은 펼치다 라는 의미의 문법이다.  이문법을 사용하면, 객체 혹은 배열을 펼칠 수 있다. 


```js
const slime = {
    name : '슬라임'
};

const cuteSlime = {
    name : '슬라임',
    attribute : 'cute'
}

const purpleCuteSlime = {
    name : '슬라임',
    attribute: 'cute',
    color : 'purple'
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);

```

위의 코드의 예제는 기존의 선언했던 객체를 건들지 않으면서 계속적으로 새로운 객체를 생성하였다. 이렇게 기존것과 상관없이 사용할 때 유용한것이 spread 문법이다.

```js
//spread 문법사용
const slime = {
    name : '슬라임'
};

const cuteSlime = {
    ...slime,
    attribute : 'cute'
};

const purpleCuteSlime = {
    ...cuteSlime,
    color: 'purple'
}

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);

```

... 이 spread문법이다. spread는 배열에서도 사용가능하다

```js
const animals = ['호랑이','악어','개'];
const anotherAnimals = [...animals, '비둘기' ]

console.log(animals);
console.log(anotherAnimals);

// [호랑이 , 악어 , 개]
// [호랑이 , 악어 , 개 , 비둘기]

```

기존 배열은 건드리지않으면서 새로운 another배열에 모두 넣고 비둘기라는 항목이 추가적으로 추가되었다.

spread 문법은 배열에서 여러번도 가능하다

```js
const numbers = [1,2,3,4,5];

const spreadNums = [...numbers, 1000 , ...numbers];

console.log(spreadNums);
// [1,2,3,4,5,1000,1,2,3,4,5]

```

## rest

rest의 생김새는 spread 문법과 비슷하지만 역할이 매우다르다.
rest는 객체 , 배열 , 그리고 함수의 파라미터에서 사용가능하다.

### 객체에서의 rest

우선 객체에서 예시를 알아보면

```js
const purpleCuteSlime = {
    name : '슬라임',
    attribute : 'cute',
    color : 'purple'
};

const {color , ...rest } = purpleCuteSlime;

console.log(color);
console.log(rest);
//purple
//{ name : 슬라임 , attribute : cute }
```

rest안에 color 값을 제외한 값 들이 들어왔다. 
rest는 객체와 배열에서 사용할때 이렇게 비구조화 할당 문법과 같이사용된다. 
추출한 값의 이름이 꼭 rest일 필요는 없다

```js

const purpleCuteSlime = {
    name : '슬라임',
    attribute: 'cute',
    color : 'purple'
};

const { color , ...cuteSlime } = purpleCuteSlime;
console.log(color);
console.log(cuteSlime);


```

이렇게 해도 무방하다. 만약 attribute까지 없앤 새로운 배열을 만들고싶다면

```js

const purpleCuteSlime = {
  name: '슬라임',
  attribute: 'cute',
  color: 'purple'
};

const { color , ...cuteSlime } = purpleCuteSlime;
console.log(color);
console.log(cuteSlime);

// purple
// { name : 슬라임 , attribute : cute }

const { attribute , ...slime } = cuteSlime; 
console.log(attribute);
console.log(slime);

// cute
// { name : 슬라임 }
```

### 배열에서의 rest

```js
const numbers = [0,1,2,3,4,5,6];

const [one, ...rest] = numbers;

console.log(one);
console.log(rest);
// 0 
// [1,2,3,4,5,6]
```

배열 비구조화 할당을 통해 원하는 값을 꺼내고 , 나머지를 rest안에 넣었다

반면에 이렇게하면 SyntaxError가 난다.

```js
const numbers = [0,1,2,3,4,5,6]

const [...rest , last] = numbers;
```


### 함수 파라미터에서의 rest

rest를 함수 파라미터에서 사용가능하다. 예를들어 파라미터로 넘겨준 모든 값들을 합해주는 함수를 만들어 주고싶다고 가정하면

```js
function sum(a,b,c,d,e,f,g){
    let sum = 0;
    if (a) sum += a;
    if (b) sum += b;
    if (c) sum += c;
    if (d) sum += d;
    if (e) sum += e;
    if (f) sum += f;
    if (g) sum += g;
    return sum;
}

const result = sum(1,2,3,4,5,6);
console.log(result);

```
위에서의 sum함수는 7개의 파라미터를 받아오지만 아래서는 6개의 값만을 넣어주었다. 마지막 g의 값은 undefiend가 되는데 sum을 더하는과정에서 undefined를 더하게되면 결과는 NaN이 되게된다. 

함수 파라미터가 몇개가 될지 모르는 상황에서 rest 파라미터를 사용하면 유용하게 사용할수 있다


```js
function sum(...rest){
    return rest;
}

const result = sum(1,2,3,4,5,6);
console.log(result);
// [1,2,3,4,5,6]
```
result에 들어있는 값은 함수에서 파라미터로 받아온 배열이다. 이제 이배열을 모두 더해주면된다.

```js
function sum(...rest) {
    return rest.reduce((acc, current) => acc + current , 0);
}

const result = sum(1,2,3,4,5,6);
console.log(result);

```

이렇게 편하게 사용할 수 있다.


출처 : 
+ [https://learnjs.vlpt.us/useful/07-spread-and-rest.html](https://learnjs.vlpt.us/useful/07-spread-and-rest.html)