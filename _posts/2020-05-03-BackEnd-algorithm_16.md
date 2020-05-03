---
title: "[JAVA] 프로그래머스 - 완주하지 못한 선수"
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
last_modified_at: 2020-05-03T00:00:00-00:00
---

## 문제 

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

## 제한 조건

+ 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
+ completion의 길이는 participant의 길이보다 1 작습니다.
+ 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 
  있습니다.
+ 참가자 중에는 동명이인이 있을 수 있습니다.

## 나의 풀이

```java

import java.util.*;
class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        int i;
        for(i = 0; i < completion.length; i++){
            if(!participant[i].equals(completion[i])){
                return participant[i];
            }
            
        }
        return participant[i];
    }
}

```

## 다른사람의 풀이

```java

import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> hm = new HashMap<>();
        for (String player : participant) hm.put(player, hm.getOrDefault(player, 0) + 1);
        for (String player : completion) hm.put(player, hm.get(player) - 1);

        for (String key : hm.keySet()) {
            if (hm.get(key) != 0){
                answer = key;
            }
        }
        return answer;
    }
}

```