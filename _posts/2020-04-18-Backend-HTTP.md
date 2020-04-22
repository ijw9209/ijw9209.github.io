---
title: "[Boostcurse] HTTP"
excerpt: "부스트코스 공부하기"
toc: true
toc_sticky: true

categories:
  - BackEnd
  - Boostcurse
tags:
  - BackEnd
  - Boostcurse
last_modified_at: 2020-04-18T08:06:00-05:00
---


# HTTP (Hypertext Transfer Protocol)이란?

+ 팀 버너스리와 그가 속한 팀은 CERN에서 HTML뿐 아니라 웹 브라우저 및 웹 브라우저 관련기술과 HTTP를 발명하였다.
+ HTTP는 서버와 클라이언트가 인터넷상에서 데이터를 주고받기 위한 프로토콜(Protocol)이다.
+ HTTP는 발전하여 HTTP/2까지 버전이 등장하였다.(자주쓰이는 버전은 HTTP/1.1)


## HTTP 작동방식

+ HTTP는 서버/클라이언트 모델을 따른다.
+ 장점
    - 불특정 다수를 대상으로 하는 서비스에는 적합하다.
    - 클라이언트와 서버가 계속 연결된 형태가 아니기 때문에 클라이언트와 서버간의 최대 연결 수 보다 훨씬 더 많은 요청과 응답을 처리할 수 있다.(Stateless때문)
+ 단점
    - 연결을 끊어버리기 때문에, 클라이언트의 이전 상황을 알 수가 없다.
    - 이러한 상태를 무상태(Stateless)라고 말한다
    - 이러한 특징 때문에 정보를 유지하기 위해서 Cookie와 같은 기술이 등장

## URL(Uniform Resource Locator)
    
+ 인터넷상의 자원의 위치
+ 특정 웹 서버의 특정 파일에 접근하기 위한 경로 혹은 주소


![image](https://cphinf.pstatic.net/mooc/20180119_25/1516354290022wUY3x_PNG/http_-_.PNG)


## HTTP(Hypertext Transfer Protocol)

+ 요청 메서드 : GET, PUT, POST, PUSH, OPTIONS 등의 요청 방식이 온다.
+ 요청 URI : 요청하는 자원의 위치를 명시한다.
+ HTTP 프로토콜 버전 : 웹브라우저가 사용하는 프로토콜 버전이다.


+ GET : 정보를 요청하기 위해 사용 (SELECT)
+ POST : 정보를 밀어넣기 위해 사용 (INSERT)
+ PUT : 정보를 업데이트 하기위해서 사용 (UPDATE)
+ DELETE : 정보를 삭제하기 위해서 사용 (DELETE)
+ HEAD : (HTTP)헤더 정보만 요청한다. 해당 자원이 존재하는지 혹은 서버에 문제가 없는지를 확인하기 위헤서 사용한다.
+ OPTIONS : 웹서버가 지원하는 메서드의 종류를 요청한다.
+ TRACE : 클라이언트의 요청을 그대로 반환한다. 예컨데 echo 서비스로 서버 상태를 확인하기 위한 주 목적으로 사용한다.


출처 : 
+ [네이버 부스트코스](https://www.edwith.org/boostcourse-web/lecture/16661/)