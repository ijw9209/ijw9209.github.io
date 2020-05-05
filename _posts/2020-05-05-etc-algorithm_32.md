---
title: "[JS] 프로그래머스 - 시저 암호"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-05-05T08:06:00-05:00
---

## 문제 

어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다. 예를 들어 AB는 1만큼 밀면 BC가 되고, 3만큼 밀면 DE가 됩니다. z는 1만큼 밀면 a가 됩니다. 문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

## 제한 조건

+ 공백은 아무리 밀어도 공백입니다.
+ s는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
+ s의 길이는 8000이하입니다.
+ n은 1 이상, 25이하인 자연수입니다.


## 나의 풀이

```js

solution = (s, n) => {
    let answer = '';

    for (let i = 0; i < s.length; i++) {
        if (s.charCodeAt(i) === 32) {
            answer += ' ';
        } else if (s.charCodeAt(i) + n > 122) {
            answer += String.fromCharCode(s.charCodeAt(i) + n - 26);
        } else if (s.charCodeAt(i) + n > 90 && s.charCodeAt(i) <= 90) {
            answer += String.fromCharCode(s.charCodeAt(i) + n - 26);
        } else {
            answer += String.fromCharCode(s.charCodeAt(i) + n);
        }
    }

    return answer;

}


test('시저 암호', () => {
    expect(solution("AB", 1)).toEqual("BC");
    expect(solution("z", 1)).toEqual("a");
    expect(solution("a B z", 4)).toEqual("e F d");
})

```


## 다른사람의 풀이

```js

function caesar(s, n) {
    var result = "";
    // 함수를 완성하세요.
  var car = ""

  for (var i=0; i<s.length;i++)
  {        
    if ( s[i] == ' ' )
      result += ' '
    else 
        result += String.fromCharCode( (s.charCodeAt(i)>90)?
      (s.charCodeAt(i)+n-97)%26+97 : (s.charCodeAt(i)+n-65)%26+65 )     
  }

    return result;
}

```
