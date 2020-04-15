---
title: "[JAVA] 프로그래머스 - 핸드폰 번호 가리기"
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
last_modified_at: 2020-04-15T08:06:00-05:00
---

## 문제 

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

## 제한 조건

+ s는 길이 4 이상, 20이하인 문자열입니다

## 나의 풀이

```java
class Solution {
  public String solution(String phone_number) {
      String answer = "";
      String arr[] = phone_number.split("");
      int hide = phone_number.length() - 4;
      for(int i = 0; i < phone_number.length(); i++) {
          if(i < hide){
              answer += "*";
          }else {
              answer += arr[i];
          }
      }
      return answer;
  }
}
```

## 다른사람의 풀이


```java

class Solution {
  public String solution(String phone_number) {
     char[] ch = phone_number.toCharArray();
     for(int i = 0; i < ch.length - 4; i ++){
         ch[i] = '*';
     }
     return String.valueOf(ch);
  }
}

```