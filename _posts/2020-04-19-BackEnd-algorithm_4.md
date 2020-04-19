---
title: "[JAVA] 프로그래머스 - 두 정수 사이의 합"
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
last_modified_at: 2020-04-19T08:06:00-05:00
---

## 문제 

두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.

## 제한 조건

+ a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.
+ a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.
+ a와 b의 대소관계는 정해져있지 않습니다.

## 나의 풀이

```java
class Solution {
  public long solution(int a, int b) {
      long answer = 0;
      
      for(int i = Math.min(a,b); i <= Math.max(a,b); i++ ){
          if(a == b){
              return a;
          }
          answer += i;
      }
      return answer;
  }
}

```

## 다른 사람의 풀이

```java

class Solution {

    public long solution(int a, int b) {
        return sumAtoB(Math.min(a, b), Math.max(b, a));
    }

    private long sumAtoB(long a, long b) {
        return (b - a + 1) * (a + b) / 2;
    }
}

```