---
title: "[Boostcurse] WAS"
excerpt: "부스트코스 공부하기"
toc: true
toc_sticky: true

categories:
  - BackEnd
  - Boostcurse
tags:
  - BackEnd
  - Boostcurse
last_modified_at: 2020-04-20T08:06:00-05:00
---


# WAS(Web Application Server)

## 클라이언트 / 서버구조

클라이언트(Client)는 서비스(Service)를 제공하는 서버(Server)에게 정보를 요청하여 응답 받은 결과를 사용한다.

![image](https://cphinf.pstatic.net/mooc/20180213_10/151849899068982T3i_PNG/05.png)

## DBMS (DataBase Management System)

다수의 사용자가 데이터베이스 내의 데이터에 접근할 수 있도록 해주는 소프트웨어이다.

![image2](https://cphinf.pstatic.net/mooc/20180122_74/15166087526093WS9P_PNG/1_1_7_DBMS.PNG)


## 미들웨어 (MiddleWare)

클라이언트 쪽에 비즈니스 로직이 많을 경우, 클라이언트 관리(배포 등)으로 인해 비용이 많이 발생하는 문제가 있다.
비즈니스 로직을 클라이언트와 DBMS사이의 미들웨어 서버에서 동작하도록 함으로써 클라이언트는 입력과 출력만 담당하도록 한다.

![image3](https://cphinf.pstatic.net/mooc/20180122_267/1516608805247GN2hK_PNG/1_1_7_.PNG)


## WAS (Web Application Server)

WAS는 일종의 미들웨어로 웹 클라이언트(보통 웹 브라우저)의 요청 중 웹 어플리케이션이 동작하도록 지원하는 목적을 가진다.

![image4](https://cphinf.pstatic.net/mooc/20180122_270/1516606715302CWRJG_PNG/1_1_7_was.PNG)

## WAS의 기본 기능

+ 프로그램 실행환경과 데이터베이스 접속 기능을 제공한다.
+ 여러개의 트랜잭션을 관리한다.
+ 업무를 처리하는 비즈니스로직을 수행한다.

## 웹 서버 vs WAS

+ WAS도 보통 자체적으로 웹 서버의 기능을 내장하고 있다.
+ 현재는 WAS가 가지고 있는 웹 서버도 정적인 콘텐츠를 처리하는 데 있어서 성능상 큰 차이가 없다.
+ 규모가 커질수록 웹 서버와 WAS를 분리한다.
+ 자원 이용의 효율성 및 장애 극복,배포 및 유지보수의 편의성을 위해 웹서버와 WAS를 대체로 분리한다.



## 용어


+ 장애극복기능 : WAS에서 동작하도록 개발자가 만든 프로그램이 오작동이 발생해 WAS자체에 문제가 발생하면
                문제가 있는 WAS를 재시작해야되는데 재시작 할때, 이때 앞단의 웹서버에서 해당 WAS를 이용하지 못하게하고 WAS를 재시작한다면 웹 어플리케이션을 사용하는 사람은 WAS의 문제가 발생하였는지 모르고 이용가능하게하는 처리


출처 : 
+ [https://www.edwith.org/boostcourse-web/lecture/16666/](https://www.edwith.org/boostcourse-web/lecture/16666/)