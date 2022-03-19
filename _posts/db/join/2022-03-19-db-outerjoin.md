---
layout: single
title:  "8. DB - OuterJOIN"
categories: MySQL
tags: [database,MySQL]
toc: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 8
---

<br>

Source Link : [Join Example 1](https://github.com/Jaehwany/Database/blob/036dc94a641e1156a4abbb18f3fbbba3a5cc7168/2.%20Join/1.%20Join_example.sql)

<br>

### ✔ Outer JOIN ?

------------------------------------------------------------------

- LEFT outer join, RIGHT outer join, FULL outer join (MySQL X)으로 구분

- 어느 한쪽 테이블에는 해당하는 데이터가 존재하는데 다른 쪽 테이블에는 데이터가 존재하지 않을 경우, 그 데이터가 검색되지 않는 문제점을 해결하기 위해 사용.

- union(합집합)을 이용하면 FULL outer join 효과를 볼 수 있다.

- union all : 합집합 + 교집합 

  

  ![image-20220319213035712](../../images/db/2022-03-19-db-outerjoin/image-20220319213035712.png)

<br>

### ✔ Outer Join Example

------------------------------------------------------------------

``` sql
-- LEFT (107건) 조회
select last_name,department_id, department_name 
from employees
left join departments using (department_id);
```

<br>

``` sql
-- RIGHT (122건) 조회
select last_name,department_id, department_name 
from employees
right join departments using (department_id);
```

<br>

``` sql
-- FULL (mysql에서는 제공 x, but Union으로 구현가능)
select employee_id, first_name
from employees
union 
select employee_id, first_name
from employees_role
order by 1;
```

<br>

### ✔ Set Operator

------------------------------------------------------------------

- 두개 이상의 쿼리결과를 하나로 결합시키는 연산자
- UNION : 양쪽 쿼리를 모두 포함 (중복 결과는 1번만 포함) - 합집합
- UNION  ALL : 양쪽 쿼리를 모두 포함 (중복 결과도 모두 포함)
- INTERSECT  : 양쪽 쿼리 결과에 모두 포함되는 행만 표현  - 교집합 (MySQL에서는 지원 안함)
- MINUS : 쿼리1 결과에 포함되고 쿼리2 결과에는 포함되지 않는 행만 표현 - 차집합 (MySQL에서는 지원 안함)

<br>

