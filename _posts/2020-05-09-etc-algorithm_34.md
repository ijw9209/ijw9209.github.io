---
title: "[JS] 프로그래머스 - 소수 찾기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-05-09T08:06:00-05:00
---

## 문제 

1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환하는 함수, solution을 만들어 보세요.

소수는 1과 자기 자신으로만 나누어지는 수를 의미합니다.
(1은 소수가 아닙니다.)

## 제한 조건

+ n은 2이상 1000000이하의 자연수입니다.

## 나의 풀이

```js

solution = n => {
    const answer = [];

    for (let i = 0; i < n + 1; i++) {
        answer.push(true);
    }
    for (let i = 2; i * i < n; i++) {
        if (answer[i]) {
            for (let j = i * i; j <= n; j += i) {
                answer[j] = false;
            }
        }
    }
    answer.splice(0, 2, false, false);
    let cnt = 0;
    for (let i = 0; i < answer.length; i++) {
        if (answer[i]) {
            cnt++;
        }
    }

    return cnt;
}

test('소수 찾기', () => {
    expect(solution(10)).toEqual(4);
    expect(solution(5)).toEqual(3);
})

```


## 다른사람의 풀이

```js

function solution(n) {
    const s = new Set();
    for(let i=1; i<=n; i+=2){
        s.add(i);
    }
    s.delete(1);
    s.add(2);
    for(let j=3; j<Math.sqrt(n); j++){
        if(s.has(j)){
             for(let k=j*2; k<=n; k+=j){    
                s.delete(k);
             }
        }
    }
    return s.size;
}


```
