---
title: "[Next] Next.js 를 사용하는이유"
excerpt: "Next.js 사용하는 이유"
toc: true
toc_sticky: true

categories:
  - React
  - Next
tags:
  - React
  - Next
last_modified_at: 2022-07-12T08:06:00-05:00
---

# Next.js

## Next.js 의 기본 배경

리액트는 기본적으로 렌더링이 모두 클라이언트 사이드에서 일어난다.
맨 처음 모든 자바스크립트 코드를 로드하기 때문에 화면이 사용자에게 보여지기까지 시간이 오래 걸린다.
그리고 공개적인 웹사이트에서의 컨텐츠 SEO 문제가 있다. 

위의 두 문제를 해결하는 것은 static pre-rendering, 즉 서버 렌더링 방식으로 해결할 수 있다.

Next.js는 서버렌더링을 쉽게 해주는 리액트 프레임워크이다. 

## Next.js의 주요 기능

1. Hot Code Reloading

+ 디스크에 변화가 감지 되면 페이지 재로드

2. Automatic Routing

+ page 폴더안에 파일이 있으면 어떤 URL 이라도 파일 시스템에 매핑됨, 설정이 필요없다.

3. Single File Components 

+ 통합된 styled-jsx를 사용하면 해당 컴포넌트 영역에 스타일을 손쉽게 추가가능

4. Server Rendering

+ 클라이언트로 html을 보내기 전 서버사이드에서 리액트 컴포넌트를 렌더링 할 수있다.

5. Automatic Code Splitting

+ 페이지들은 자기가 필요한 자바스크립트 및 라이브러리들만 렌더링됨. 해당 페이지에 필요한 자바스크립트만 로드

6. Prefetching

+ 두개의 다른 페이지를 연결하는 Link 컴포넌트는 백그라운드에서 자동으로 페이지 리소스를 사전 패치하는 prefetch프로퍼티를 지원

7. Dynamic Components 

+ 자바스크립트 모듈과 리액트 컴포넌트를 동적으로 임포트할 수 있다.

8. Static Exports 

+ Next.js는 next export 명령어를 통해 모든 정적 사이트를 export 할수 있게 해준다.


## 기본 설치방법

```
npx create-next-app@latest
# or
yarn create next-app

```

typescript

```
npx create-next-app@latest --typescript
# or
yarn create next-app --typescript


```


설치후

```
npm run dev 

or 

yarn dev

```
