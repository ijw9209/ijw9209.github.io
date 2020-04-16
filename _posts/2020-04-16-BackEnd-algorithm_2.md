---
title: "[JAVA] 프로그래머스 - 약수의합"
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
last_modified_at: 2020-04-16T08:06:00-05:00
---

## 문제 

정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

## 제한 조건

+ n은 0 이상 3000이하인 정수입니다.

## 나의 풀이

```java

class Solution {
  public int solution(int n) {
      int sum = 0;
      for(int i = 1; i <= n; i++){
          if(n % i == 0){
              sum += i;
          }
      }
      return sum;
  }
}

```
