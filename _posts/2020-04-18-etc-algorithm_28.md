---
title: "[JS] 프로그래머스 - 최대공약수와 최소공배수"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-18T08:06:00-05:00
---

## 문제 


두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해 보세요. 배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.

## 제한 조건

+ 두 수는 1이상 1000000이하의 자연수입니다.


## 나의 풀이

```js
solution = (n, m) => {
    const answer = [];

    const arr1 = measure(n);
    const arr2 = measure(m);
    const fillter = arr1.filter((item) => arr2.indexOf(item) > -1);

    answer[0] = Math.max.apply(null, fillter);
    answer[1] = n * m / answer[0];
    return answer;
}

measure = n => {
    const arr = [];
    let num = 0;
    for (let i = 1; i <= n; i++) {
        if (n % i === 0) {
            arr[num] = i;
            num++;
        }
    }
    return arr;
}

test('최대공약수와 최소공배수', () => {
    expect(solution(3, 12)).toEqual([3, 12]);
    expect(solution(2, 5)).toEqual([1, 10]);
})


```

