---
title: "[JAVA] 프로그래머스 - 정수 내림차순으로 배치하기"
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
last_modified_at: 2020-05-08T00:00:00-00:00
---

## 문제 

함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

## 제한 조건

+ n은 1이상 8000000000 이하인 자연수입니다.

## 나의 풀이

```java

import java.util.Arrays;
import java.util.Collections;

class Solution {
  public long solution(long n) {
      long answer = 0;
      int len = Long.toString(n).split("").length;
      
      String[] arr = new String[len];
      arr = Long.toString(n).split("");
      
      String str = "";
      
      Arrays.sort(arr , Collections.reverseOrder());
      
      for(int i = 0; i < len; i++){
          str += (long)Integer.parseInt(arr[i]);
      }
      
      answer = Long.parseLong(str);
      return answer;
  }
}

```


## 다른사람의 풀이

```java

public class ReverseInt {
    String res = "";
    public int reverseInt(int n){
        res = "";
        Integer.toString(n).chars().sorted().forEach(c -> res = Character.valueOf((char)c) + res);
        return Integer.parseInt(res);
    }

    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void  main(String[] args){
        ReverseInt ri = new ReverseInt();
        System.out.println(ri.reverseInt(118372));
    }
}


```

