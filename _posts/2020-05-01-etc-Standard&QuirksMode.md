---
title: "[HTML] 표준모드와 호환모드"
excerpt: "표준모드와 호환모드"
toc: true
toc_sticky: true

categories:
  - html
tags:
  - html
last_modified_at: 2020-05-01T08:06:00-05:00
---

# 표준모드와 호환모드

과거의 웹 페이지는 넷스케이프와 익스플로러 버전이 따로 존재했고 웹 표준이 없었다. 그러나 W3C가 웹 표준을 만들면서 브라우저가 웹 사이트를 제대로 표현할 수 없게 되자 렌더링을 할 때 **표준모드(Standard mode)**와 **호환모드(Quirks mode)**로 렌더링을 할 수 있게 옵션을 제공하였다.

브라우저는 HTML 문서가 DOCTYPE을 가지고 있지 않으면 호환 모드로 렌더링을 하고, 가지고 있지 않다면 주어진 DOCTYPE에 맞게 표준 모드로 렌더링을 한다. 호환 모드로 렌더링을 하게 되면 오래된 웹 페이지들을 최신 버전의 브라우저에서도 깨지지 않게 하기 때문에 각 브라우저마다 다르게 보일 수 있다. 예를 들어 IE의 경우 호환모드에서 박스 모델(Box model)을 잘못 해석하지만, 나머지 브라우저들은 그렇지 않다.

결론적으로, 정말 특별한 경우가 아니라면 DOCTYPE을 명시하여 브라우저가 표준모드로 렌더링 하게 하자. 현재 시점에서 HTML5에서 권장하는 방식인 `<DOCTYPE html>` 을 사용하는것이 바람직하다.

출처 : 
+ [https://github.com/baeharam/Must-Know-About-Frontend](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/html/standard-quirks.md)