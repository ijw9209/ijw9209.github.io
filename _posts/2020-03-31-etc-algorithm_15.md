---
title: "프로그래머스 - 핸드폰 번호 가리기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-31T08:06:00-05:00
---

## 문제 

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.


### 제한사항

s는 길이 4 이상, 20이하인 문자열입니다.


## 나의 풀이

```js


solution = phone_number => {
    let answer = '';

    const hide = phone_number.length - 4;
    for (let i = 0; i < phone_number.length; i++) {
        if (i < hide) {
            answer += "*";
        } else {
            answer += phone_number[i];
        }
    }
    return answer;
}

test('핸드폰 번호 가리기', () => {
    expect(solution("01033334444")).toBe("*******4444");
    expect(solution("027778888")).toBe("*****8888");
})

```

### 다른사람의 풀이 1

```js

function hide_numbers(s) {
    return s.replace(/\d(?=\d{4})/g, "*");
  }

  console.log("결과 : " + hide_numbers('01033334444'));

```

### 다른사람의 풀이 2


```js


function hide_numbers(s){
    var result = "*".repeat(s.length - 4) + s.slice(-4);

    return result;
  }

  console.log("결과 : " + hide_numbers('01033334444'));

```


