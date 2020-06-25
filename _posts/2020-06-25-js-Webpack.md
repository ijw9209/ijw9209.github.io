---
title: "Webpack 기초"
excerpt: "Webpack 기초"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-06-25T08:06:00-05:00
---

# Webpack개념잡기

## Webpack이란?

웹팩을 알기 위해서는 모듈 번들러(Module Bundler)가 무엇인지 알아야한다

### Module

+ 프로그램을 구성하는 구성 요소의 일부
+ 관련된 데이터와 함수들이 묶여서 모듈을 형성하고 파일 단위로 나뉘는것이 일반적
+ 모듈화 프로그래밍은 기능별로 파일을 나눠가며 프로그래밍을 하는것으로 유지 보수가 쉽다는 장점이있다.

### Bundler

+ 번들러는 지정한 단위로 파일들을 하나로 만들어서 요청에 대한 응답으로 전달할 수 있는 환경을 만들어주는 역할을 한다.
+ 번들러를 사용하면 소스 코드를 모듈별로 작성할 수 있고 모듈간 외부 라이브러리의 의존성도 쉽게 관리할 수 있다.


### Webpack

+ 웹팩(Webpack)은 자바스크립트 정적 모듈 번들러(Static Module Bundler)이다.
+ 웹팩에서 모든 것은 모듈이다. 자바스크립트, 스타일, 이미지등 모든것을 자바스크릅트 모듈로 로딩해서 사용한다.
+ 웹팩의 주요 네 가지 개념으로 **Entry, Output, Loader, Plugin**이 있다.


1. **entry**
+ 의존성 그래프의 시작점을 웹팩에서는 엔트리(Entry)라고 한다.
+ 웹팩은 엔트리를 통해 필요한 모듈을 로딩하고 하나의 파일로 묶는다.
+ 여러개의 엔트리가 존재할 수 있다.

2. **Output**
+ 엔트리에 설정한 자바스크립트 파일을 시작으로 하나로 묶는다. 그 후 번들된 결과 물을 처리할 위치를 output에 기록한다.

3. **Loader** 
+ 웹팩은 오직 JavaScript와 Json만 이해할 수 있다.
+ 로더는 다른 Type의 파일(img, font, stylesheet 등)을 웹팩이 이해하고 처리 가능한 모듈로 변환 시키는 작업을 한다. 

4. **Plugin**
+ 로더가 파일단위로 처리하는 반면 플러그인은 번들된 결과물을 처리한다
+ 로더가 변환하는 동안 플러그인은 bundle optimization, asset management and injection of environment와 같은 일을 진행할 수 있다.


출처 :

+ [https://velog.io/@hih0327/Webpack-%EA%B8%B0%EC%B4%88](https://velog.io/@hih0327/Webpack-%EA%B8%B0%EC%B4%88)