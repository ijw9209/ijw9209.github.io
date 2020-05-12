---
title: "[JAVA] 프로그래머스 - 문자열 다루기 기본"
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
last_modified_at: 2020-05-12T00:00:00-00:00
---

## 문제 

문자열 s의 길이가 4 혹은 6이고, 숫자로만 구성돼있는지 확인해주는 함수, solution을 완성하세요. 예를 들어 s가 a234이면 False를 리턴하고 1234라면 True를 리턴하면 됩니다.

## 제한 조건

+ s는 길이 1 이상, 길이 8 이하인 문자열입니다.

## 나의 풀이

```java

class Solution {
  public boolean solution(String s) {
      boolean answer = true;
      String regex = "^[0-9]+$";
        
      return (s.length() == 4 || s.length() == 6)&&(s.matches(regex)) ? true : false;
  }
}


```


## 다른사람의 풀이

```java

class Solution {
  public boolean solution(String s) {
      if(s.length() == 4 || s.length() == 6){
          try{
              int x = Integer.parseInt(s);
              return true;
          } catch(NumberFormatException e){
              return false;
          }
      }
      else return false;
  }
}

```

