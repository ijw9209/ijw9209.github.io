---
title: "[Next] Next.js 공식문서 공부2(CSS)"
excerpt: "Next.js Assets, Metadata, and CSS"
toc: true
toc_sticky: true

categories:
  - React
  - Next
tags:
  - React
  - Next
last_modified_at: 2022-07-14T08:06:00-05:00
---

# Next.js Assets, Metadata, and CSS

## 1. Setting

우선 CREATE-NEXT-APP으로 개발환경 준비하기

```
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/assets-metadata-css-starter"
```

next 공식문서에 있는 코드를 원하는 디렉토리에 터미널로 설치한다.

설치후 

```
npm run dev
```
명령어로 실행할 수 있다.



## 2. Assets , Download Your Profile Picture

Next.js는 이미지와 같은 정적파일을 지원한다. 상위에 있는 `public` 디렉토리에 파일을
위치시키고 `public` 내부의 파일은 `pages` 와 유사하게 루트에서 참조할 수 있다.

+ 1. 아무 이미지나 준비한다. (jpg)
+ 2. `public` 디렉토리 안에 `images` 폴더를 만든다.
+ 3. `profile.jpg` 파일을 `public/images` 폴더안에 위치시킨다.
+ 4. 이미지의 사이즈는 400px by 400px


### 2-1. Image Component and Image Optimization

Next.js 는 `<img>` 태그를 진화시킨 이미지 컴포넌트를 지원한다. 
또한 WebP와 같은 최신 형식으로 이미지 최적화와 크기조정을 지원한다. 

### 2-2. Using the Image Component

이미지 컴포넌트는 다음과 같이 사용한다.

```js
import Image from 'next/image';

const YourComponent = () => (
  <Image
    src="/images/profile.jpg" // Route of the image file
    height={144} // Desired size with correct aspect ratio
    width={144} // Desired size with correct aspect ratio
    alt="Your Name"
  />
);

```


## 3. Metadata

`<title>` 태그와 같은 페이지의 메타데이터를 변경하기 원한다면, 

`pages/index.js`에 다음과 같은 코드 찾는다

```js
<Head>
  <title>Create Next App</title>
  <link rel="icon" href="/favicon.ico" />
</Head>

```

Next.js 에서는 소문자 `<head>` 가아닌 `<Head>` 컴포넌트를 사용한다.

`<Head>` 컴포넌트는 `next/head` 모듈에서 사용할수 있다.

### 3-1. Adding Head to first-post.js


`pages/posts/first-post.js` 파일에 다음과 같이 작성한다.

```js
import Head from 'next/head';
```

또한 내용도 다음과 같이 수정한다.

```js
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
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

실행하여 접근해보면 `head` 태그와 `title`태그가 추가된 것을 확인 할 수 있다.


## 4. Third-Party JavaScript


### 4-1. Adding Third-Party JavaScript

보통 자바스크립트에서는 스크립트를 다음과 같이 추가한다.

```js
<Head>
  <title>First Post</title>
  <script src="https://connect.facebook.net/en_US/sdk.js" />
</Head>

```

이렇게 스크립트를 추가한다면 동일한 페이지에서 가져온 다른 자바스크립트 코드와
로드될 시기를 정확하게 알 수가 없다. 특정 스크립트가 렌더링을 차단하고 페이지 콘텐츠를 지연시킬경우에 성능에 상당한 영향이 생긴다.


### 4-2. Using the Script Component

Next.js에서는 `<script>` 태그를 확장시킨 `<Script>` 컴포넌트를 사용한다.

`pages/posts/first-post.js` 에 다음과 같이 입력한다.

```js
import Script from 'next/script';

```

`FirstPost` 컴포넌트도 다음과 같이 변경한다.


```js
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
      <Script
        src="https://connect.facebook.net/en_US/sdk.js"
        // strategy="lazyOnload"
        onLoad={() =>
          console.log(`script loaded correctly, window.FB has been populated`)
        }
      />
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

`<Script>` 컴포넌트는 다음과 같은 속성값들을 가진다.

+ `strategy` 서드파티 스크립트의 로드 시간을 통제한다. `lazyOnload`는 브라우저가 이 스크립트를 느리게 로딩하도록 설정한다.
+ `onLoad` 는 스크립트가 완료된 직후 자바스크립트 코드를 실행하는데 사용된다. 이 예제에서는 로드 완료 콘솔을 찍는데 사용되었다.


## 5. CSS Styling


Next.js 는 styled-jsx 및 styled-components 또는 emotion 라이브러리도 지원한다.


### 5-1. Layout Component

먼저 모든 페이지에 공유해서 사용할 수 있는 Layout 컴포넌트를 추가한다.

+ 상위 디렉토리에 `components` 폴더를 만든다.
+ `components` 폴더안에 `layout.js` 파일을 만들고 아래와 같은 내용을 작성한다.

```js
export default function Layout({ children }) {
  return <div>{children}</div>;
}
```


`pages/posts/first-post.js` 파일은 다음과 같이 작성한다.

```js
import Head from 'next/head';
import Link from 'next/link';
import Layout from '../../components/layout';

export default function FirstPost() {
  return (
    <Layout>
      <Head>
        <title>First Post</title>
      </Head>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </Layout>
  );
}

```

### 5-2 Adding CSS

`components/layout.module.css` 파일을 만들고 다음과 같이 추가한다.

```css
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}

```

+ CSS 모듈을 사용하려면 파일이름이 반드시 `.module.css`로 끝나야한다.!!


`components/layout.js`파일을 다음과 같이 수정한다.
```js
import styles from './layout.module.css';

export default function Layout({ children }) {
  return <div className={styles.container}>{children}</div>;
}


```

### 5-3 Automatically Generates Unique Class Names

CSS 모듈은 고유한 클래스이름을 자동으로 생성하여 한 클래스 이름 충돌에 걱정할 필요가 없다.

![image](https://nextjs.org/static/images/learn/assets-metadata-css/devtools.png)


## 6. Global Styles

CSS 모듈은 컴포넌트-레벨의 스타일로 사용된다. CSS를 모든 페이지에 로드되도록 원한다면 다음과 같이 작성하면 된다.

+ top-level 에 `styles` 디렉토리를 만들고, `global.css` 파일을 안에 만든다.
+ 다음과 같은 내용을 추가한다.

```css
html,
body {
  padding: 0;
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen, Ubuntu,
    Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
  line-height: 1.6;
  font-size: 18px;
}

* {
  box-sizing: border-box;
}

a {
  color: #0070f3;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

img {
  max-width: 100%;
  display: block;
}

```

마지막으로 `pages/_app.js` 에 import 시킨다.

```js
import '../styles/global.css';

export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />;
}

```

[http://localhost:3000/posts/first-post](http://localhost:3000/posts/first-post) 경로로가면 다음과 같은 화면을 확인 할 수 있다.

![image23](https://nextjs.org/static/images/learn/assets-metadata-css/global-styles.png)


## 7. Polishing Layout

다음강의로 넘어가기전에 페이지의 style을 다듬자.


### 7-1. Update `components/layout.module.css`

`components/layout.module.css` 를 다음과 같이 변경한다.

```css
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}

.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.backToHome {
  margin: 3rem 0 0;
}
```

### 7-2. Create `styles/utils.module.css`

`styles/utils.module.css`를 생성하고 다음과 같이 작성한다.


```css

.heading2Xl {
  font-size: 2.5rem;
  line-height: 1.2;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingXl {
  font-size: 2rem;
  line-height: 1.3;
  font-weight: 800;
  letter-spacing: -0.05rem;
  margin: 1rem 0;
}

.headingLg {
  font-size: 1.5rem;
  line-height: 1.4;
  margin: 1rem 0;
}

.headingMd {
  font-size: 1.2rem;
  line-height: 1.5;
}

.borderCircle {
  border-radius: 9999px;
}

.colorInherit {
  color: inherit;
}

.padding1px {
  padding-top: 1px;
}

.list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.listItem {
  margin: 0 0 1.25rem;
}

.lightText {
  color: #666;
}


```

### 7-3. Update `components/layout.js`


`components/layout.js`를 다음과 같이 변경한다. 

```jsx
import Head from 'next/head';
import Image from 'next/image';
import styles from './layout.module.css';
import utilStyles from '../styles/utils.module.css';
import Link from 'next/link';

const name = 'Your Name';
export const siteTitle = 'Next.js Sample Website';

export default function Layout({ children, home }) {
  return (
    <div className={styles.container}>
      <Head>
        <link rel="icon" href="/favicon.ico" />
        <meta
          name="description"
          content="Learn how to build a personal website using Next.js"
        />
        <meta
          property="og:image"
          content={`https://og-image.vercel.app/${encodeURI(
            siteTitle,
          )}.png?theme=light&md=0&fontSize=75px&images=https%3A%2F%2Fassets.vercel.com%2Fimage%2Fupload%2Ffront%2Fassets%2Fdesign%2Fnextjs-black-logo.svg`}
        />
        <meta name="og:title" content={siteTitle} />
        <meta name="twitter:card" content="summary_large_image" />
      </Head>
      <header className={styles.header}>
        {home ? (
          <>
            <Image
              priority
              src="/images/profile.jpg"
              className={utilStyles.borderCircle}
              height={144}
              width={144}
              alt={name}
            />
            <h1 className={utilStyles.heading2Xl}>{name}</h1>
          </>
        ) : (
          <>
            <Link href="/">
              <a>
                <Image
                  priority
                  src="/images/profile.jpg"
                  className={utilStyles.borderCircle}
                  height={108}
                  width={108}
                  alt={name}
                />
              </a>
            </Link>
            <h2 className={utilStyles.headingLg}>
              <Link href="/">
                <a className={utilStyles.colorInherit}>{name}</a>
              </Link>
            </h2>
          </>
        )}
      </header>
      <main>{children}</main>
      {!home && (
        <div className={styles.backToHome}>
          <Link href="/">
            <a>← Back to home</a>
          </Link>
        </div>
      )}
    </div>
  );
}

```

### 7-4. Update `pages/index.js`

`page/index.js`를 다음과 같이 변경한다.

```jsx
import Head from 'next/head';
import Layout, { siteTitle } from '../components/layout';
import utilStyles from '../styles/utils.module.css';

export default function Home() {
  return (
    <Layout home>
      <Head>
        <title>{siteTitle}</title>
      </Head>
      <section className={utilStyles.headingMd}>
        <p>[Your Self Introduction]</p>
        <p>
          (This is a sample website - you’ll be building a site like this on{' '}
          <a href="https://nextjs.org/learn">our Next.js tutorial</a>.)
        </p>
      </section>
    </Layout>
  );
}
```

+ [https://nextjs.org/learn/basics/assets-metadata-css](https://nextjs.org/learn/basics/assets-metadata-css)