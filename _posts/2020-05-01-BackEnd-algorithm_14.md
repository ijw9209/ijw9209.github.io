---
title: "[JAVA] 프로그래머스 - 자연수 뒤집어 배열로 만들기"
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
last_modified_at: 2020-05-01T00:00:00-00:00
---

## 문제 

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

## 제한 조건

+ n은 10,000,000,000이하인 자연수입니다.


## 나의 풀이

```java

import java.util.*;
class Solution {
  public int[] solution(long n) {
      int len = (int)(Math.log10(n)+1);
      int answer[] = new int[len];
      
      String s = n + "";
      String arr[] = new String[len];
      arr = s.split("");
      
      for(int i = 0 ; i < len; i++){
          answer[i] = Integer.parseInt(arr[i]);
      }
      
      int left = 0;
      int right = len - 1;
      
      while(left < right){
          int temp = answer[left];
          answer[left] = answer[right];
          answer[right] = temp;
          left++; 
          right--;
      }
      
      return answer;
  }
}

```

## 다른사람의 풀이

```java


class Solution {
  public int[] solution(long n) {
      String a = "" + n;
        int[] answer = new int[a.length()];
        int cnt=0;

        while(n>0) {
            answer[cnt]=(int)(n%10);
            n/=10;
            System.out.println(n);
            cnt++;
        }
      return answer;
  }
}


```