---
layout: single
title:  "10. DB - Subquery"
categories: MySQL
tags: [database,MySQL]
toc: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 10
---

<br>

Source Link : [Subquery](https://github.com/Jaehwany/Database/blob/036dc94a641e1156a4abbb18f3fbbba3a5cc7168/3.%20Subquery)

<br>

### ✔ 서브 쿼리 (Subquery) 

------------------------------------------------------------------

- 다른 쿼리 내부에 포함되어 있는 SELECT 문을 의미
- 서브 쿼리를 포함하고 있는 쿼리를 외부 쿼리 또는 메인 쿼리라고 부른다
- 서브 쿼리는 내부 쿼리라고도 부른다.

<br>

### ✔ 서브 쿼리의 종류

------------------------------------------------------------------

- <span style ="background-color:#f1f8ff">중첩 서브 쿼리 (Nested Subquery)</span> : Where 문에 작성하는 서브 쿼리
  - 단일 행, 복수 행, 다중 열
- <span style ="background-color:#f1f8ff">인라인 뷰 (Inline View)</span>: From 문에 작성하는 서브 쿼리
- <span style ="background-color:#f1f8ff">스칼라 서브 쿼리 (Scalar Subquery)</span> : SELECT 문에 작성하는 서브 쿼리

<br>

### ✔ 서브 쿼리를 사용하는 이유?

------------------------------------------------------------------

- JOIN을 사용하면 쿼리가 복잡해 지거나 카테시안 곱으로 속도 저하가 발생할 수 있기 때문

  <span style="background-color:#ffdce0">(case by case) </span>

<br>

### ✔ 서브 쿼리 주의 사항

------------------------------------------------------------------

- 서브 쿼리는 반드시 ( )로 감싸야 한다.

- 서브 쿼리는 단일 행 또는 다중 행 비교 연산자 [ > , < , >=, <= , <> ] 와 함께 사용된다.

  <br>

### ✔ 서브 쿼리가 사용이 가능한곳

------------------------------------------------------------------

- SELECT

- FROM

- WHERE

- HAVING

- ORDER BY

- INSERT문 VALUES

- UPDATE 문 SET

