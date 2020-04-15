---
title: "[JS] 프로그래머스 - 자연수 뒤집어 배열로 만들기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-30T08:06:00-05:00
---

## 문제 

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

### 제한사항

n은 10,000,000,000이하인 자연수입니다.


## 나의 풀이

```js

solution = n => {
    const answer = [];
    let str = String(n);
    for (let i = 0; i < str.length; i++) {
        answer[i] = Number(str[i]);
    }
    answer.reverse();
    return answer;
}

//자연수 뒤집어 배열로 만들기
test('자연수 뒤집어 배열로 만들기', () => {
    expect(solution(12345)).toEqual([5, 4, 3, 2, 1]);
})

```

