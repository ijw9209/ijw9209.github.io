---
title: "프로그래머스 - 약수의 합 구하기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-22T08:06:00-05:00
---

## 문제 

정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

제한 사항
n은 0 이상 3000이하인 정수입니다.
## 나의 풀이


```js
function solution(n) {
    var answer = 0;


    for (var i = 1; i <= n; i++) {
        if (n % i === 0) {
            answer += i;
        }
    }
    // 2,3,4,6 
    return answer;
}

test('약수의 합 구하기', () => {
    //expect(solution("12")).toBe(28);
    expect(solution("5")).toBe(6);
})


```

일단 약수의 개수를 구해서 하는건가 싶어서 갯수로 해봣는데 계속 실패하였다
그래서 살짝 힌트를 봤더니 들어온값에 나머지가 0 이면 약수라는것을 알았다.
아직 사고방식이 많이부족한것같다. 좀더 생각하는 방식을 기르자!


## 다른 사람의 풀이 1


```js

function sumDivisor(num) {
    //1과 자기 자신을 약수로 가진다.
    var answer = 1 + num;

    for (let i = 2; i < num; i++) {
        if (num % i == 0)
            answer += i
    }

    return answer;
}

console.log(sumDivisor(12));
```


## 다른 사람의 풀이 2

```js
 
let sumDivisor = num => {

    let answer = 0,
        i = 1,
        j = num % 2 == 0 ? 1 : 2

    for (i; i < num; i = i + j) if (num % i == 0) answer += i

    return answer + num
}

console.log(sumDivisor(12));
```