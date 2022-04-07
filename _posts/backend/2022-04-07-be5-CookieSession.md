---
layout: single
title:  "Cookie & Session"
categories: Web
tags: [Web]
toc: true
toc_sticky: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 5
---

<br>

###### 🚥 Cookie & Session

<br>

- http protocol의 특징
  - client가 server에 요청
  - server는 요청에 대한 처리를 한 후 client에 응답
  - 응답 후 연결 해제 statless

- HTTP protocol의 약점을 보완하기 위해 사용

-------------

- **Cookie**

  서버에서 <span style="color:red">사용자의 컴퓨터<에 저장하는 정보파일

  사용자가 별도의 요청을 하지 않아도 브라우저는 request시 request Header를 넣어 자동으로 서버에 전송

  key와 value로 구성되고 String 형태로 이루어져 있음

  Browswer마다 저장되는 쿠키는 다르다 (서버에서는 Browser가 다르면 다른 사용자로 인식)

-----------

- **Cookie의 사용 목적**

  세션관리 : 사용자 아이디, 접속시간, 장바구니 등의 서버가 알아야 할 정보 저장

  개인화 : 사용자마다 다르게 그 사람에 적절한 페이지를 보여줄 수 있다
  
  트래킹 : 사용자의 행동과 패턴을 분석하고 기록

------------

<br>

- **Cookie의 사용 예**

  ID 저장 (자동 로그인)

  일주일간 다시 보지 않기

  최근 검색한 상품들을 광고에 추천

  쇼핑몰 장바구니 기능

------------

<br>

- **Cookie의 구성 요소**

  이름 : 여러 개의 쿠키가 client의 컴퓨터에 저장되므로 각 쿠키를 구별하는 데 사용되는 이름

  값 : 쿠키의 이름과 매핑되는 값

  유효기간 : 쿠키의 유효기간

  도메인 : 쿠키를 전송할 도메인

  경로 : 쿠키를 전송할 요청 경로

------------

<br>



- **Cookie의 동작 순서**

  Client가 페이지를 요청

  WAS는 Cookie 생성

  HTTP Header에 Cookie를 넣어 응답

  Browser는 넘겨받은 Cookie를 PC에 저장하고, 다시 WAS가 요청할 때 요청과 함꼐 Cookie 전송

  Browser가 종료되어도 Cookie의 만료 기간이 남아 있다면 Client는 계속 보관

  동일 사이트 재방문시 Client의 PC에 해당 Cookie가 있는 경우, 요청 페이지와 함께 Cookie를 전송 

------------

<br>

- **Cookie의 특징**

  이름, 값,만료일, 경로 정보로 구성되어 있다

  클라이언트에 총 300개의 쿠키를 저장할 수 있다

  하나의 도메인 당 20개의 쿠키를 가질 수 있다

  하나의 쿠키는 4KB까지 저장 가능하다

------------

<br>

- **Cookie의 설정**

  name이 userid인 C

------------

<br>
