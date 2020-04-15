---
title: "[JS] 프로그래머스 - 2016년"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-04T08:06:00-05:00
---

## 문제 


2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각 SUN,MON,TUE,WED,THU,FRI,SAT

입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 TUE를 반환하세요.

### 제한사항

+ 2016년은 윤년입니다.
+ 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)

## 나의 풀이

```js

solution = (a, b) => {

    let day = "2016-" + a + "-" + b;
    const week = ['SUN', 'MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT'];
    let answer = week[new Date(day).getDay()];

    return answer;
}

test('2016년', () => {
    expect(solution(5, 24)).toEqual("TUE");
})


```

### 다른사람의 풀이 1

```js

function getDayName(a,b){
    return new Date(2016,a-1,b).toString().slice(0,3).toUpperCase();
}

```

### 다른사람의 풀이 2

```js

function getDayName(a,b){
    var date = new Date(2016, (a - 1), b);
      return date.toString().slice(0, 3).toUpperCase();
}

```

