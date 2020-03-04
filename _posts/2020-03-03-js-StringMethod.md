---
title: "JS StringMethod"
excerpt: "JS StringMethod"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-03T08:50:00
---

# JavaScirpt String Method

## 1. String Length

**length** 속성은 String의 길이를 리턴한다

```js
var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
var sln = txt.length;
//return 26
```

## 2. Finding a String in a String (문자열에서 문자열찾기)

**indexOf(검색할 값 , 시작위치)** - 앞에서부터 검색할 값을 찾기 시작

시작위치가 생략될 경우 처음부터 시작

결과값이 없을 경우 -1

**lastIndexOf(검색할 값 , 시작위치)** - 끝에서부터 검색할 값을 찾기 시작

시작위치가 생략될 경우 맨 끝에서부터 시작

결과값이 없을 경우 -1

```js
var str = "이체할 금액 300원 , 이체한 금액 300원";

alert(str.indexOf("3"));
// 7

// indexOf 는 처음부터 검색을 시작하기 때문에 처음 발견된 3의 위치를
// Return- 7

alert(str.indexOf("3", 10));
// 21

// 시작위치가 10이기 때문에 "원" 다음부터 오른쪽으로 검색을 시작해서
// 처음 3을 건너 뛰고 두번째 발견된 3의 위치를
// Return - 21

alert(str.lastIndexOf("3"));
// 21

// lastIndexOf는 끝에서부터 검색을 시작하기 때문에 처음 발견된 3의 위치를
// Return - 21

alert(str.lastIndexOf("3", 10));
// 7

// 시작위치가 10이기 때문에 "이" 다음부터 왼쪽으로 검색을 시작해서

// 처음 3을 건너 뛰고 두번째 발견된 3의 위치를
// Return - 7

alert(str.lastIndexOf("5"));
// -1

// 일치하는 문자가 없기 때문에 -1을 Return
```

## 3. Extracting String Parts(문자열에서 부분 추출하기)

아래 3개의 메소드는 문자열을 추출할수 있다

- slice(start, end)
- substring(start, end)
- substr(start, length)

### 3-1. slice() 메소드

**slice(시작위치 , 종료위치)** 간단히말하면 특정위치를 주고 그부분만을 자를수 있다

```js
var str = "Apple, Banana, Kiwi";
var res = str.slice(7, 13);

//result Banana
//최초의 위치는 0이다.
```

파라미터가 음수이면 , 위치는 문자열의 끝부터 카운트된다.

```js
var str = "Apple, Banana, Kiwi";
var res = str.slice(-12, -6);
//result Banana
```

두번째 매개변수를 생략하면 문자열의 나머지부분을 자른다.

```js
var res = str.slice(7);
//result Banana, Kiwi

//or 끝에서 계산
var res = str.slice(-12);
//result Banana, Kiwi
```

### 3-2 The substring() 메소드

**substring()**은 slice()메소드와 유사하다

**substring()**의 차이점은

- start가 stop보다 크면 자리를 바꾼다.
- start나 stop이 음수이거나 NaN이면 0을 사용한다.

```js
var str = "Apple, Banana, Kiwi";
var res = str.substring(7, 13);

//result Banana
```

두번째 매개변수를 생략하면 substring()의 나머지 부분을 자른다

### 3-3 substr() 메소드

**substr()**도 slice() 메소드와 유사하다

차이는 두번째 넣는값에 길이를 넣는다

```js
var str = "Apple, Banana, Kiwi";
var res = str.substr(7, 6);

//result Banana
```

두번째 매개변수를 생략하면 나머지부분을 자른다

```js
var str = "Apple, Banana, Kiwi";
var res = str.substr(7);

//result Banana
```

첫 번째 매개 변수가 음수이면 문자열의 끝에서부터 위치가 계산

```js
var str = "Apple, Banana, Kiwi";
var res = str.substr(-4);

//result Kiwi
```

세가지 메소드의 차이점

- slice(begin [,end])
- substring(from[,to])
- substr(start [,length])

**slice()**는 시작부터 끝
**substring()**은 slice()와 비슷하지만 시작점이 0보다 작은경우 조금 다른 결과.
**substr()**은 시작부터 길이.

## 4. Replaceing String Content (문자열의 내용 교체)

**replace()** 메소드는 특정한값을 또다른 값으로 대체한다

```js
str = "Please visit Microsoft!";
var n = str.replace("Microsoft", "W3Schools");

// result Microsoft >> W3Schools
```

**replace()**메소드는 첫번째 로 맞는 글자를 바꾸어준다

```js
str = "Please visit Microsoft and Microsoft!";
var n = str.replace("Microsoft", "W3Schools");

//before Please visit Microsoft and Microsoft!
//result Please visit W3Schools and Microsoft!
```

또한 **replace()**메소드는 대,소문자를 구분한다

```js
str = "Please visit Microsoft!";
var n = str.replace("MICROSOFT", "W3Schools");
//안바뀜
```

행여나 교체하려면 정규표현식을 /i 플래그와사용하면된다

```js
str = "Please visit Microsoft!";
var n = str.replace(/MICROSOFT/i, "W3Schools");
```

모든걸 변경하려면 /g 를 사용하면 된다.

```js
str = "Please visit Microsoft and Microsoft!";
var n = str.replace(/Microsoft/g, "W3Schools");
//result Please visit W3Schools and W3Schools!
```

## 5. 대소문자로 변환

대문자는 **toUpperCase()** 를 사용하면된다.

```js
var text1 = "Hello World!"; // String
var text2 = text1.toUpperCase(); // text2 is text1 converted to upper

//result : HELLO WORLD!
```

반대로 **toLowerCase()**는 소문자로 반환된다

```js
var text1 = "Hello World!"; // String
var text2 = text1.toLowerCase(); // text2 is text1 converted to lower

//result : hello world!
```

## 6. CONCAT() 메서드

**CONCAT()** 메서드는 두개이상의 문자열을 조인한다

```js
var text1 = "Hello";
var text2 = "World";
var text3 = text1.concat(" ", text2);

//result : Hello World!
```

concat()방법 대신 덧셈 연산자를 사용 할 수 있다.

```js
var text = "Hello" + " " + "World!";
var text = "Hello".concat(" ", "World!");
```

## 7.Stirng.trim()

**trim()** 은 문자열의 양쪽의 공백을 제거할 수 있다.

```js
var str = "       Hello World!        ";
alert(str.trim());

//result : Hello World!
```

## 8. Extracting String Characters

3개의 메소드는 문자열의 문자를 추출할수 있다

- charAt(position)
- charCodeAt(position)
- Property access [ ]

### 8-1 The charAt() Method

**charAt()** 메서드는 문자열에서 지정된 인덱스(위치)에 있는 문자를 보여줌

```js
var str = "HELLO WORLD";
str.charAt(0);

//return H
```

### 8-2 charCodeAt () Method

charCodeAt()메서드는 문자열에서 지정된 인덱스에있는 문자의 유니 코드를 반환합니다

```js
var str = "HELLO WORLD";

str.charCodeAt(0); // returns 72
```

### 8-3 Property access [ ]

ECMAScript 5 에 문자열 속성 액세스

```js
var str = "HELLO WORLD";
str[0];

//return H
```

속성엑세스는 읽기전용이며 , Internet Explorer 7 이전에 브라우저에선 작동하지 않는다

```js
var str = "HELLO WORLD";
str[0] = "A"; // Gives no error, but does not work
str[0]; // returns H
```

## 9. 문자열을 배열로 변환 split()

**split()**메서드는 문자열을 배열로 변환 할 수 있다 .

```js
var txt = "a,b,c,d,e"; // String
txt.split(","); // Split on commas
txt.split(" "); // Split on spaces
txt.split("|"); // Split on pipe
```

separator 가 생략되면 하나의 배열에 모든문자가 들어갈것이다 그배열의 인덱스는 0만 존재한다 .
separator가 "" 이면 반환될 배열은 단일문자 배열이다

```js
var txt = "Hello";
txt.split("");

//result [H,E,L,L,O]
```

공부후 느낀점 :
자바에서도 한번 배웠었는데 쓰임새는 비슷한것같다.
하지만 보면서도 이게뭐였지 하는 것들이 있었다.
공부하면서 다시한번 생각날 수 있었고 , 좀더 편리하게 사용할 수 있을것같다.

- [https://devjhs.tistory.com/79](https://devjhs.tistory.com/79)
