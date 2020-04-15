---
title: "[JS] 프로그래머스 - 문자열 내 p와 y찾기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-20T08:06:00-05:00
---

## 문제 

대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.

예를 들어 s가 pPoooyY면 true를 return하고 Pyy라면 false를 return합니다

## 나의 풀이


```js
function solution(s) {

    var lower = s.toLowerCase()
    var pcnt = 0;
    var ycnt = 0;
    for (var i = 0; i < lower.length; i++) {
        if (lower[i] === 'p') {
            pcnt++;
        } else if (lower[i] === 'y') {
            ycnt++;
        }
    }
    if (pcnt === ycnt) {
        return true;
    } else {
        return false;
    }
}

test('문자열 내 p와 y의 개수', () => {
    expect(solution("pPoooyY")).toBeTruthy();
    expect(solution("Pyy")).toBeFalsy();
})

```


## 다른 사람의 풀이 1


```js
function solution(s) {
    return s.match(/p/ig).length == s.match(/y/ig).length;
}

```


## 다른 사람의 풀이 2

```js
function solution(s) {
    //함수를 완성하세요
    return s.toUpperCase().split("P").length === s.toUpperCase().split("Y").length;
}
```