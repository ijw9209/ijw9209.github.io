---
title: "[정보처리산업기사] 응용 SW 기초 기술 활용 02 /  애플리케이션 설계 01"
excerpt: "응용 SW 기초 기술 활용  /  애플리케이션 설계"
toc: true
toc_sticky: true

categories:
  - etc
  - certificate
tags:
  - etc
  - certificate
last_modified_at: 2022-02-17T08:06:00-05:00
---


# TCP / IP 프로토콜 (2022-02-17)

+ TCP/IP는 TCP와 IP 프로토콜만을 지칭하는 것이아니라 UDP, ICMP, ARP, RARP 등 관련된 프로토콜을 통칭한다.
+ TCP와 UDP의 가장 큰 차이점은 데이터 전송의 신뢰성에 있다.
+ 인터넷 연결을 위한 프로토콜이다.


## IP의 헤더(Header)

+ IP헤더의 길이는 최소 2Byte에서 최대 60Byte이다.

+ IHL(IP Header Length) : 헤더의 길이를 기록
+ TOS(Type Of Service) : 요구되는 서비스 품질을 기록
+ Total Packet Length : IP 헤더 및 데이터를 포함한 IP 패킷 전체의 길이를 바이트 단위로 길이를 표시 

## TCP 헤더

+ Source Port Number , Destination Port Number, Sequence Number ...


## UDP 헤더

+ Source Port Number , Destination Port Number, UDP length, UDP Checksum


# TCP/ IP 응용 계층(인터넷 서비스) 

## (1) 전자 우편 (SMTP)

+ 편지를 받을때는 POP 서버 편지를 보낼때는 SMTP 서버를 이용
+ 전자우편을 주고 받을때는 송신자와 수신자가 동시에 인터넷에 연결되어 있지않아도됨

## (2) HTTP 서비스

+ html 문서를 송수신하기 위한 표준 프로토콜

## (3) FTP 서비스

+ 파일 전송 프로토콜
+ 파일 업로드와 다운로드 
+ 계정 없이 접속할 수 있는 FTP 서버를 Anonymous(익명) FTP 서버라고함

## (4) TELNET

+ 원격 접속 서비스
+ 가상 터미널 기능을 갖는다.


# TCP 계층 전송계층

## (1) TCP(Transmission Control Protocol)

+ 전송 데이터의 흐름을 제어, 데이터의 에러 유무를 검사
+ 수신측에서 잘못 전송된 패킷에 대해 재전송을 요구

## (2) UDP(User Datagram Protocol)

+ 비 접속형 통신 제공
+ 통신 수립 단계가 없음


## (3) RTP

# IP 계층

## (1) IP(Internet Protoco)

+ 패킷에 주소를 지정, 경로를 설정

## (2) ARP(Address Resolution Protocol)

+ IP주소를 -> 물리적주소(MAC) 주소로 바꿈

## (3) RARP(Reverse Address Resolution Protocol)

+ ARP와 반대로 물리적주소를 -> IP 주소로

## (4) ICMP(Internet Control Message Protocol)

+ 오류 상태 통지, 예상치 못한 상황에대한 정보를 관리 (PING)

## DNS (Domain Name Server)

+ 호스트 컴퓨터이름 , 소속기관이름 , 소속기관 종류, 소속 국가명 순


# 어플리케이션 설계 - 소프트웨어 생명주기(2022-02-19)

## 소프트웨어 생명주기(Software Life Cycle)

+ 소프트웨어 생명 주기는 소프트웨어를 개발하기 위한 설계, 운용, 유지보수 등의 과정을 각 단계 별로 나눈것

+ 대표적인 생명 주기 모형은 폭포수 모형, 프로토타입 모형, 나선형 모형, 애자일 모형 등이 있다.


### 폭포수 모형(Waterfall Model)

+ 폭포수 모형은 각 단계를 확실히 매듭짓고 그 결과를 철저히 검토하여 승인 과정을 거친 후 다음 단계를 진행
+ 가장 오래되고 가장 폭넓게 사용된 전통적인 소프트웨어 생명주기 모형
+ 각 단계가 끝난 후 다음 단계를 수행하기 위한 결과물이 명확히 산출 되어야함


### 프로토타입 모형(Prototype Model, 원형 모형)

+ 실제 개발될 소프트웨어에 대한 견본품(Prototype)을 만들어 최종 결과물을 예측하는 모형
+ 견본품은 사용자와 시스템 사이의 인터페이스에 중점을 두어 개발함


### 나선형 모형(Spiral Model, 점진적 모형)

+ 나선을 따라 돌듯 여러번의 소프트웨어 개발 과정을 거쳐 점진적으로 완벽한 최종 소프트웨어를 개발하는 모형

+ 누락되거나 추가된 요구사항을 첨가할 수 있음 
+ 유지 보수 과정이 필요없음
+ 보햄(Boehm)이 제안, 폭포수 모형과 프로토타입의 장점에 위험분석 기능을 추가
+ 계획수립 > 위험분석 > 개발 및 검증 > 고객 평가 > 계획수립 > 위험분석 > .. 과 같은 사이클이 돌아감

### 애자일 모형(Agile Model)

+ 애자일은 '민첩한', '기민한' 이라는 의미로 고객의 요구사항변화에 유연하게 대응할 수 있도록 일정한 주기를 반복하면서 개발하는 모형
+ 어느 특정 개발 방법론이 아니라 좋은 것을 빠르고 낭비없게 만들기 위해 고객과의 소통에 총점을 맞춘 방법론을 통칭
+ 폭포수 모형과 대조적임
+ 애자일 모형을 기반으로 하는 소프트웨어 개발 모형에는 스크럼(Scrum), XP(eXtreme Programming), 칸반(Kanban), Lean, 기능 중심 개발(FDD; Feature Driven Development)

+ 애자일 개발 4가지 핵심가치
  - 프로세스와 도구보다는 **개인과 상호작용에 더 가치를 둠**
  - 방대한 문서 보다는 **실행되는 SW에 더 가치를 둠**
  - 계약 협상보다는 **고객과 협엡에 더 가치를 둠**
  - 계획을 따르기 보다는 **변화에 반응하는 것에 더 가치를 둠**


## 소프트웨어 공학

+ 소프트웨어 공학(SE; Software Engineering)은 소프트웨어의 위기를 극복하기 위한 방안으로 연구된 학문
+ 여러가지 방법론과 도구, 관리 기법들을 통하여 소프트웨어의 품질과 생산성 향상을 목적으로 사용한다.

+ 소프트웨어 공학의 기본 원칙
  - 현대적인 프로그래밍 기술을 계속적으로 적용해야 함
  - 개발된 소프트웨어의 품질이 유지되도록 지속적으로 검증해야함
  - 소프트웨어 개발 관련 사항 및 결과에 대한 명확한 기록을 유지해야함

# 소프트웨어 개발 방법론

+ 소프트웨어 개발 방법론은 **소프트웨어 개발, 유지보수 등에 필요한** 여러가지 일들의 수행방법과 이러한 일들을 효율적으로 수행하려는 과정에서 필요한 **각종 기법 및 도구를 체계적으로 정리하여 표준화한 것**

+ 소프트웨어 개발 방법론의 목적은 소프트웨어의 생산성과 품질 향상이다.
+ 주요 소프트웨어 개발 방법론
  - 구조적 방법론
  - 정보공학 방법론
  - 객체지향 방법론
  - 컴포넌트 기반(CBD) 방법론
  - 제품 계열 방법론
  - 애자일 방법론


## 구조적 방법론

+ 구조적 방법론은 정형화된 분석 절차에 따라 **사용자 요구사항을 파악하여 문서화하는 처리(Process) 중심의 방법론**
+ 1960년대까지 가장 많이 적용되었던 소프트웨어 개발 방법론
+ 쉬운 이해 및 검증이 가능한 프로그램 코드를 생성하는 것이 목적
+ 복잡한 문제를 다루기 위해 분할과 정복(Devide and Conquer) 원리를 적용
+ 구조적 방법론의 개발 절차
  - 타당성 검토 > 계획 > 요구사항 > 설계 > 구현 > 시험 > 운용/유지보수


## 정보공학 방법론 

+ 정보공학 방법론은 정보 시스템의 개발을 위해 **계획, 분석, 설계 구축에 정형화된 기법들을** 상호 연관성 있게 **통합 및 적용하는 자료(Data) 중심의 방법론**
+ 정보 시스템 개발 주기를 이용하여 대규모 정보 시스템을 구축하는데 적합함
+ 정보공학 방법론의 개발 절차
  - 정보 전략 계획 수립 > 업무 영역 분석 > 업무 시스템 설계 > 업무 시스템 구축


## 객체지향 방법론

+ 현실 세계의 개체(Entity)를 기계의 부품처럼 하나의 객체(Object)로 만들어 소프트웨어를 개발할 떄 기계의 부품을 조립하듯이 **객체들을 조립해서** 필요한 **소프트웨어를 구현하는 방법론**
+ 객체지향 방법론은 구조적 기법의 문제점으로 인한 소프트웨어 위기의 해결책으로 채택
+ 객체지향 방법론의 구성요소 : 객체, 클래스, 메시지 등
+ 객체지향 방법론의 기본 원칙 : 캡슐화, 정보 은닉 , 추상화, 상속성, 다형성
+ 객체지향 방법론의 개발 절차
  - 요구 분석 > 설계 > 구현 > 테스트 및 검증 > 인도단계

## 컴포넌트 기반(CBD: Component Based Design) 방법론

+ 컴포넌트 기반 방법론은 기존의 시스템이나 소프트웨어를 구성하는 **컴포넌트를 조합하여** 하나의 **새로운 애플리케이션을 만드는 방법론**
+ 컴포넌트의 재사용(Reusability)이 가능하여 시간과 노력을 절감할 수 잇음
+ 새로운 기능을 추가하는 것이 간단하여 확장성이 보장됨
+ 유지 보수 비용을 최소화하고 생산성 및 품질을 향상 시킬 수 있음
+ 컴포넌트 기반 방법론의 개발 절차
  -  개발 준비 > 분석 > 설계 > 구현 > 테스트 > 전개 > 인도 단계


## 제품 계열 방법론

+ 제품 계열 방법론은 특정 **제품에 적용하고 싶은 공통된 기능을 정의하여 개발하는 방법론**
+ 임베디드 소프트웨어를 만드는데 적합
+ 영역공학과 응용공학으로 구분
  - 영역공학 : 영역 분석, 영역 설계, 핵심 자산을 구현하는 영역
  - 응용공학 : 제품 요구 분석, 제품 설계, 제품을 구현하는 영역
+ 영역공학과 응용공학의 연계를 위해 제품의 요구사항, 아키텍쳐, 조립 생산이 필요함

# 스크럼(Scrum) 기법 - D

+ 스크럼은 **팀이 중심이 되어 개발의 효율성을 높이는 기법**
+ 팀원 스스로가 스크럼 팀을 구성하고 개발 작업에 관한 모든 것을 스스로 해결할 수 있어야 함

+ 스크럼 팀의 구성원 및 역할
  - 제품 책임자(PO : Product Owner)
    * 요구사항이 담긴 백로그(Backlog)를 작성하는 주체
    * 이해관계자들 중 개발될 제품에 대한 이해도가 높고, 요구사항을 책임지고 의사를 결정할 사람으로 선정
  - 스크럼 마스터(SM : Scrum Master)
    * 스크럼 팀이 스크럼을 잘 수행할 수 있도록 가이드 역할을 수행함
  - 개발팀 (DT : Development Team)
    * 제품 책임자와 스크럼 마스터를 제외한 모든 팀원으로 제품 개발을 수행함

+ 스크럼 개발 프로세스
  - 스프린트 계획 회의
    * 제품 백로그 중 이번 스프린트에서 수행할 작업을 대상으로 단기 일정을 수립하는 회의
  - 스프린트
    * 실제 개발 작업을 진행하는 과정, 보통 2 ~ 4주 정도의 기간 내에서 진행
  - 일일 스크럼 회의
    * 모든 팀원이 약 15분 동안 진행상황을 점검, 남은 작업 시간은 소멸 차트(Burn-down Chart)에 표시
  - 스프린트 검토 회의 
    * 부분 또는 전체 완성 제품이 요구사항에 잘 부합하는지 테스팅 하는 회의
  - 스프린트 회고
    * 정해놓은 규칙 준수 여부 , 개선할점 확인


# XP(eXtreme Programming) 기법 

+ XP는 수시로 발생하는 고객의 **요구사항에 유연하게 대응하기 위해 고객의 참여와 개발과정의 반복을 극대화하여** 개발 **생산성을 향상시키는 방법**
+ 짧고 반복적인 개발 주기, 단순한 설계, 고객의 적극적인 참여를 통해 소프트웨어를 빠르게 개발하는 것을 목적으로 함
+ 릴리즈의 기간을 짧게 반복하며, 고객의 요구사항 반영에 대한 가시성을 높임
+ XP의 5가지 핵심 가치
  - 의사소통(Communication)
  - 단순성(Simplicity)
  - 용기(Courage)
  - 존중(Respect)
  - 피드백(Feedback)

+ XP 개발 프로세스
  - 릴리즈 계획 수립(Release Planning) 
    * 부분 혹은 전체 개발 완료 시점에 대한 일정을 수립하는것
    * 몇 개의 스토리가 적용되어 부분적으로 기능이 완료된 제품을 제공하는 것을 릴리즈 라고함
  - 이터레이션(lteration, 주기)
    * 실제 개발 작업을 진행하는 과정으로, 보통 1~3주 정도의 기간으로 진행됨
  - 승인검사(Acceptance Test)
    * 하나의 이터레이션 안에서 부분 완료 제품이 구현되면 수행하는 테스트
  - 소규모 릴리즈(Small Release)
    * 요구사항에 유연하게 대응할 수 있도록 릴리즈의 규모를 축소한것

+ XP의 주요 실천방법(Practice)

  - **짝 프로그래밍(Pair Programming)**
    * 다른 사람과 함께 프로그래밍을 수행함으로써 개발에 대한 책임을 공동으로 나눠 갖는 환경을 조성 
  - **공동 코드 소유(Collective Ownership)**
    * 개발 코드에 대한 권한과 책임을 공동으로 소유함
  - **테스트 주도 개발(Test-Driven Development)**
    * 개발자가 실제 코드를 작성하기 전에 테스트 케이스를 먼저 작성하므로 자신이 무엇을 해야할지 파악
    * 테스트가 지속적으로 진행될 수 있도록 자동화된 테스팅 도구(구조, 프레임워크)를 사용함
  - **전체 팀(Whole Team)**
    * 개발에 참여하는 모든 구성원(고객 포함)들은 각자 자신의 역할이 있고 그 역할에 대한 책임을 가져야함
  - **계속적인 통합(Continuous Integration)**
    * 모듈 단위로 나눠서 개발된 코드들은 하나의 작업이 마무리 될 때마다 지속적으로 통합됨
  - **리팩토링(Refactoring)**
    * 프로그램의 단순화, 유연성 강화등을 위해 기능의 변경없이 시스템을 재구성함
  - **소규모 릴리즈(Small Releases)**
    * 릴리즈 기간을 짧게 반복함으로써 고객의 요구 변화에 신속히 대응할 수있음