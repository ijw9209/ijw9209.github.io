---
title: "[JS] 프로그래머스 - 정수 내림차순으로 배치하기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-22T08:06:00-05:00
---

## 문제 

함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

## 제한 조건

+ n은 1이상 8000000000 이하인 자연수입니다.


## 나의 풀이

```js

solution = n => {
    let answer = 0;
    const arr = [];
    let str = String(n);
    for (let i = 0; i < str.length; i++) {
        arr[i] = str[i];
    }
    const sortArr = arr.sort(function (a, b) {
        return b - a;
    });

    answer = sortArr.join("");
    return Number(answer);
}

test('정수 내림차순으로 배치하기', () => {
    expect(solution(118372)).toEqual(873211);
})


```


## 다른사람의 풀이

```js

function solution(n) {
  const newN = n + "";
  const newArr = newN
    .split("")
    .sort()
    .reverse()
    .join("");

  return +newArr;
}

```
