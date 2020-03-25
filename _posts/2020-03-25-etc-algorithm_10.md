---
title: "프로그래머스 - 평균구하기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-25T08:06:00-05:00
---

## 문제 

정수를 담고 있는 배열 arr의 평균값을 return하는 함수, solution을 완성해보세요.

제한사항
arr은 길이 1 이상, 100 이하인 배열입니다.
arr의 원소는 -10,000 이상 10,000 이하인 정수입니다.


## 나의 풀이

```js

solution = arr => {
    let sum = 0;
    for (let value of arr) {
        sum += value;
    }
    return sum / arr.length;
}

test('평균구하기', () => {
    expect(solution([1, 2, 3, 4])).toBe(2.5);
    expect(solution([5, 5])).toEqual(5);
})

```


## 다른사람의 풀이 1


```js

function average(array) {
    return array.reduce((a, b) => a + b) / array.length;
}

```

reduce , map , filter 함수에 대해 좀더 익숙해져야겠다.