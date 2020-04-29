---
title: "[HTML] local storage vs session storage vs cookie"
excerpt: "local storage vs session storage vs cookie"
toc: true
toc_sticky: true

categories:
  - html
tags:
  - html
last_modified_at: 2020-04-29T08:06:00-05:00
---

# local storage vs session storage vs cookie

모두 클라이언트 상에서 Key/value 쌍을 저장할 수 있는 메커니즘으로 value는 반드시 문자열이어야 한다. 또한 모두 동일출처정책(SOP)를 따르기 때문에 다른 도메인에서 접근할 수 없다.

||cookie|local storage|session storage|
|---------|----------|-----------|------------|
|생성자|클라이언트/서버|클라이언트|클라이언트|
|지속시간|설정 여부에 따름|명시적으로 지울때까지|탭 윈도우 닫을때까지|
|용량|5KB|5KB/10MB|5MB|
|서버와의 통생|O|X|X|
|취약점|XSS/CSRF공격|XSS공격|XSS공격|

출처 : 
+ [https://github.com/baeharam/Must-Know-About-Frontend/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/html/web-storage-api.md)