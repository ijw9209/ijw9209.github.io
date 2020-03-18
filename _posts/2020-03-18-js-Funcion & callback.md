---
title:  "JS 함수와 콜백"
excerpt: "JS Functio & callback"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-18T08:06:00-05:00
---


# 값으로서의 함수와 콜백

자바스크립트에서는 함수도 객체다 . 다시말해서 일종의 값이다. 
자바스크립트 함수가 다른언어와 다른점은 함수가 일종의 **값**이 될 수 있다는 점이다.

```js
function a() {}

//var a = function(){}
```

위 예제에서 함수 a는 변수 a에담겨진 값이다. 또한 함수는 객체의 값으로 포함될 수 있다.
이렇게 객체의 속성값으로 담겨진 함수를 메소드(method)라고 부른다.

```js
a = {
    b:function(){
    }
};
// a 라는 변수 안에 담겨있는 객체안에 메소드 b가 있다.
// function : 값 
// b : 변수 , key
```


함수는 값이기 때문에 다른 함수의 인자로 전달 될 수도 있다. 아래예제를 보자
```js
function cal(func , num){
    return func(num);
}

function increase(num){
    return num+1;
}
function decrease(num){
    return num-1;
}
alert(cal(increase , 1));
alert(cal(decrease , 1));
```

함수 cal은 첫번째 인자로 전달된 increase를 실행하는데 이 때 두번째 인자의 값이 1을 인자로 전달한다. increase 는 계산된 결과를 리턴하고 다시 cal이 그 값을 리턴함


함수는 함수의 리턴 값으로도 사용할 수 있다.

```js
function cal(mode){
    var funcs = {
        'plus' : function(left , right) {return left + right},
        'minus' : function(left, right) {return left = right}
    }
    return funcs[mode];
}

alert(cal('plus')(2,1));
alert(cal('minus')(2,1));
```

당연히 배열의 값으로도 사용할 수 있다.

```js
var process = [
    function(input) {return input + 10},
    function(input) {return input * input},
    function(input) {return input / 2}
]
var input = 1;
for(var i = 0; i < process.length; i++){
    input = process[i](input);
}
alert(input);   // 60.5
```

## 콜백

**콜백(Callback)**은 **다른 코드의 인수로서 넘겨주는 실행 가능한 코드**를 말한다.
콜백을 넘겨 받는 코드는 이 콜백을 필요에 따라 즉시 실행할 수도 있고,아니면 나중에 실행할 수도있다

### 처리의 위임

값으로 사용될 수 있는 특성을 이용하면 함수의 인자로 전달할 수 있다. 값으로 전달된 함수는 호출 될 수 있기 때문에 이를 이용하면 함수의 동작을 완전히 바꿀 수 있다. 인자로 전달된 함수 sortNumber에 따라서 sort의 동작방법이 완전히 바뀌게 된다.

```js
function sortNumber(a, b){
    return b-a;
}
var numbers = [20, 10, 9,8,7,6,5,4,3,2,1];
alert(numbers.sort(sortNumber)); // array, [20,10,9,8,7,6,5,4,3,2,1]
```

### 비동기처리 

콜백은 비동기 처리에서 유용하게 사용된다. 비동기처리는 **특정 로직의 실행이 끝날 때까지 기다려주지 않고 나머지 코드를 먼저 실행하는 것이 비동기 처리**이다.
시간이 오래걸리는 작업이 있을때 이작업이 완료된 후에 처리해야 할 일을 콜백으로 지정하면 해당 작업이 끝났을때 미리 등록한 작업을 실행하도록 할 수 있다. 다음 코드는 서버환경에만 동작한다.

datasource.json.js
```js
{"title":"JavaScript","author":"egoing"}
```

demo1.hmtl

```html
<!DOCTYPE html>
<html>
<head>
<script src="//code.jquery.com/jquery-1.11.0.min.js"></script>
</head>
<body>
<script type="text/javascript">
    $.get('./datasource.json.js', 
        //이 함수가 콜백
        function(result){
        console.log(result);
    }, 'json');
</script>
</body>
</html>
```

+ [생활코딩](https://opentutorials.org/course/743/6508)