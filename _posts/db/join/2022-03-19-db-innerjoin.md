---
layout: single
title:  "MySQL - Inner Join, Natural Join"
categories: MySQL
tags: [database,MySQL]
toc: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 7
---

<br>

Source Link : [Join Example 1](https://github.com/Jaehwany/Database/blob/036dc94a641e1156a4abbb18f3fbbba3a5cc7168/2.%20Join/1.%20Join_example.sql)

<br>

### ✔ Inner JOIN ?

------------------------------------------------------------------

- 가장 일반적인 JOIN의 종류, 교집합

- Equi-Join이라고도 하며, N개의 테이블 조인 시 N-1개의 조인 조건이 필요

- Inner Join이 default라 Inner를 빼고 join만 적어도 됨

  ![image-20220319211240752](../../images/db/2022-03-19-db-innerjoin/image-20220319211240752.png)

<br>

### ✔ Inner Join Example

------------------------------------------------------------------

``` sql
-- 방법1.MySQL구문
select employee_id, e.department_id, department_name
from employees e, departments d
where e.department_id = d.department_id;
```

<br>

``` sql
-- 방법2.Ansi표준구문
select department_id, city
from departments 
join locations using(location_id);
```

<br>

### ✔ Natural JOIN

------------------------------------------------------------------

- 일치하는 Column이 여러 개 있을 때 모두를 and 연산으로 조인

- <span style="background-color:#ffdce0">타입이 같은 Column들을 모두 조인에 사용하기 때문에 원하지 않는 결과가 나올 수 있다.</span>

- <span style="color:red">자연 조인은 테이블간에 동일한 형식을 갖는 공통 컬럼이 반드시 하나만 존재해야 한다.</span>

  

<br>

### ✔ Natural Join Example

------------------------------------------------------------------

``` sql
-- 방법1.Inner join
select last_name,department_id,manager_id
from departments 
inner join employees using(department_id,manager_id);
```

<br>

``` sql
-- 방법2.Natural 조인 이용
select last_name,department_id,manager_id
from departments natural join employees;
```

<br>
