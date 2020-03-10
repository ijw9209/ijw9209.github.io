---
title: "Http 프로토콜"
excerpt: "HTTP 프로토콜"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-10T08:06:00-05:00
---

# HTTP Protocol


## 1. HTTP 프로토콜 이란?

HTTP(Hypertext Transfer Protocol)은 상호간의 정의한 규칙을 의미하며 특정 기기간의
데이터를 주고받기 위해 정의되었다.

웹에서는 브라우저와 서버 간에 데이터를 주고받기 위한 방식으로 HTTP프로토콜을 사용하고 있으며
프런트엔드 개발자라면 필수적으로 알아야함!

## 2. HTTP 프로토콜 특징

HTTP 프로토콜은 상태가 없는 (stateless) 프로토콜 이다.
여기서 상태가 없다라는 말은 **데이터를 주고 받기 위한 각각의 데이터요청이 서로 독립적으로 관리**가 된다는 말이다.
좀 더 쉽게 말해서 이전 데이터 요청과 다음 데이터 요청이 서로 관련이 없다.

이러한 특징 때문에 서버는 세션과 같은 별도의 추가 정보를 관리 하지 않아도 되고,
다수의 요청 처리 및 서버의 부하를 줄일 수 있는 성능상의 이점이 생긴다.

HTTP 프로토콜은 일반적으로 TCP/IP 통신 위에서 동작하며 기본포트는 80번

## 3. HTTP Request & HTTP Response

HTTP 프로토콜로 데이터를 주고 받기 위해서는 아래와 같이 요청(Request)을 보내고 응답(Response)를 받아야함.

![http](https://joshua1988.github.io/images/posts/web/http/request-response.png)

요청과 응답을 이해하기 위해서는 클라이언트와 서버를 이해해야하는데

+ 클라이언트 : 요청을 보내는쪽을 의미 일반적으로 웹관점에서는 브라우저
+ 서버 : 요청을 받는 쪽 일반적으로 데이터를 보내주는 원격지의 컴퓨터

## 4. URL

URL(Uniform Resource Locators)서버에 자원을 요청하기 위해 입력하는 영문주소.

![URL](https://joshua1988.github.io/images/posts/web/http/url-structure.png)

## 5. HTTP 요청 메서드

앞에서 본 URL을 이용하면 서버에 특정 데이터를 요청 할 수 있음. 
요청하는 데이터의 특정 동작을 수행하고 싶으면?
**HTTP 요청 메서드를 이용** (=HTTP Verbs) 라고도 불림 

주요메서드 
+ GET : 존재하는 자원에 대한 **요청**
+ POST : 새로운 자원을 **생성**
+ PUT : 존재하는 자원에 대한 **변경**
+ DELETE : 존재하는 자원에 대한 **삭제**

이와 같이 데이터에 대한 조회.생성.변경.삭제 동작을 HTTP 요청 메서드로 정의할 수 있음.
때에 따라서는 POST 메서드로 PUT , DELETE의 동작도 수행할 수 있음

기타 요청 메서드
+ HEAD : 서버 헤더 정보를 획득 ,GET과 비슷하나 Response Body를 반환하지 않음
+ OPTIONS : 서버 옵션들을 확인하기 위한 요청 . CORS에서 사용

## 6. HTTP 상태 코드

앞에서 살펴본 URL과 요청 메서드가 클라이언트에서 설정할 정보라면 
HTTP 상태코드 (HTTP Stauts Code)는 서버에서 설정해주는 응답(Response) 정보입니다.

상태코드를 잘알면 에러처리를 잘할 수 있기 때문에 중요하다

예를 들어 아래와 같이 사용자 목록을 받아오는 GET 메서드 요청을 날려보면

```
http://domain.com/users
```

위 요청을 보내고 나면 서버에서 응답으로 오는 상태 코드가 2개로 나뉨.
**200(성공)** 과 **404(실패)** 따라서 이 http 상태 코드로 추가적인 로직을 구현할수있음

### 6-1 2xx - 성공

200번대의 상태코드는 대부분 성공
+ 200 : GET 요청에 대한 성공
+ 204 : No Content. 성공했으나 응답 본문에 데이터가 없음
+ 205 : Reset Content. 성공했으나 클라이언트의 화면을 새로 고침하도록 권고
+ 206 : Parial Content. 성공했으나 일부 범위의 데이터만 반환

### 6-2 3xx - 리다이렉션

300번대의 상태코드는 대부분 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새 URL로 리다이렉션을 유도하는 경우

+ 301 : Moved Permanetly , 요청한 자원이 새 URL에 존재
+ 303 : See Other , 요청한 자원이 임시 주소에 존재
+ 304 : Not Modified , 요청한 자원이 변경되지 않았으므로 클라이언트에서 캐싱된 자원을 사용하도록 권고,
         ETag와 같은 정보를 활용하여 변경 여부를 확인

###  6-3 4xx - 클라이언트 에러

400번대 상태 코드는 대부분 클라이언트의 코드가 잘못된 경우. 
유효하지 않은 자원을 요청했거나 요청이나 권한이 잘못된 경우 발생

+ 400 : Bad Request , 잘못된 요청
+ 401 : Unauthorized , 권한 없이 요청 . Authorization 헤더가 잘못된경우
+ 403 : Forbidden, 서버에서 해당 자원에 대해 접근 금지
+ 405 : Method Not Allowed , 허용되지 않은 요청 메서드
+ 409 : Conflict , 최신 자원이 아닌데 업데이트하는경우 ex)파일 업로드 시 버전 충돌

### 6-4 5xx - 서버에러

500번대 상태 코드는 서버쪽에서 오류가 난 경우
+ 501 : Not Implemented , 요청한 동작에 대해 서버가 수행할 수 없는 경우
+ 503 : Service Unvailable, 서버가 과부하 또는 유지 보수로 내려간경우

위에서 본것같이 다시 그림을 보면

![http](https://joshua1988.github.io/images/posts/web/http/http-full-structure.png)

클라이언트는 URL로 서버에 자원을 요청하고 , 서버는 클라이언트에 상태코드와 응답 데이터를 보내준다

+ 출처 : [https://joshua1988.github.io/web-development/http-part1/#%EB%93%A4%EC%96%B4%EA%B0%80%EB%A9%B0](https://joshua1988.github.io/web-development/http-part1/#%EB%93%A4%EC%96%B4%EA%B0%80%EB%A9%B0)