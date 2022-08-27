---
layout: single
title:  "MySQL 15 - Transaction 처리"
categories: MySQL
tags: [database,MySQL]
toc: true
toc_sticky: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 15
---

<br>

![image-20220322031630012](../../../images/db/image-20220322031630012.png)


<br>

###### ✔ 트랜잭션

- 트랜잭션이란, 데이터베이스의 상태를 변경시키기 위해 수행하는 작업 단위
- SELECT, UPDATE, INSERT, DELETE 와 같은 행동을 뜻함

-----------------------

<br>

###### ✔ 트랜잭션 특징

- <span style ="background-color:#f1f8ff">원자성</span> : 트랜잭션이 **DB에 모두 반영되거나, 전혀 반영되지 않음**를 뜻한다.
- <span style ="background-color:#f1f8ff">일관성</span> : 트랜잭션 **처리의 결과가 항상 일관되어야 한다**
- <span style ="background-color:#f1f8ff">독립성 </span>: **하나의 트랜잭션은 다른 트랜잭션에 끼어들 수 없는 독립성**을 가진다
- <span style ="background-color:#f1f8ff">지속성 </span>: **트랜잭션이 성공적으로 완료되면 영구적으로 결과에 반영**되어야 한다

----------------

<br>

###### ✔ 트랜잭션 처리

- <span style ="background-color:#fff5b1">commit</span> : 일의 시작과 끝이 완벽하게 마무리가 되면 테이블에 적용 (일관성 있는 상태)
- <span style ="background-color:#fff5b1">rollback</span> : 처리도중 인터럽트(interrupt:장애)가 발생하면 되돌아옴 (원자성 깨진 상태)

--------------

- 트랜젝션 처리를 안했을 경우 오류 상황

``` sql
-- 콘솔창에서
update book set subject='JSP 20일 완성' where num=1;

-- 이클립스창 또는  MySQL Workbench에서
update book set subject='JSP 마스터북' where num=1;
```



<img src="../../../images/db/2022-03-20-db-transaction/image-20220320031820402.png" alt="image-20220320031820402" style="zoom: 80%;" />

-----------

- 트랜젝션 처리를 했을 경우

``` sql
set autocommit=1;
-- 콘솔창에서
update book set subject='JSP 20일 완성' where num=1;

-- 이클립스창 또는  MySQL Workbench에서
update book set subject='JSP 마스터북' where num=1;
```

![image-20220320031940242](../../../images/db/2022-03-20-db-transaction/image-20220320031940242.png)
