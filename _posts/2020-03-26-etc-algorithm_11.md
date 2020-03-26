---
title: "프로그래머스 - 짝수와 홀수"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-26T08:06:00-05:00
---

## 문제 

정수 num이 짝수일 경우 Even을 반환하고 홀수인 경우 Odd를 반환하는 함수, solution을 완성해주세요.

제한 조건
num은 int 범위의 정수입니다.
0은 짝수입니다.

## 나의 풀이

```js

function solution(num) {

    return (num % 2 === 0) ? "Even" : "Odd";
}

test('짝수와 홀수', () => {
    expect(solution(3)).toEqual("Odd");
    expect(solution(4)).toBe("Even");
})

```

