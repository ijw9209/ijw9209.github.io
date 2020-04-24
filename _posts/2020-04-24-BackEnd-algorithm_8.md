---
title: "[JAVA] 프로그래머스 - 가운데 글자 가져오기"
excerpt: "JAVA로 프로그래머스 알고리즘풀기"
toc: true
toc_sticky: true

categories:
  - etc
  - BackEnd
  - java
tags:
  - etc
  - BackEnd
  - java
last_modified_at: 2020-04-24T08:06:00-05:00
---

## 문제 

단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

## 제한 조건

+ s는 길이가 1 이상, 100이하인 스트링입니다.


## 나의 풀이

```java

class Solution {
  public String solution(String s) {
      String answer = "";
      int div = s.length() / 2;
      if(s.length() % 2 == 0){
          answer = s.substring(div - 1, div + 1);
      }else{
          answer = s.substring(div , div + 1);
      }
      return answer;
  }
}

```


## 다른 사람의 풀이

```java

class StringExercise{
    String getMiddle(String word){

        return word.substring((word.length()-1) / 2, word.length()/2 + 1);    
    }
    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void  main(String[] args){
        StringExercise se = new StringExercise();
        System.out.println(se.getMiddle("power"));
    }
}

```
