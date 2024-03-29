---
title: "[정보처리 산업기사 실기] 서술문제 요약"
excerpt: "[정보처리 산업기사 실기] 서술형 요약"
toc: true
toc_sticky: true

categories:
  - etc
  - certificate
tags:
  - etc
  - certificate
last_modified_at: 2022-05-01T08:06:00-05:00
--- 


# 1. 응용 SW 기초 기술 활용

+ 운영체제의 목적
- 처리 능력(Throughput) : 일정 시간 내 시스템이 처리하는 일의 양
- 반환 시간(Turn Around Time) : 시스템에 작업을 의뢰한 시간부터 처리가 완료될 때까지 걸린 시간
- 사용 가능도(Availability) : 시스템을 사용할 필요가 있을 때 즉시 사용 가능한 정도
- 신뢰도(Reliability) : 시스템이 주어진 문제를 정확하게 해결하는 정도


+ 데이터 베이스의 스키마
  - 스키마 : 스키마는 데이터베이스의 구조와 제약조건에 관한 전반적인 명세를 기록한 것

+ 관계형 데이터 베이스의 릴레이션 구조 중 도메인의 개념
  - 도메인 : 하나의 애트리뷰트가 취할 수 있는 같은 타입의 원자(Atomic)값들의 집합

+ 트랜잭션
  - 트랜잭션 : 데이터베이스의 상태를 변화시키는 하나의 논리적 기능을 수행하기위한 작업의 단위 또는 한꺼번에 모두 수행되어야 할 일련의 연산

+ 트랜잭션의 특성 (ACID)
- 원자성 : 트랜잭션의 연산은 모두 반영되도록 완료되든지 전혀 반영되지 않도록 복구 되어야함
- 일관성 : 트랜잭션이 성공하면 언제나 일관성 있는 데이터베이스 상태로 변환
- 독립성,격리성,순차성 : 둘 이상의 트랜잭션이 실행되는 경우 하나의 트랜잭션 실행중 다른 트랜잭션이 끼어들 수 없음
- 영속성,지속성 : 성공적으로 완료된 트랜잭션의 결과는 영구적으로 반영되어야 함

+ 협업 도구의 개념
  - 협업 도구는 개발에 참여하는 사람들이 서로 다른 작업 환경에서 원활히 프로젝트를 수행하도록 도와주는 도구

+ 데이터 마이닝(Data Mining)
  - 대량의 데이터를 분석하여 데이터에 내제된 변수 사이의 상화 관계를 규명하여 일정한 패턴을 찾아내는 기법

+ 프로토콜의 기본요소
 - 구문(Syntax) : 전송하고자 하는 데이터의 형식, 부호화, 신호 레벨 등을 규정
 - 의미(Semantics) : 두 기기 간 효율적이고 정확한 정보 전송을 위한 협조 사항과 오류 관리를 위한 제어 정보 규정
 - 시간(Timing) : 두 기기간 통신 속도, 메세지의 순서 제어 등을 규정

+ 데이터 베이스
 - 데이터 베이스는 공동으로 사용될 데이터를 중복을 배제하여 통합하고, 쉽게 접근하여 처리할 수 있도록 저장장치에 저장하여 사용하여 운영하는 운영데이터 이다.

+ 논리적 독립성
 - 논리적 독립성은 데이터의 논리적 구조를 변경시키더라도 응용프로그램은 영향을 받지 않는 성질이다.

+ WAS
- WAS는 동적 서비스를 제공하거나, 웹 서바와 데이터 베이스 서버 또는 웹서버와 파일 서버사이에서 인터페이스 역할을 수행하는 서버이다.

# 2. UI 테스트

+ UI 기본 원칙
  - 직관성 :  누구나 쉽게 이해하고 사용할 수 있어야 함
  - 유효성 : 사용자의 목적을 정확하고 완벽하게 달성해야함
  - 학습성 : 누구나 쉽게 배우고 익힐 수 있어야 함
  - 유연성 : 사용자의 요구사항을 최대한 수용하고 실수를 최소화 해야함

+ 소프트웨어 품질 목표 중 신뢰성(Reliability)?
- 신뢰성 : 주어진 시간동안 주어진 기능을 오류 없이 수행할 수 잇는 정도

+ 사용성(Usability)
 - 사용자와 컴퓨터 사이에 발생하는 어떠한 행위에 대해 사용자가 정확하게 이해하고 사용하며, 향후 다시사용하고 싶은정도

 # 3. 화면 구현

 + 프로토타입  
 - 프로토타입은 와이어프레임이나 스토리보드 등에 인터랙션을 적용함으로 실제 구현된 것 처럼 테스트가 가능한 동적인 모형

 + 감성공학
 - 감성공학은 제품이나 작업환경을 사용자의 감성에 알맞도록 설계 및 제작하는 기술함

 # 4. 프로그래밍 언어활용

 + 헝가리안 표기법
 - 변수에 자료형을 알 수 있도록 변수 명 앞에 자료형을 의미하는 문자를 표기하여 작성하는 기법

 + 절차적 프로그래밍 언어의 개념 
 - 일련의 처리 절차를 정해진 문법에 따라 순서대로 기술 하는 언어

 + 객체지향 프로그래밍 언어의 개념
 - 현실세계의 객체를 하나의 객체로 만들어, 객체들을 조립하여 프로그램을 작성하는 기법

 + 선언형 언어
 - 프로그램이 수행해야 할 문제를 기술하는 언어
 + 명령형 언어
 - 문제를 해결하기 위한 방법을 기술하는 언어

 + stdlib.h ? 
 - 자료형 변환, 난수 발생, 메모리 할당에 사용되는 기능 제공