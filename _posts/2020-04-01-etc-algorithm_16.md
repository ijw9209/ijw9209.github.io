---
title: "[JS] 프로그래머스 - 제일 작은 수 제거하기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-01T08:06:00-05:00
---

## 문제 

정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.


### 제한사항

arr은 길이 1 이상인 배열입니다.
인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.

## 나의 풀이

```js

solution = arr => {
    if (arr.length <= 2) {
        return [-1];
    }

    let min = Math.min.apply(null, arr);
    let idx = arr.indexOf(min);
    arr.splice(idx, 1);
    return arr;
}

test('제일 작은 수 제거하기', () => {
    expect(solution([4, 3, 2, 1])).toEqual([4, 3, 2]);
    expect(solution([10])).toEqual([-1]);
})

```

### 다른사람의 풀이 1

```js

function solution(arr) {
    arr.splice(arr.indexOf(Math.min(...arr)),1);
    if(arr.length<1)return[-1];
    return arr;
}
```

### 다른사람의 풀이 2


```js

 function solution(arr) {
    var a=Math.min.apply(null,arr);
    arr.splice(arr.indexOf(a),1);

    if(arr[0]==undefined)
        return [-1];
    else
        return arr;
}
```


