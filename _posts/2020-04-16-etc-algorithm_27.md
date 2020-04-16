---
title: "[JS] 프로그래머스 - 정수 제곱근 판별"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-16T08:06:00-05:00
---

## 문제 

임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.
n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.

## 제한 조건

+ n은 1이상, 50000000000000 이하인 양의 정수입니다.

## 나의 풀이

```js

solution = n => {

    const num = Math.sqrt(n);
    if (Number.isInteger(num)) {
        return Math.pow(num + 1, 2);
    } else {
        return -1
    }
}

test('정수제곱근판별', () => {
    expect(solution(121)).toEqual(144);
    expect(solution(3)).toEqual(-1);
})

```

