---
title: "[HTML] script, script async, script defer"
excerpt: "script, script async, script defer"
toc: true
toc_sticky: true

categories:
  - html
tags:
  - html
last_modified_at: 2020-04-30T08:06:00-05:00
---

# script, script async, script defer

+ `<script>` : HTML 파싱이 중단되고 즉시 스크립트가 로드되며 로드된 스크립트가 실행되고 파싱이 재개된다.

+ `<script async>` : HTML 파싱과 병렬적으로 로드가 되는데, 스크립트를 실행할 때는 파싱이 중단된다. 구글 애널리틱스와 같이 다른 스크립트가 의존하지 않는 독자적인 스크립트를 로드할 때 적합하다.

+ `<script defer>` : HTML 파싱과 병렬적으로 로드가 되는데, 파싱이 끝나고 스크립트를 로드한다. 보통 `<body>` 태그 직전에 삽입하는것이 좋다.

**주의할 점은 async와 defer의 경우 `src` 속성이 없으면 적용되지 않는다.**

아래 그림을 통해 보다 확실하게 확인할 수 있다. 

![image](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/html/script.png)


출처 : 

+ [https://github.com/baeharam/Must-Know-About-Frontend/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/html/script-tag-type.md#script-script-async-script-defer)