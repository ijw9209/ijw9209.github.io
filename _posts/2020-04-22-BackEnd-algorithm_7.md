---
title: "[JAVA] 프로그래머스 - 문자열을 정수로 바꾸기"
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
last_modified_at: 2020-04-22T08:06:00-05:00
---

## 문제 

문자열 s를 숫자로 변환한 결과를 반환하는 함수, solution을 완성하세요.

## 제한 조건

+ s의 길이는 1 이상 5이하입니다.
+ s의 맨앞에는 부호(+, -)가 올 수 있습니다.
+ s는 부호와 숫자로만 이루어져있습니다.
+ s는 0으로 시작하지 않습니다.


## 나의 풀이

```java
class Solution {
  public int solution(String s) {
      int answer = 0;
      answer = Integer.parseInt(s);
      return answer;
  }
}
```


## 다른 사람의 풀이

```java
public class StrToInt {
    public int getStrToInt(String str) {
            boolean Sign = true;
            int result = 0;

      for (int i = 0; i < str.length(); i++) {
                char ch = str.charAt(i);
                if (ch == '-')
                    Sign = false;
                else if(ch !='+')
                    result = result * 10 + (ch - '0');
            }
            return Sign?1:-1 * result;
    public static void main(String args[]) {
        StrToInt strToInt = new StrToInt();
        System.out.println(strToInt.getStrToInt("-1234"));
    }
}
```
