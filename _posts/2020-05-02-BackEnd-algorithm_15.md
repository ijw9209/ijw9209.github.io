---
title: "[JAVA] 프로그래머스 - 콜라즈 추측"
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
last_modified_at: 2020-05-02T00:00:00-00:00
---

## 문제 

1937년 Collatz란 사람에 의해 제기된 이 추측은, 주어진 수가 1이 될때까지 다음 작업을 반복하면, 모든 수를 1로 만들 수 있다는 추측입니다. 작업은 다음과 같습니다.

1. 입력된 수가 짝수라면 2로 나눕니다. 
2. 입력된 수가 홀수라면 3을 곱하고 1을 더합니다.
3. 결과로 나온 수에 같은 작업을 1이 될 때까지 반복합니다.

예를 들어, 입력된 수가 6이라면 6→3→10→5→16→8→4→2→1 이 되어 총 8번 만에 1이 됩니다. 위 작업을 몇 번이나 반복해야하는지 반환하는 함수, solution을 완성해 주세요. 단, 작업을 500번을 반복해도 1이 되지 않는다면 –1을 반환해 주세요.

## 제한 조건

+ 입력된 수, num은 1 이상 8000000 미만인 정수입니다.


## 나의 풀이

```java

class Solution {
    public int solution(int num) {
        int cnt = 0;
        while(true){
            
            if(cnt > 500){
                return -1;
            }else if(num > 1){
            num = (num % 2 == 0) ? num / 2 : num * 3 + 1;
            }else if(num == 1){
                return cnt;
            }
            cnt++;
        }
    }
}

```

## 다른사람의 풀이

```java

class Collatz {
    public int collatz(int num) {
    long n = (long)num;
    for(int i =0; i<500; i++){      
      if(n==1) return i;
      n = (n%2==0) ? n/2 : n*3+1;            
    }
    return -1;
  }
    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void main(String[] args) {
        Collatz c = new Collatz();
        int ex = 6;
        System.out.println(c.collatz(ex));
    }
}

```