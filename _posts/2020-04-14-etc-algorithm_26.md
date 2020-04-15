---
title: "[JS] 프로그래머스 - x만큼 간격이 있는 n개의 숫자"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-14T08:06:00-05:00
---

## 문제 

함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

## 제한 조건

+ x는 -10000000 이상, 10000000 이하인 정수입니다.
+ n은 1000 이하인 자연수입니다.

## 나의 풀이

```js


solution = (x, n) => {
    var answer = [];

    for (let i = 1; i <= n; i++) {
        answer[i] = x * i;
    }
    answer.splice(0, 1);
    return answer;
}

test('x만큼 간격이 있는 n개의 숫자', () => {
    expect(solution(2, 5)).toEqual([2, 4, 6, 8, 10]);
    expect(solution(4, 3)).toEqual([4, 8, 12]);
    expect(solution(-4, 2)).toEqual([-4, -8]);
})


```


## 다른 사람의 풀이 

```js


function solution(x, n) {
    return Array(n).fill(x).map((v, i) => (i + 1) * v)
}

```
