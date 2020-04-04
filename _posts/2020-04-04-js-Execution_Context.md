---
title: "JS 실행 컨텍스트(Execution Context)"
excerpt: "실행 컨텍스트(Execution Context)"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-04-04T08:06:00-05:00
---

# 실행 컨텍스트(Execution Context)


## 실행 컨텍스트란?

코드의 실행환경에 대한 여러가지 정보를 담고 있는 개념, 간단히 말하면 JS엔진에 의해 만들어지는 코드 정보를 담은 객체의 집합이다. 

## 종류

JS의 코드는 3가지 종류로 이루어진다. 

+ 글로벌 스코프 
+ 함수 스코프 
+ eval() 

위의 코드는 자신만의 실행 컨텍스트를 소유한다

엔진이 스크립트 파일을 실행하기전 글로벌 실행 컨텍스트(Global Execution Context,GEC)가 생성되고, 함수를 호출할때 마다 함수 실행 컨텍스트(Function Execution Context)가 생성된다. 주의 할 점은, GEC의 경우 이전에생성되지만 FEC는 호출할때 생성된다.

## 실행 컨텍스트 스택(Execution Context Stack)

실행 컨텍스트가 생성되면 흔히 콜 스택(Call Stack)이라고도 불리는 실행 컨텍스트 스텍에 쌓이게됨.
GEC는 코드를 실행하기전에 쌓이고, 모든 코드를 실행하면 제거된다. FEC는 호출할때 쌓이고 호출이 끝나고 리턴하게되면 제거된다

```js
function func() {
    console.log('함수 실행 컨텍스트');
}
console.log('글로벌 실행 컨텍스트');
func();
```

1. 처음 코드를 실행하기 전 GEC가 쌓이고 콘솔에 "글로벌 실행 컨텍스트" 출력
2. `func()`를 호출하고 그에대한 FEC가 만들어져 쌓임, FEC를 실행하여 콘솔에 "함수 실행 컨텍스트" 출력
3. `func()` 종료 뒤 FEC 스택에서 제거 후, 모든 코드가 실행종료되고 GEC가 스택에서 제거됨

## 구성 요소

실행 컨텍스트는 다음과 같은 구성요소를 갖는다

+ Lexical Environment
+ Variable Environment 
+ this 바인딩

### Lexical Environment

Lexical Environment는 변수 및 함수 등의 식별자(Identifier) 및 외부 참조에 관한 정보를 가지고 있는 컴포넌트이다. 이 컴포넌트는 2개의 구성요소를 갖는다

+ Environment Record 
+ outer 참조 

Environment Record가 식별자에 관한 정보를 가지고 있으며 outer 참조는 외부 Lexical Environment를 참조하는 포인터이다. 

```js
var x  = 10;
function foo() {
    var y = 20;
    console.log(x);
}

```
위와 같은 코드가 있을 때는 아래처럼 Lexical Environment가 형성된다.

```js
globalEnvironment = {
        environmentRecord = { x : 10},
        outer : null
}
fooEnvironment = {
        environmentRecord = { y : 20},
        outer : globalEnvironment
}

```

`foo()` 에서 x를 참조할 때는 Environment Record를 찾아보고 없기 때문에 outer 참조를 사용하여 외부의 Lexical Environment에 속해있는 Environment Record를 찾아보는 방식이다.

### Variable Environment 

Variable Environment는 Lexical Environment와 동일한 성격을 띄지만 var로 선언된 변수만 저장한다는 점에서 다르다. Lexical Environment는 var로 선언된 변수를 제외하고 나머지(let이나 함수선언문)을 저장한다.

### this 바인딩

this의 바인딩은 실행 컨텍스트가 생성될 때마다 this 객체에 어떻게 바인딩이 되는지를 나타낸 것이다. (ES6부터 thi의 바인딩은 LexicalEnvironment 안에 있는 EnvironmentRecord 안에서 일어나는 사실을 알고만 있자.)

+ GEC의 경우
    - strict mode라면 `undefined`로 바인딩된다
    - 아니면 글로벌 객체로 바인딩된다. (브라우저에선 window, 노드에선 global)
+ FEC의 경우
    - 해당 함수가 어떻게 호출되었는지에 따라 바인딩된다.

## 과정

EC는 2가지 과정을 거친다

1. Creaction Phase (생성단계)
2. Execution Phase (실행단계)


## 생성단계

생성단계는 다시 3단계로 나누어진다

1. Lexical Environment 생성
2. Variable Environment 생성
3. this 바인딩

주의할 점은 값이 변수에 매핑되지 않는다는 것이다. var의 경우는 undefined로 초기화되고 let 이나 const는 아무 값도 가지지 않는다


## 실행단계 

이제 코드를 실행하며 변수에 값을 매핑시킨다. 

```js
var a = 3;
let b = 4;

function func(num){
    var t = 9;
    console.log(a + b + num + t);
}

var r = func(4);
```

+ GEC의 생성 단계

여기서 생성이 될 때 실행 컨텍스트 스택에 쌓인다.

```js
GEC {
	ThisBinding: window,
	LexicalEnvironment: {
		EnvironmentRecord: {
			b: <uninitialized>,
			func: func(){...}
		},
		outer 참조: null
	},
	VariableEnvironment: {	
		EnvironmentRecord: {
			a: undefined,
			r: undefined
		},
		outer 참조: null
	}
}
```

+ GEC의 실행 단계

```js
GEC {
    ThisBinding: window,
	LexicalEnvironment: {
		EnvironmentRecord: {
			b: 4,
			func: func(){...}
		},
		outer 참조: null
	},
	VariableEnvironment: {
		EnvironmentRecord: {
			a: 3,
			r: undefined
		},
		outer 참조: null
	}
}

```

이제 `func()`를 호출하고 FEC를 생성한다.

+ FEC의 생성 단계

```js
FEC {
    ThisBinding : window,
    LexicalEnvironment : {
        EnvironmentRecord : {
            arguments : { num : 4, length : 1},
        },
        outer: GEC의 LexicalEnvironment
    },
    VariableEnvironment : {
        EnvironmentRecord : {
            t : undefined
        }, 
        outer : GEC의 LexicalEnvironment
    }
}

```

+ FEC의 실행 단계

```js
FEC {
	ThisBinding: window,
	LexicalEnvironment: {
		EnvironmentRecord: {
			arguments: { num: 4, length: 1 },
		},
		outer: GEC의 LexicalEnvironment
	},
	VariableEnvironment: {
		EnvironmentRecord: {
			t: 9
		},
		outer: GEC의 LexicalEnvironment
	}
}


```

FEC가 스택에서 제거되고 GEC의 r이 20으로 초기화된다.

```js



GEC {
	ThisBinding: window,
	LexicalEnvironment: {
		EnvironmentRecord: {
			b: 4,
			func: func(){...}
		},
		outer 참조: null
	},
	VariableEnvironment: {
		EnvironmentRecord: {
			a: 3,
			r: 20
		},
		outer 참조: null
	}
}

```

모든 코드를 실행하고 GEC가 스택에서 제거된 뒤 프로그램이 종료된다.

출처 : 
+ [https://github.com/baeharam/Must-Know-About-Frontend/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/javascript/execution-context.md)