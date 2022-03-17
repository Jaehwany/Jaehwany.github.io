---
layout: single
title:  "MySQL - 데이터베이스 생성"
categories: MySQL
tags: [database,MySQL]
toc: true
author_profile: false
sidebar:
    nav: "docs"
search: false
---

<br>

### ✔ 데이터베이스 생성 (CREATE)



``` sql
-- 다국어 처리(utf8mb3) : 3byte
create database dbtest
default character set utf8mb3 collate utf8mb3_general_ci;
```

``` sql
-- 이모지 문자 처리(utf8mb4) : 4byte
create database dbtest
default character set utf8mb4 collate utf8mb4_general_ci;

use dbtest;

create table test(
	val varchar(10)
);

insert into test (val)
values ('a');

insert into test (val)
values ('😊');

select * from test;
```

Character set : 각 문자가 컴퓨터에 저장될 때 어떠한 '코드'로 저장될지에 대한 규칙의 집합

Collation : 특정 문자 셋에 의해 문자들을 서로 '비교' 할 때 사용하는 규칙들의 집합

<br>

### ✔ 데이터베이스 변경 (ALTER)

``` sql
alter database dbtest
default character set utf8mb4 collate utf8mb4_general_ci;
```

<br>

### ✔ 데이터베이스 삭제 (DROP)

``` sql
drop database dbtest;
```

<br>

### ✔ 데이터베이스 사용 (USE)

``` sql
use datadb;
```
