---
title: "[Next] Next.js 폰트 적용"
excerpt: "Next.js  폰트 적용 방법"
toc: true
toc_sticky: true

categories:
  - React
  - Next
tags:
  - React
  - Next
last_modified_at: 2022-08-01T08:06:00-05:00
---

# Next.js 다운받은폰트 적용방법

## 1. 폰트 다운

폰트를 구글 폰트 등 무료 사이트에서 다운받는다.

- [https://fonts.google.com/?sidebar.open=&selection.family=Noto+Sans+KR:wght@300](https://fonts.google.com/?sidebar.open=&selection.family=Noto+Sans+KR:wght@300)

하지만 그냥 다운받는다면, 용량이 매우크기때문에

다음과 같은 사이트에서 경량화 폰트를 받는것도 방법이다

- [https://nonria.com/post/104/](https://nonria.com/post/104/)

## 2. Next.js에 적용

`public/static/fonts` 디렉터리를 만들고, 다운받은 폰트 파일을 넣어준다.

그 다음 위와 같은 폴더에 `style.css` 파일을 만든다.

`style.css`에 다음과 같이 @font-face를 작성한다.

아래는 예시이다.

```css
@font-face {
  font-family: "Noto Sans CJK KR";
  font-style: normal;
  font-weight: 100;
  src: url("NotoSansKR-Light.woff2") format("woff2"), url("NotoSansKR-Light.woff")
      format("woff"), url("NotoSansKR-Light.otf") format("truetype");
}

@font-face {
  font-family: "Noto Sans CJK KR";
  font-style: normal;
  font-weight: normal;
  src: url("NotoSansKR-Regular.woff2") format("woff2"), url("NotoSansKR-Regular.woff")
      format("woff"), url("NotoSansKR-Regular.otf") format("truetype");
}

@font-face {
  font-family: "Noto Sans CJK KR";
  font-style: normal;
  font-weight: 500;
  src: url("NotoSansKR-Medium.woff2") format("woff2"), url("NotoSansKR-Medium.woff")
      format("woff"), url("NotoSansKR-Medium.otf") format("truetype");
}

@font-face {
  font-family: "Noto Sans CJK KR";
  font-style: normal;
  font-weight: bold;
  src: url("NotoSansKR-Bold.woff2") format("woff2"), url("NotoSansKR-Bold.woff")
      format("woff"), url("NotoSansKR-Bold.otf") format("truetype");
}
```

## 3. app.js에 import

`app.js`에 `style.css`파일을 import 한다.

## 4. 다음과 같이 적용하면 끝

전역 css 등과 같은 곳에서 다음과 같이 적용하면 적용이 된다.

```css
body {
  font-family: "Noto Sans CJK KR";
  font-weight: 500;
}
```
