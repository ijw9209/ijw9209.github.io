---
title: "[Vue] Vue js? "
excerpt: "[Vue] Vue js?"
toc: true
toc_sticky: true

categories:
  - Vue
  - etc
tags:
  - Vue
  - etc
last_modified_at: 2020-03-03T08:59:00
---

# Vue.js 란?

## 1. Vue.js 란 ?

MVVM 패턴의 ViewModel 레이어에 해당하는 화면단 라이브러리

![vue](https://joshua1988.github.io/images/posts/web/vuejs/view-model.png)

특징

- 데이터 바인딩과 화면단위를 컴포넌트 형태로 제공하며 , 관련 API를 지원하는데 궁극적인 목표
- 양방향 데이터 바인딩
- 하지만 컴포넌트의 통신은 React의 단방향 데이터 흐름(부모 > 자식) 을 사용
- 다른 프런트 앤드 프레임워크와 비교했을 때 상대적으로 가볍고 빠르다.
- 초기에 배우기 쉬움

## 2. MVVM 패턴

Backend 로직과 Client의 마크업 & 데이터 표현단을 분리하기 위한 구조,
전통적인 MVC방식에 기인하였다.
화면 앞단의 화면 동작 관련 로직과 뒷단의 DataBase 데이터 처리 및 서버로직을 분리하고 , 뒷단에서 넘어온 데이터를 Model에 담아 View로 넘겨주는 중간지점이다.

![vue](https://joshua1988.github.io/images/posts/web/vuejs/mvvm-pattern.png)

- [출처] : (https://joshua1988.github.io/web-development/vuejs/vuejs-tutorial-for-beginner/#vuejs-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0)
