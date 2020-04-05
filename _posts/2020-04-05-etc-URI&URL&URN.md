---
title: "URI & URL & URN"
excerpt: "URI & URL & URN"
toc: true
toc_sticky: true

categories:
  - etc
tags:
  - etc
last_modified_at: 2020-04-05T08:06:00-05:00
---

# URI & URL & URN


![image](https://media.vlpt.us/post-images/pa324/43314730-092e-11ea-9e05-cf069c31c421/image.png)

## URL (Uniform Resource Locator)

네트워크 상에 자원이 어디에 있는지를 알려주기 위한 규약이다. URL은 웹사이트 주소 뿐만 아니라 컴퓨터 네트워크 상의 자원을 모두 나타낼 수 있다.
그 주소로 접속하려면 해당 URL에 맞는 프로토콜을 알아야한다. 또한 동일한 프로토콜로 접속해야한다.  


+ 자원
+ 예전에는 URL이 가르키는것은 파일소스
+ 요즘은 Rewrite등의 아파치,톰캣 등의 핸들러때문에 자원이라부름
+ 웹사이트 주소가 요청하는 파일이라기 보다는, 구분자로 보는것
+ 웹 상에 서비스를 제공하는 각 서버들에 있는 파일의 위치를 표시하기 위한것


## URI ( Uniform Resource Identifier) 

+ 통합 자원 식별자
+ 인터넷에 있는 자원을 나타내는 유일한 주소
+ URI의 존재는 인터넷에서 요구되는 기본조건, 인터넷 프로토콜에 항상 붙어다님 
+ URI의 하위에 URL, URN이 있다 
+ URI의 보편적인 형태가 URL인데 URI의 부분집합이라 볼 수 있다. 
+ http://test.com/test.pdf?docid=111 이라는 주소는 URI이지만 URL은 아님
 - http://test.com/test.pdf 까지 URL임(주소의 위치) 
+ http://test.com/test.pdf?docid=111 , http://test.com/test.pdf?docid=112 는 같은 URL을 가지고 다른 URI를 가짐 


## URN (Uniform Resource Name)

+ 위치와 상관없이 리소스의 이름값을 사용해서 접근하는 방식
+ 노출된 URL은 http://blog/syun/222 인데 http://blog.com/syun/list/323 으로 요청을 보내면 404 response를 받는다 이를 보완하기 위해서 위치정보와는 무관하게 리소스를 찾을 수 있게 해주는 방식
+ 해당 리소스의 위치정보가 아닌 실제 리소스의 이름으로 사용하는 방식


정리하자면 
+ URI에는 URL,URN이 포함된다. URL은 URI 이지만, URI는 URL이 아니다
+ URL은 인터넷 상의 자원위치를 나타낸다
+ URI는 인터넷상의 자원을 식별하기 위한 문자열의 구성 

출처 : 
+ [https://velog.io/@pa324/](https://velog.io/@pa324/%EA%B0%9C%EB%B0%9C%EC%83%81%EC%8B%9D-URI-URL-%EC%B0%A8%EC%9D%B4-%EC%A0%95%EB%A6%AC)

+ [https://hyunalee.tistory.com/2](https://hyunalee.tistory.com/2)