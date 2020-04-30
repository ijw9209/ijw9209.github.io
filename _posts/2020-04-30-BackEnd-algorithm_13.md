---
title: "[JAVA] 프로그래머스 - 자릿수 더하기"
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
last_modified_at: 2020-04-30T00:00:00-00:00
---

## 문제 

자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

## 제한 조건

+ N의 범위 : 100,000,000 이하의 자연수



## 나의 풀이

```java

import java.util.*;
public class Solution {
    public int solution(int n) {
        int answer = 0;
        while(n != 0){
            answer += n%10;
            n /= 10;
        }
        return answer;
    }
}

```

