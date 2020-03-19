---
title: "프로그래머스 - 같은숫자는 싫어!"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-19T08:06:00-05:00
---

## 문제 

배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,

arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.
배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.


## 풀이 1

```js
function solution(arr) {

    let answer = [];
    
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] !== arr[i + 1]) {
            answer[i] = arr[i]
        }
    }

    function isUndefiend(value) {
        return value !== undefined;
    }

    var filter = answer.filter(isUndefiend);
    return filter;

}

test('같은 숫자는 싫어', () => {
    expect(solution([1, 1, 3, 3, 0, 1, 1])).toEqual([1, 3, 0, 1]);
    expect(solution([4, 4, 4, 3, 3])).toEqual([4, 3]);
})

```

문제를 푸는데 answer 배열에 undefined가 담겨져서 isUndefind 함수를 만들어서 풀었다.
이유를 알고보니 answer의 인덱스값을 같이돌리니 첫번째 실행문의 1,3,4,5 이렇게 인덱스값이들어가 answer배열의 나머지값들은 비어있으니 당연히 undefined가 뜨는거였다!

## 다시 풀어본 풀이

```js
function solution(arr)
{
    let answer = [];
    let j = 0;
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] !== arr[i + 1]) {
            answer[j] = arr[i]
            j++
        }
    }
    return answer;
}

```

그래서 이런식으로하면 정상적으로 undefined 가 뜨지않고 출력되었다. 좀만더 차근차근히 생각했으면 좀더 쉽게 풀렸을텐데 좀더 생각하는 습관을 길러야겠다. 또한 다른사람의 풀이를 보니
filter함수에대해 좀더 공부를 해야겠다.

## 다른사람의 풀이 1

```js
function solution(arr) {

    return arr.filter((val,index) => val != arr[index+1]);
}

```

## 다른사람의 풀이 2

```js

function solution(arr) {
    var answer = [arr[0]];

    for (let i=1; i<arr.length; i++) {
        if (answer[answer.length - 1] !== arr[i]) {
            answer.push(arr[i]);
        }
    }

    return answer;
}

```


