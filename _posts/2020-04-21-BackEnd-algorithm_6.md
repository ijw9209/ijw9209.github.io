---
title: "[JAVA] 프로그래머스 - 하사드수"
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
last_modified_at: 2020-04-21T08:06:00-05:00
---

## 문제 

양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.

## 제한 조건

+ x는 1 이상, 10000 이하인 정수입니다.


## 나의 풀이

```java
class Solution {
  public boolean solution(int x) {
      boolean answer = true;
      String s = Integer.toString(x);
      String[] arr = s.split(""); 
      int sum = 0;
      for(int i = 0; i < arr.length; i++){
          sum += Integer.parseInt(arr[i]);
      }
      if(x % sum == 0){
          answer = true;
      } else{
          answer = false;
      }
      
      return answer;
  }
}
```
