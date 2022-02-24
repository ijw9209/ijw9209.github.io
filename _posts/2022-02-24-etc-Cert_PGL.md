---
title: "테스트 및 배포 01"
excerpt: "테스트 및 배포 01"
toc: true
toc_sticky: true

categories:
  - etc
  - certificate
tags:
  - etc
  - certificate
last_modified_at: 2022-02-24T08:06:00-05:00
--- 


# 데이터 타입 B (2022-02-24)

+ 데이터 타입(Data Type)은 변수(Variable)에 저장될 데이터의 형식을 나타내는 것으로, 변수에 값을 저장하기 전에 문자형, 정수형, 실수형 등 어떤 형식의 값을 저장할지 데이터 타입을 지정하여 변수를 선언해야함

## C의 데이터 타입 크기 및 기억범위

+ 문자(char , 1Byte, -128 ~ 127)
+ 부호 없는 문자형(unsigned char, 1Byte, 0 ~ 255)
+ 정수
  - short , 2Byte, 
  - int, 4Byte, 
  - long, 4Byte
  - long long, 8Byte
+ 부호 없는 정수형
  - unsigned short, 2Byte
  - unsigned int, 4Byte
  - unsigned long, 4Byte
+ 실수
  - float, 4Byte
  - double, 8Byte
  - long double, 8Byte

## JAVA의 데이터 타입 크기 및 기억 범위

+ 문자
  - char, 2Byte
+ 정수
  - byte, 1Byte
  - short, 2Byte
  - int, 4Byte
  - long, 8Byte
+ 실수
  - float, 4Byte
  - double, 8Byte
+ 논리
  - boolean, 1Byte


## Python의 데이터 타입 크기 및 기억 범위

+ 문자
  - str, 무제한, 무제한
+ 정수
  - int, 무제한, 무제한
+ 실수
  - float, 8Byte
  - complex, 16Byte 