---
title: "[네트워크] URL을 입력하고 벌어지는 일"
excerpt: "URL을 입력하고 벌어지는 일"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-08-30T08:06:00-05:00
---

# URL을 입력하고 벌어지는 일

1. URL을 웹 브라우저의 주소창에 입력한다.
2. 웹 브라우저가 URL을 해석하고, 문법에 맞지 않으면 기본 엔진으로 검색
3. 문법에 맞으면 URL의 호스트 부분을 인코딩함
4. **HSTS(HTTP Strict Transport Security)** 목록을 확인하고 있으면 HTTPS로, 없으면 HTTP로 요청
5. DNS(Domain Name Server)조회
    + 브라우저/로컬 캐시 확인해서 도메인에 해당하는 IP가 있는지 확인한다.
    + 없으면 OS에게 DNS 서버에 요청하라고 지시
    + DNS 서버는 해당 도메인에 해당하는 IP를 돌려줌
6. TCP 소켓을 열고 **3-way handshake**로 연결을 설정한다.
7. HTTPS 요청이라면 **TLS(Transport Layer Security) handshake**과정을 통해 세션키를 생성한다.
8. 세션이 유지되는 동안 서버에게 요청하고 응답을 받는 과정을 반복한다.
    + 응답 상태코드에 따라 다르게 처리한다.
    + 응답을 디코딩(Decoding)하고 캐싱 가능하다면 캐싱한다.
9. 웹 브라우저는 응답받은 HTML/CSS/JS 및 이미지, 폰트 등의 리소스를 사용하여 렌더링한다.
10. 서버와의 세션이 종료되면 **4-way handshake**로 연결을 종료한다.


+ 용어 정리
    - **URL** : 네트워크 상에 자원이 어디에 있는지 알려주기위한 규약, URL은 웹사이트 주소 뿐만 아니라 컴퓨터 네트워크 상의 자원을 모두 나타낼 수 있다.
    - **HSTS(HTTP Strict Transport Security)** : HTTPS를 강제하는 사이트의 경우 HTTP로 접근할때, 302 Redirect하는 경우가 많음. 유저(브라우저)에게 HTTPS 요청만 허용함을 알려주는 것을 HSTS라고함.(응답 Header에 추가)
    - **TCP 3-way Handshake** : 
        * TCP는 장치들 사이에 논리적인 접속을 성립(establish) 하기 위하여 three-way handshake를 사용한다.
        * TCP 3 Way Handshake는 TCP/IP 프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정임.
    - **TLS/SSL** : SSL(Secure Sockets Layer)은 Certificat Authority(CA)라 불리는 서드 파티로 부터 서와
    클라이언트의 인증을 하는데 사용, 주로 전송계층과 응용계층 사이에서 보안조치를 하는데 사용하게 된다. 우리들이 많이 사용하는 **https://**는 SSL을 사용하는 경우를 의미한다. TLS(Transprot Layer Security )로 최근에 부르는데 SSL은 과거 명칭임
+ 출처

- [https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/network/type-url-process.md](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/network/type-url-process.md)
- [HSTS](https://akageun.github.io/2018/03/07/hsts.html)
- [TCP 3-way Handshake](https://mindnet.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-22%ED%8E%B8-TCP-3-WayHandshake-4-WayHandshake)
- [TLS/SSL](https://hanjungv.github.io/2017-11-07-1_CS_SSL/)