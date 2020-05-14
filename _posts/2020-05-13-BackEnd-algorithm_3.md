---
title: "[JAVA, C] 프로그래머스 - 평균구하기"
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
last_modified_at: 2020-05-13T08:06:00-05:00
---

## 문제 

정수를 담고 있는 배열 arr의 평균값을 return하는 함수, solution을 완성해보세요.

## 제한 조건

+ arr은 길이 1 이상, 100 이하인 배열입니다.
+ arr의 원소는 -10,000 이상 10,000 이하인 정수입니다.

## 나의 풀이

## JAVA


```java

class Solution {
  public double solution(int[] arr) {
      double answer = 0;
      int length = arr.length;
      for(int i = 0; i < arr.length; i++){
          answer += arr[i];
      }
      return answer / length;
  }
}

```
## JAVA 다른사람의 풀이



### JAVA

```java
import java.util.Arrays;

public class GetMean {
    public int getMean(int[] array) {
        return (int) Arrays.stream(array).average().orElse(0);
    }
}

```

## C 

```c

#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

// arr_len은 배열 arr의 길이입니다.
double solution(int arr[], size_t arr_len) {
    double answer = 0;
    int sum = 0;
    for(int i = 0; i < arr_len; i++){
        sum += arr[i];
    }
    answer = (double)sum / arr_len;
    return answer;
}

```



### C 다른사람의 풀이

```c

#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

// arr_len은 배열 arr의 길이입니다.
double solution(int arr[], size_t arr_len) {
    double answer = 0;
    float sum = 0;

    for(int i = 0; i < arr_len; ++i)
    {
        answer += arr[i];
    }
    answer /= arr_len;

    return answer;
}


```