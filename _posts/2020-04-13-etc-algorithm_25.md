---
title: "[JS] 프로그래머스 - 문자열 내림차순으로 배치하기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-13T08:06:00-05:00
---

## 문제 


문자열 s에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 문자열을 리턴하는 함수, solution을 완성해주세요.
s는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.

## 제한사항 

+ str은 길이 1 이상인 문자열입니다.

## 나의 풀이

```js

solution = s => {

    const arr = s.split('');
    return arr.sort().reverse().join('');

}

test('문자열 내림차순으로 배치하기', () => {
    expect(solution("Zbcdefg")).toEqual("gfedcbZ");
})

```


## 다른 사람의 풀이 

```js

function solution(s) {
    return s.split('').sort((a, b) => {
        if (a > b) return -1;
        if (b > a) return 1;
        return 0;
    }).join('');
}

```
