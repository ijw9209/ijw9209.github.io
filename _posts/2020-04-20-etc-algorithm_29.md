---
title: "[JS] 프로그래머스 - 직사각형 별찍기"
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

이 문제에는 표준 입력으로 두 개의 정수 n과 m이 주어집니다.
별(*) 문자를 이용해 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 출력해보세요.

## 제한 조건

+ n과 m은 각각 1000 이하인 자연수입니다.


## 나의 풀이

```js

process.stdin.setEncoding('utf8');
process.stdin.on('data', data => {
    const n = data.split(" ");
    const a = Number(n[0]), b = Number(n[1]);
    let answer = "";
    for(let i = 0; i < b; i++){
        for(let j = 0; j < a; j++){
        answer += "*";
        }
        answer += "\n";
    }
    console.log(answer);
});

```


## 다른사람의 풀이

```js

process.stdin.setEncoding('utf8');
process.stdin.on('data', data => {
    const n = data.split(" ");
    const a = Number(n[0]), b = Number(n[1]);
    let answer = "";
    for(let i = 0; i < b; i++){
        for(let j = 0; j < a; j++){
        answer += "*";
        }
        answer += "\n";
    }
    console.log(answer);
});

```
