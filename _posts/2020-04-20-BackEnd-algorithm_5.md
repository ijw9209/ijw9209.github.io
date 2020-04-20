---
title: "[JAVA] 프로그래머스 - 수박수박수박수박수?"
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
last_modified_at: 2020-04-20T08:06:00-05:00
---

## 문제 

길이가 n이고, 수박수박수박수....와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 수박수박을 리턴하고 3이라면 수박수를 리턴하면 됩니다.

## 제한 조건

+ n은 길이 10,000이하인 자연수입니다.

## 나의 풀이

```java
class Solution {
  public String solution(int n) {
      String answer = "";
      String [] subak = {"수","박"};
      for(int i = 0; i < n; i++){
          if(i % 2 == 0){
              answer += subak[0];
          }else{
              answer += subak[1];
          }
      }
      
      return answer;
  }
}
```

## 다른 사람의 풀이

```java

public class WaterMelon {
    public String watermelon(int n){

        return new String(new char [n/2+1]).replace("\0", "수박").substring(0,n);
    }
}
```