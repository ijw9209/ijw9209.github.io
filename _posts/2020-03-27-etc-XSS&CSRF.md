---
title: "XSS와 CSRF"
excerpt: "XSS와 CSRF"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-03-27T01:15:00
---


# XSS와 CSRF

## XSS(Cross Site Script , 사이트간 스크립팅)

웹사이트 관리자가 아닌 사람이 웹사이트에 악성 스크립트를 삽입할 수있는 취약공격기법.
사용자로 부터 받은 입력을 제대로 검증하지 않을때 나타나고 사용자의 쿠키정보 및 세션ID 정보를 탈취할수있다.

+ 저장 XSS : 웹사이트에 취약점이 있는 웹 서버에 스크립트를 저장시켜서 해당 웹사이트를 요청하는 사용자로 하여금 스크립트를 실행하게하는 기법

+ 반사 XSS : 검색을 사용할때 결과가 없으면 브라우저에서 입력한 값을 문서에 포함하여 응답하는데 이를 사용하여 스크립트를 실행하는 기법으로 악성 URL을 배포하여 클릭하도록 유도하는 방법

+ DOM 기반 XSS : 공격 스크립트가 DOM 생성의 일부로 실행되면서 공격하는 기법. 반사 XSS와 마찬가지로 악성 URL을 배포하여 클릭하도록 유도.

## XSS대응방안

+ 입/출력 값 검증 무효화 : 스크립트를 실행할 때 `<script>` 태그를 사용하니 <를 `&lt`;로 바꾼다거나 하는 방법으로 무효화 시킬수 있다

+ 보안 라이브러리 사용 : 입/출력이 스크립트를 실행하는지에 대한 필터를 구현한 기존라이브러리를 사용.


## CSRF (Cross Site Request Forgery , 사이트간 요청변조)

사용자가 의도치 않게 공격자가 의도한 행동을 하여 취약점을 노출 시키거나 수정/삭제/생성 등을 하게 만드는 공격
메일을 열어보거나 악성 사이트에 접근했을 때 특정한 요청을 하는 CSRF 스크립트를 실행하는 방식 

+ `www.mybank.com`에 접속해있는 상태이고
+ 이 사이트에서 송금할때 `http://www.mybank.com/transfer?to=<계좌번호>&amount=<액수>` 형식으로 보낸다하면
+ `www.cute-cat.org`란 악성사이트에 접속
+ 해당 사이트 관리자가 URL 쿼리 방식을 알고있다면 CSRF 스크립트를 사이트에 넣을 수 있다.
+ 사이트에 접속하면 해당 스크립트를 실행하게되고 `www.mybank.com`에 요청이 가게되서 송금하게된다

## CSRF 대응방안

+ referrer 검증 : 요청 헤더에 있는 referrer 속성을 검증하여 신뢰할 수 있는 도메인에서 들어오는 요청인지 검색
+ CSRF 토큰 : 랜덤한 수를 사용자의 세션에 저장하여 사용자의 모든 요청(Request)에 대하여 서버단에서 검증하는 방법.
+ 캡챠(Captcha) 사용 : 사용자와의 상호작용을 통해 숫자/문자를 입력하여 검증한다


출처 :
+ [https://github.com/baeharam/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/security/xss-csrf.md)
+ [https://sj602.github.io/2018/07/14/what-is-CSRF/](https://sj602.github.io/2018/07/14/what-is-CSRF/)
