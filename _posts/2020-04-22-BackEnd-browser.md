---
title: "[Boostcurse] Browser의 동작"
excerpt: "부스트코스 공부하기"
toc: true
toc_sticky: true

categories:
  - BackEnd
  - Boostcurse
tags:
  - BackEnd
  - Boostcurse
last_modified_at: 2020-04-22T08:06:00-05:00
---

# browser의 동작

브라우저는 월드와이드웹(WWW)에서 정보를 검색, 표현하고 탐색하기 위한 소프트웨어이다.

인터넷에서 특정 정보로 이동할 수 있는 주소 입력창이 있고 서버와 HTTP로 정보를 주고 받을 수 있는 네트워크 모듈도 포함하고 있다.
그리고 서버에서 받은 문서 (HTML, CSS , JavaScript)를 해석하고 실행하여 화면에 표현하기 위한 해석기(Parser) 들을 가지고 있다.
브라우저마다 서로 다른 엔진을 포함하고 있다.
아래그림이 대표적인 내용


![image](https://cphinf.pstatic.net/mooc/20171231_32/1514692895834EoHUo_PNG/webkitflow.png)


HTML을 해석해서 DOM Tree를 만들고, CSS를 해석해서 CSS Tree(CSS Object Model)을 만든다.
이 과정에서 Parsing 과정이 필요하며 토큰 단위로 해석되는 방식은 일반적인 소스코드의 컴파일 과정이라 보면된다.
DOM Tree와 CSS Tree, 이 두개는 연관되어 있으므로 Render Tree로 다시 조합된다.
이렇게 조합된 결과는 화면에 어떻게 배치할지 크기와 위치 정보를 담고 있다.
이후에 이렇게 구성된 Render Tree정보를 통해서 화면에 어떤 부분에 어떻게 색칠을 할지 Painting과정을 거친다.

출처 : 
+ [https://www.edwith.org/boostcourse-web/lecture/16663/](https://www.edwith.org/boostcourse-web/lecture/16663/)