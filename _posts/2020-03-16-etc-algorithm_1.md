---
title: "프로그래머스 - 가운데글자 반환하기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-16T08:06:00-05:00
---

## 문제 

단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

## 풀이

```js
Center = (str) => {
    let answer = ''
    const i = str.length / 2

    if (str.length % 2 == 0) {
        answer = str[i - 1] + str[str.length / 2]
        return answer
    } else {
        answer = str[Math.floor(str.length / 2)]
        return answer
    }
}

//가운데 글자 반환하기
test('centerStr', () => {
    expect(Center("abcdef")).toBe("cd");
    expect(Center("abcde")).toBe("c");
})

```