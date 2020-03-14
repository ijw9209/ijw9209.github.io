---
title:  "JS Closure(클로저)"
excerpt: "JS Closure(클로저)"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-14T08:06:00-05:00
---



# 클로저 

클로저(closure) 내부함수가 외부함수의 맥락(context)에 접근 할 수 있는것을 가르킨다.


## 내부함수

자바스크립트는 함수안에서 또 다른 함수를 선언 할 수 있다.

```js
//외부함수
function outter() {
    
    //내부함수
    function inner() {
    //var inner = function() 과 같음    
        var title = 'coding everybody';
        alert(title);
    }
    inner();
}
outter();
```

위의 예제에서 함수 ouuter의 내부에는 함수 inner가 정의. inner와 같은함수를 내부함수라고 하고, 내부함수는 외부함수의 지역변수의 접근 할 수 있다.

```js
function outter() {
    //외부함수의 지역변수 title
    var title = 'coding everybody';
    function inner(){
        alert(title);
    }
    inner();
}
outter();

```
위의 예제는 내부함수 inner에서 title을 호출했을때 outter(외부함수)의 지역변수에 접근가능한 것을 보여준다

## 클로저

클로저는 내부함수와 밀접한 관계를 가지고 있다. 내부함수는 외부함수의 지역변수에 접근할수 있고 외부함수의 실행이 끝나서 외부함수가 소멸된 이후에도 내부함수가 외부함수의 변수에 접근 할 수있다. 이러한 메커니즘을 **클로저** 라고 한다.

```js
function outter() {
    var title = 'coding everybody';
    return function() {
        alert(title);
    }
}
var inner = outter();
inner();    //coding everybody

```
함수 outter를 호출하여 변수 inner에 담는다 그 결과는 이름이 없는함수다. 실행이 inner();로 넘어오면 outter함수는 실행이 끝났기 때문에 이 함수의 지역변수는 소멸되는 것이 자연스럽다. 하지만 inner();를 실행했을때 "coding everybody"가 출력된것은 외부함수의 지역변수 title이 소멸되지 않았다는것을 의미한다

**클로저**란 내부함수가 외부함수의 지역변수에 접근 할 수 있고, 외부함수는 외부함수의 지역변수를 사용하는 내부함수가 소멸될때까지 소멸되지않는 특성을 의미한다.


```js
function factory_movie(title){
    return {
        get_title : function () {
            return title;
        },
        set_title : function(_title) {
            title = _title
        }
    }
}
ghost = factory_movie('Ghost in the shell');
matrix = factory_movie('Matrix')

alert(ghost.get_title()); //ghost in the shell 
alert(matrix.get_title());  //Matrix

ghost.set_title('공각기동대');

alert(ghost.get_title()); //공각기동대 
alert(matrix.get_title()); //Matrix

```
위의 예제를 정리해보면

1. 클로저는 객체의 메소드에도 사용할 수 있다. 위의 예제는 함수의 리턴값으로 객체를 반환하고 있다. 객체는 메소드 get_title과 set_title을 가지고있다. 이 메소드들은 외부함수인 factory_movie의 인자값으로 할당된 지역변수 title을 사용하고 있다.

2. 동일한 외부함수 안에서 만들어진 내부함수나 메소드는 외부함수의 지역변수를 공유한다. 실행된 set_title은 외부함수 factory_movie의 지역변수 title의 값을 '공각기동대로 변경했다. ghost.get_title();의 값이 '공각기동대'인 것은 set_title과 get_title함수가 title의 값을 공유한다는 의미이다.


3. 그런데 똑같은 외부함수 fatory_movie를 공유하고 있는 ghost와 matirx의 get_title의 결과는 서로각각 다르다. 그것은 외부함수가 실행 될때마다 새로운 지역변수를 포함하는 클로저가 생성되기 때문에 ghost와 matrix는 서로 완전히 독립된 객체가 된다.

4. factory_movie의 지역변수 title은 정의된 객체의 메소드에서만 접근 할 수 있는 값이다. 이 말은 title의 값을 읽고 수정 할 수 있는 것은 factory_movie 메소드를 통해서 만들어진 객체 뿐 이라는 것이다.
JavaScript는 기본적으로 private한 속성을 지원하지 않는데, 클로저의 이러한 특성을 이용해서 private한 속성을 사용할 수 있다.

```js
var arr = []
for(var i = 0; i < 5; i++) {
    arr[i] = function() {
        return i;
    }
}
for(var index in arr){
    console.log(arr[index]());
}
```

함수가 함수 외부의 컨텍스트에 접근할 수 있을것으로 기대하겠지만 위의 결과는 아래와같다 
5 , 5 , 5 , 5, 5

위의 코드는 아래와 같이 변경해야한다.

```js
var arr = []
for(var i = 0; i < 5; i++ ){
    arr[i] = function(id) {
        return function() {
            return id;
        }
    }(i);
}
for(var index in arr) {
    console.log(arr[index]);
}

// 결과 0 1 2 3 4
```

결론 : 내부함수가 외부함수의 지역변수의 접근할 수 있고, 외부함수가 소멸되어도 내부함수가 소멸될때까지 소멸되지 않는것이 **클로저**


클로저 참고
+ [https://opentutorials.org/course/743/6544](https://opentutorials.org/course/743/6544)
+ [https://developer.mozilla.org/ko/docs/JavaScript/Guide/Closures](https://developer.mozilla.org/ko/docs/JavaScript/Guide/Closures)
+ [http://ejohn.org/apps/learn/#48](http://ejohn.org/apps/learn/#48)
+ [http://blog.javarouka.me/2012/01/javascripts-closure.html](http://blog.javarouka.me/2012/01/javascripts-closure.html)