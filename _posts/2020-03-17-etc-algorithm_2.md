---
title: "[JS] 프로그래머스 - 두 정수사이의 합"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-17T08:06:00-05:00
---

## 문제 

두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.

## 풀이

나의풀이
```js
function solution(a, b) {

    let answer = 0;

    if (a < b) {
        for (let i = a; i <= b; i++)
            answer += i;
    } else {
        for (let i = b; i <= a; i++) {
            answer += i;
        }
    }
    if (a === b) {
        answer = a;
    }
    return answer;
}

test('두 정수사이의 합', () => {
    expect(solution(3, 5)).toBe(12);
    expect(solution(5, 3)).toBe(12);
    expect(solution(3, 3)).toBe(3);
});
```

다른사람의 풀이1

```js

//다른사람
function solution(a, b) {
return (a+b)*(Math.abs(b-a)+1)/2
}
```

한줄로 끝나는거보고 대단하다생각했다..


다른사람의 풀이2

```js
    let sum = 0;
    for (let i = Math.min(a, b); i <= Math.max(a, b); i++) {
        sum += i;
    }
    return sum;
```

이 풀이를 보고 잘 몰랐던 min , max함수에대해서 다시공부해보게 되었다.
여러 메소드들을 공부하고 사용해보고 찾아보니 많은 도움이되는것같다.