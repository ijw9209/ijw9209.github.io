---
title: "BOM & DOM"
excerpt: "BOM 과 DOM"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-01T08:06:00-05:00
---

# BOM & DOM

## BOM (Browser Object Model)

브라우저의 창이나 프레임을 프로그래밍적으로 제어할 수 있게해주는 객체 모델이다. 브라우저의 새창 , 다른문서로의 이동하는 기능을 실행시킬 수 있다. 
전역객체인 window 가 있고 하위객체로 location, navigator , document, screen , history 가 있다.


![image](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/frontend/bom.png)


## DOM (Document Object Model)

웹페이지를 프로그래밍적으로 제어할 수 있는 객체 모델 이다. 최상위로 Node가 있으며 아래 사진과 같은 구조로 나타난다

![image](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/frontend/dom.png)


```html
<!DOCTYPE html>
<html>
    <head>
        <title>제목</title>
    </head>
    <body>
    <div class="클래스"></div>
    <!-- 주석 -->
    <a href="https://naver.com">네이버</a>
    </body>
</html>

```    
![image](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/frontend/dom2.png)

[LiveDomViewer](https://software.hixie.ch/utilities/js/live-dom-viewer/)를 사용해서 보면 엘리먼트 뿐만아니라 텍스트와 주석 노드까지 포함한다. 


요약하면 태그는 요소 노드가 되고 트리구조를 형성한다. 문자는 텍스트 노드가 되며, html의 모든것은 DOM을 구성한다. 주석까지도.


출처: 
+ [https://github.com/baeharam/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/frontend/bom-dom.md)
+ [https://ko.javascript.info/dom-nodes](https://ko.javascript.info/dom-nodes)