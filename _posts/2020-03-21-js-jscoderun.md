---
title:  "JS 엔진이 코드를 실행하는 과정"
excerpt: "JS 엔진이 코드를 실행하는 과정"
toc: true
toc_sticky: true

categories:
  - js
tags:
  - js
last_modified_at: 2020-03-21T08:06:00-05:00
---

# 자바스크립트 엔진이 코드를 실행하는 과정

자바스크립트를 실행하기 위해선 자바스크립트 엔진이 필요하고 웹브라우저는 자바스크립트 엔진을 내장하고 있다. 브라우저마다 엔진의 종류가 다르지만 코드를 실행하는 방식은 비슷하기 때문에 보통 어떻게 실행하는지 알아두는것이 좋다.

![image](https://github.com/baeharam/Must-Know-About-Frontend/raw/master/images/javascript/engine-overview.png)


+ 소스코드를 만나면 파싱하여 **AST(Abstract Syntax Tree,추상 구문 트리)**로 변환한다
+ **인터프리터(Interpreter)**는 AST를 기반으로 **바이트코드(Bytecode)**를 생성 한다.
+ 인터프리터가 바이트코드를 실행할 때, 자주 사용되는 함수 및 타입정보등이 있는 **프로파일링데이터(Profiling data)**와 같이 **최적화 컴파일러(Optimizing compiler)** 에게 보낸다. 
+ 최적화 컴파일러는 프로파일링 데이터를 기반으로 **최적화된 코드(Optimizing code)를 생성** 
+ 하지만 , 프로파일링 데이터 중에 **잘못된 부분이 있다면 최적화 해제(Deoptimize)**를 하고 다시 바이트코드를 실행해서 이전 동작을 반복한다


## 용어

+ 추상 구문 트리 : 추상구문트리는 프로그래밍 언어로 작성된 소스코드의 추상, 구문 구조의 트리이다. 이 트리의 각 노드는 소스 코드에서 발생되는 구조를 나타낸다. 구문이 추상적이라는 의미는 실제 구문에서 나타나는 모든 세세한 정보를 나타내지 않는다는 것을 의미한다.

+ 인터프리터 : 인터프리터는 프로그램의 소스코드를 바로 실행하는 컴퓨터 프로그램 또는 환경을 말한다. 기계어로 변환하는 컴파일과는 대비된다. 
인터프리터는 다음의 과정가운데 적어도 한가지 기능을 가진 프로그램이다
1. 소스코드를 직접실행한다
2. 소스코드를 효율적인 다른 중간 코드로 변환하고, 변환한것을 바로 실행한다.
3. 인터프리터 시스템의 일부인 컴파일러가 만든, 미리 컴파일된 저장코드의 실행을 호출한다.

+ 바이트코드 : 바이트코드는 특정 하드웨어가 아닌 가상컴퓨터에서 돌아가는 실행 프로그램을 위한 이진 표현법이다. 하드웨어보다 소프트웨어에서 처리되기때문에 , 보통 기계어보다 추상적이다.

출처
+ [https://github.com/baeharam/](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/frontend/engine.md)
+ [추상구문트리-위키피디아](https://ko.wikipedia.org/wiki/%EC%B6%94%EC%83%81_%EA%B5%AC%EB%AC%B8_%ED%8A%B8%EB%A6%AC)
+ [인터프리터-위키피디아](https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0)
+ [바이트코드-위키피디아](https://ko.wikipedia.org/wiki/%EB%B0%94%EC%9D%B4%ED%8A%B8%EC%BD%94%EB%93%9C)