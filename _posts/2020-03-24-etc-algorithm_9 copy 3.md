---
title: "프로그래머스 - 수박수박수박수박수?"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-24T08:06:00-05:00
---

## 문제 

길이가 n이고, 수박수박수박수....와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 수박수박을 리턴하고 3이라면 수박수를 리턴하면 됩니다.

제한 조건
n은 길이 10,000이하인 자연수입니다.

## 나의 풀이

```js

solution = n => {

    const subak = ["수", "박"]
    let answer = "";

    for (let i = 0; i < n; i++) {
        if (i % 2) {
            answer += subak[1];
        } else {
            answer += subak[0];
        }
    }
    return answer;
}

test('수박수박수박수박수박수?', () => {
    expect(solution(3)).toEqual("수박수");
    expect(solution(4)).toEqual("수박수박");
})

```



## 다른사람의 풀이 1



```js

function waterMelon(n){
    var result = "수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박"
    //함수를 완성하세요

    return result.substring(0,n);
  }

  // 실행을 위한 테스트코드입니다.
  console.log("n이 3인 경우: "+ waterMelon(3))
  console.log("n이 4인 경우: "+ waterMelon(4))
}

```

## 다른사람의 풀이 2


```js

function waterMelon(n){
    var result = "수박";
     result = result.repeat(n-1).substring(0,n);
    //함수를 완성하세요

    return result;
  }

  // 실행을 위한 테스트코드입니다.
  console.log("n이 3인 경우: "+ waterMelon(3))
  console.log("n이 4인 경우: "+ waterMelon(4))

```