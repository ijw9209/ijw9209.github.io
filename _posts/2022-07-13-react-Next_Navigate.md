---
title: "[Next] Next.js 공식문서 공부"
excerpt: "Next.js Navigate Between Pages"
toc: true
toc_sticky: true

categories:
  - React
  - Next
tags:
  - React
  - Next
last_modified_at: 2022-07-13T08:06:00-05:00
---

# Next.js Navigate Between Pages

## 1. next-blog 설치

우선 CREATE-NEXT-APP으로 개발환경 준비하기

```
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/navigate-between-pages-starter"
```

next 공식문서에 있는 예제를 원하는 디렉토리에 터미널로 설치한다.

설치후 

```
npm run dev
```
명령어로 실행할 수 있다.



## 2. Pages in Next.js

기본적으로 `pages/index.js` 가 `/` 루트 경로이다.
새로 `pages/posts/first-post.js` 폴더와 파일을 만들어보자

`first-post.js` 파일에 다음과 같이 작성한다.

```jsx
export default function FirstPost() {
  return <h1>First Post</h1>;
}

```

[http://localhost:3000/posts/first-post](http://localhost:3000/posts/first-post)


작성후 위와 같은 경로로들어가면 

![image](https://nextjs.org/static/images/learn/navigate-between-pages/first-post.png)

이런 화면을 볼 수 있다.

next.js의 경로는 `pages` 디렉토리와 관련하여 경로가 만들어진다.


## 3. Link Component

Next.js는 Link 컴포넌트를 이용해 다른 페이지간 이동을 구현할 수 있다. 

먼저 `pages/index.js`에 `Link` 컴포넌트를 import 시킨다.

```js
import Link from 'next/link';
```

`pages/index.js`파일 안에 타이틀 부분에 `h1` 태그를 찾아서

```html
<h1 className="title">
  Learn <a href="https://nextjs.org">Next.js!</a>
</h1>

```

다음과 같은 코드로 변환한다.

```js

<h1 className="title">
  Read{' '}
  <Link href="/posts/first-post">
    <a>this page!</a>
  </Link>
</h1>

```

`{' '}`는 빈공간을 띄우기 위해 사용한다.

위와 같이 변환 후 `pages/posts/first-post.js`도 다음과 같은 코드로 변환한다.


```js
import Link from 'next/link';

export default function FirstPost() {
  return (
    <>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </>
  );
}

```

![image1](https://nextjs.org/static/images/learn/navigate-between-pages/links.gif)


변환 후 실행해보면 다음과 같은 이미지를 볼 수 있다.

`Link` 컴포넌트는 클라이언트 사이드 네비게이션이다. 클라이언트 사이드 네비게이션은 브라우저를 더욱 더
빠르게 띄우기 위해서 사용한다.

클라이언트 사이드 렌더링을 확인하려면 개발자 도구를 키고 `<html>` 태그의 css의 `background`를 바꿔서

다음과 같이 확인해 볼수 있다.

![image2](https://nextjs.org/static/images/learn/navigate-between-pages/client-side.gif)

페이지가 변해도 배경색은 렌더링되지 않고 바뀌는 부분만 렌더링 되는 것 을 확인 할 수 있다.


+ [https://nextjs.org/learn/basics/navigate-between-pages](https://nextjs.org/learn/basics/navigate-between-pages)