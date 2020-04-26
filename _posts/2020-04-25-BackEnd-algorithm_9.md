---
title: "[JAVA] 프로그래머스 - 나누어 떨어지는 숫자 배열"
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
last_modified_at: 2020-04-25T08:06:00-05:00
---

## 문제 

array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.
divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.

## 제한 조건

+ arr은 자연수를 담은 배열입니다.
+ 정수 i, j에 대해 i ≠ j 이면 arr[i] ≠ arr[j] 입니다.
+ divisor는 자연수입니다.
+ array는 길이 1 이상인 배열입니다.


## 나의 풀이

```java

import java.util.Arrays;

class Solution {
  public int[] solution(int[] arr, int divisor) {
      int answer[] = {-1};
      int idx = 0;
      int j = 0;
      for(int i = 0; i < arr.length; i++){
          if(arr[i] % divisor == 0){
               idx++;
          }
      }
      
      if(idx == 0){
          
      }else{
          answer = new int[idx];
      }      
      for(int i = 0; i < arr.length; i++){
          if(arr[i] % divisor == 0){
              answer[j] = arr[i];
              j++;
          }
      }
      Arrays.sort(answer);
      return answer;
  }
}

```


## 다른 사람의 풀이

```java
import java.util.Arrays;

class Divisible {
    public int[] divisible(int[] array, int divisor) {
        //ret에 array에 포함된 정수중, divisor로 나누어 떨어지는 숫자를 순서대로 넣으세요.
        return Arrays.stream(array).filter(factor -> factor % divisor == 0).toArray();
    }
    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void main(String[] args) {
        Divisible div = new Divisible();
        int[] array = {5, 9, 7, 10};
        System.out.println( Arrays.toString( div.divisible(array, 5) ));
    }
}
```
