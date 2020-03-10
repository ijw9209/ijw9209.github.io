---
title: "[자료구조] Array List"
excerpt: "Array List - 자료구조"
toc: true
toc_sticky: true

categories:
  - etc
  - data structure
tags:
  - etc
  - data structure
last_modified_at: 2020-03-10T08:06:00-05:00
---

# Array List - 자료구조

Array List는 배열을 이용해서 리스트를 구현한 것 
장점 : 내부적으로 배열을 이용하기 때문에 인덱스를 이용해서 접근하는것이 빠름
단점 : 데이터의 추가와 삭제가 느림
(데이터를 추가와 삭제할때마다 뒤에있는 모든데이터를 움직여야해서 느리다.)

## 1. 데이터의 추가


Array List는 내부적으로 데이터를 배열에 저장 , 배열의 특성상 데이터를 저장하면 
이후의 데이터들이 한칸씩 뒤로 물러남



![arraylist](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2886.png)


**추가할곳의 위치의 뒤쪽의 데이터는 뒤로물러남!**


## 2. 데이터의 삭제

삭제도 추가와 비슷 , 빈자리가 생기면 빈자리를 채우기 위해 순차적으로 한칸씩
땡김!

![arraylist](https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/module/1335/2887.png)


## 3. 데이터 가져오기

인덱스를 이용해서 데이터를 가져오고 싶을때 Array List 는 매우빠름.
메모리상의 주소를 정확하게 참조해서 가져오기때문