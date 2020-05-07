---
title: "[JS] 프로그래머스 - 행렬의 덧셈"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-05-07T08:06:00-05:00
---

## 문제 

행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

## 제한 조건

+ 행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.

## 나의 풀이

```js

solution = (arr1, arr2) => {


    const answer = [];
    let len1 = arr1.length;
    let len2 = arr1[0].length;

    for (let i = 0; i < len1; i++) {
        answer.push([]);
    }

    for (let i = 0; i < len1; i++) {
        for (let j = 0; j < len2; j++) {
            answer[i][j] = arr1[i][j] + arr2[i][j];
        }
    }

    return answer;

}

test('행렬의 덧셈', () => {
    expect(solution([[1, 2], [2, 3]], [[3, 4], [5, 6]])).toEqual([[4, 6], [7, 9]]);
})

```


## 다른사람의 풀이

```js

function sumMatrix(A,B){

    return A.map((a,i) => a.map((b, j) => b + B[i][j]));
}

```
