---
title: "[JS] 프로그래머스 - 모의고사"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-07T08:06:00-05:00
---

## 문제 

수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

+ 1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
+ 2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
+ 3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

### 제한사항

+ 시험은 최대 10,000 문제로 구성되어있습니다.
+ 문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
+  가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.

## 나의 풀이

```js

solution = answers => {

    const one = [1, 2, 3, 4, 5];
    const two = [2, 1, 2, 3, 2, 4, 2, 5];
    const three = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5];
    const cnt = [0, 0, 0];

    for (let i = 0; i < answers.length; i++) {
        if (one[i % 5] === answers[i]) cnt[0]++;
        if (two[i % 8] === answers[i]) cnt[1]++;
        if (three[i % 10] === answers[i]) cnt[2]++;
    }
    let max = Math.max(...cnt);
    let answer = [];
    for (let i = 0; i < cnt.length; i++) {
        if (cnt[i] === max) {
            answer.push(i + 1);
        }
    }
    return answer;
}

test('모의고사', () => {
    expect(solution([1, 2, 3, 4, 5])).toEqual([1]);
    expect(solution([1, 3, 2, 4, 2])).toEqual([1, 2, 3]);
})


```

### 다른사람의 풀이 1

```js

function solution(answers) {
    var answer = [];
    var a1 = [1, 2, 3, 4, 5];
    var a2 = [2, 1, 2, 3, 2, 4, 2, 5]
    var a3 = [ 3, 3, 1, 1, 2, 2, 4, 4, 5, 5];

    var a1c = answers.filter((a,i)=> a === a1[i%a1.length]).length;
    var a2c = answers.filter((a,i)=> a === a2[i%a2.length]).length;
    var a3c = answers.filter((a,i)=> a === a3[i%a3.length]).length;
    var max = Math.max(a1c,a2c,a3c);

    if (a1c === max) {answer.push(1)};
    if (a2c === max) {answer.push(2)};
    if (a3c === max) {answer.push(3)};


    return answer;
}


```

