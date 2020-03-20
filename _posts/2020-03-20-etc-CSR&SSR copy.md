---
title: "CSR과 SSR"
excerpt: "CSR과 SSR"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-20T01:15:00
---

# CSR(Client Side Rendering)과 SSR(Server Side Rendering)

## SPA와 MPA

+ SPA (Single Page Application)

하나의 HTML 파일을 기반으로 자바스크립트를 이용해 동적으로 화면의 컨텐츠를 바꾸는 방식의 웹 어플리케이션이다.

+ MPA(Multiple Page Application)

사용자가 페이지를 요청할 때 마다,웹 서버가 요청한 UI와 필요한 데이터를 HTML로 파싱해서 보여주는 방식의 웹 어플리케이션이다.

**SPA**가 사용하는 방식이 **CSR**이고 **MPA**가 사용하는 방식이 **SSR**이다. 

### CSR

![IMAGE](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/frontend/CSR.png)


CSR에선 브라우저가 서버에 HTML과 JS파일을 요청한 후 로드되면 사용자의 상호작용에따라 JS를 이용해서 동적으로 렌더링을 시킨다.
(쉽게 말하면 사용자에 행동에따라 필요한 부분만 다시 읽기 때문에 서버측에서 렌더링하여 전체 페이지를 다시 읽는것 보다 빠른 인터렉션을 기대할 수 있다.)

+ 장점
    - 첫 로딩만 기다리면 , 동적으로 빠르게 렌더링이 되기때문에 사용자경험(UX)가 좋다.
    - 서버에게 요청하는 횟수가 훨씬 적기 때문에 서버의 부담이 덜하다

+ 단점
    - 검색엔진
    JS위주로 돌아가는 프로젝트는 JS엔진이 돌아가지 않으면 원하는 정보를 표시해주지 못함.
    크롬에서 REACT로 만든 웹앱의 소스를 확인하면 , 내용이 비어있다.
    그렇기 때문에 검색엔진 크롤러가 데이터들을 제대로 수집하지 못함 , 하지만 구글의 검색엔진은 자바스크립트 엔진이 내장되어있다. 네이버나 다음 등 검색엔진은 제대로 크롤링 하지 못하기 때문에 SSR을 따로 구현해야함



### SSR

![IMAGE](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/frontend/SSR.png)

SSR에선 브라우저가 페이지를 요청할 때마다 해당 페이지의 관련된 HTML , CSS , JS 파일 및 데이터를 받아와서 렌더링을 시킨다.

+ 장점
    - 초기 로딩속도가 빠르기 때문에 사용자가 컨텐츠를 빨리 볼 수 있다.
    - JS를 이용한 렌더링이 아니기 때문에 검색 엔진 최적화가 가능함.
+ 단점
    - 매번 페이지를 요청할 때마다 새로고침 되기 때문에 사용자 경험(UX)가 SPA에비해 좋지않다.
    - 서버에 매번 요청을 하기 때문에 서버의 부하가 커진다.



## UX와 UI

- **UX(User Experience)** 디자인은 사용자 경험을 의미한다. 사용자가 어떤 제품,시스템 서비스 등 직접적 혹은 간접적으로 이용하면서 느끼는 반응과 행동들과 같은 경험을 총체적으로 설계(사용자가 겪을 경험 중심적인 관점)

- **UI(User Interface)** 디자인은 사용자가 제품을 어떤 방식으로 이용하도록 만드느냐를 디자인하는것 즉, 겉으로 시각화되는 작업이라 보면된다. 사용자가 실제로 마주하게될 디자인 레이아웃등을 아우르는 개념(눈에 보이는 색감, 정렬, 모양과 크기등)

참고 및 출처
+ [CSR(Client Side Rendering)과 SSR(Server Side Rendering)](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/frontend/csr-ssr.md)
+ [UI&UX](http://media.fastcampus.co.kr/knowledge/about-uxuidesign/)    
+ [서버사이드렌더링 & 클라이언트사이드렌더링](https://velog.io/@zansol/%ED%99%95%EC%9D%B8%ED%95%98%EA%B8%B0-%EC%84%9C%EB%B2%84%EC%82%AC%EC%9D%B4%EB%93%9C%EB%A0%8C%EB%8D%94%EB%A7%81SSR-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8%EC%82%AC%EC%9D%B4%EB%93%9C%EB%A0%8C%EB%8D%94%EB%A7%81CSR)