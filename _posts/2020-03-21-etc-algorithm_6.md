---
title: "프로그래머스 - 문자열을 정수로 바꾸기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-21T08:06:00-05:00
---

## 문제 

문제 설명
문자열 s를 숫자로 변환한 결과를 반환하는 함수, solution을 완성하세요.

제한 조건
s의 길이는 1 이상 5이하입니다.
s의 맨앞에는 부호(+, -)가 올 수 있습니다.
s는 부호와 숫자로만 이루어져있습니다.
s는 0으로 시작하지 않습니다.

## 나의 풀이


```js
function solution(s) {
    let answer = 0;

    answer = Number(s);
    return answer;
}


test('문자열을 정수로바꾸기', () => {
    //expect(solution("1234")).toBe(1234);
    expect(solution("-1234")).toBe(-1234);
})

```


## 다른 사람의 풀이 1


```js

function solution(str) {
    return str / 1
}
```


## 다른 사람의 풀이 2

```js
 function solution(str) {
    return +str;
}
```