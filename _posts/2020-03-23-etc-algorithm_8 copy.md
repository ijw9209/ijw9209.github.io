---
title: "[JS] 프로그래머스 - 이상한 문자 만들기"
excerpt: "TDD를 사용한 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-23T08:06:00-05:00
---

## 문제 

문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

제한 사항
문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.

## 나의 풀이

```js
function solution(s) {

    var arr = s.split(" ");
    var result = "";
    var len = arr.length;
    var arr2 = [];
    for (var i = 0; i < len; i++) {

        arr2[i] = upper(arr[i]);
    }
    result = arr2.join(' ');
    return result;
}

function upper(arr1) {
    var str = "";
    for (var i = 0; i < arr1.length; i++) {
        if (i % 2 === 0) {
            str += arr1[i].toUpperCase();
        } else {
            str += arr1[i].toLowerCase();
        }
    }
    return str;
}

test('이상한 문자 만들기', () => {
    expect(solution("try hello world")).toEqual("TrY HeLlO WoRlD");
})

```

띄어쓰기에 걸리면 0으로 다시 세어야하기때문에 힘들었다 split으로 자르면
공백이 없어지기때문에 upper함수를 호출하는곳에 공백을추가하면 맨뒤칸도 공백이 추가되어 계속 실패하였다. 그래서 또다른 배열에담고 join(' ')을 사용하여 다시 묶었더니 정확히 공백이들어가졌다 지금은 지저분해서 다시한번풀어보며 좀더 나은 코드를 작성해야겠다.


## 다른사람의 풀이 1



```js

function toWeirdCase(s){
    //함수를 완성해주세요
    return s.toUpperCase().replace(/(\w)(\w)/g, function(a){return a[0].toUpperCase()+a[1].toLowerCase();})

  }

```

## 다른사람의 풀이 2


```js

function toWeirdCase(s){
    var result = "";
      var num = 0;

    console.log(s.length);

    for(var i = 0; i < s.length; i++){
     if(s.charAt(i) == " "){
      num = 0;
      result += " ";
      continue;
     }
      else if(num % 2 == 0){
        result += (s.charAt(i)).toUpperCase();
        num++;
      }
      else{
        result += (s.charAt(i)).toLowerCase();
        num++; 
      }
    }
}

```