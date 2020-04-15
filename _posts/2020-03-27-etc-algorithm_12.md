---
title: "[JS] 프로그래머스 - 자릿수 더하기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-27T08:06:00-05:00
---

## 문제 


자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

제한사항
N의 범위 : 100,000,000 이하의 자연수


## 나의 풀이

```js

solution = n => {

    const answer = String(n);
    let result = 0;
    for (const element of answer) {
        result += Number(element)
    }
    return result;

}

test('자릿수 더하기', () => {
    expect(solution(123)).toEqual(6);
    expect(solution(987)).toEqual(24);
})

```

## 다른사람의 풀이


```js

function solution(n){
    
    return (n+"").split("").reduce((acc, curr) => acc + parseInt(curr), 0)
}

```