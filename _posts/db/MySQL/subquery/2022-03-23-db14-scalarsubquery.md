---
layout: single
title:  "MySQL 14 - 스칼라 서브쿼리 & 서브쿼리 활용"
categories: MySQL
tags: [database,MySQL]
toc: true
toc_sticky: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 14
---

<br>

![image-20220322031630012](../../../images/db/image-20220322031630012.png)

<br>

###### ✔ 스칼라 서브 쿼리 

- SELECT 절에 있는 서브 쿼리
- 한개의 행만 반환

``` sql
select e.employee_id, e.first_name, salary, department_id,
	 (select avg(salary) from employees where department_id = 60) as avg60
from employees e
where department_id = 60;
```

``` sql
select
	(select sum(salary) from employees where department_id = 50) sum50,
	(select avg(salary) from employees where department_id = 60) avg60,
	(select max(salary) from employees where department_id = 90) max90,
	(select min(salary) from employees where department_id = 90) min90
from dual;
```

------------------------------

<br>

###### ✔ 서브 쿼리 - CREATE, INSERT, UPDATE, DELETE

- 서브 쿼리를 이용한 CREATE, INSERT, UPDATE, DELETE

- <span style ="background-color:#fff5b1">CREATE</span>

``` sql
-- employees table을 emp_copy라는 이름으로 복사(컬럼 이름 동일).
create table emp_copy
select * from employees;

-- employees table의 구조만 emp_blank라는 이름으로 생성(컬럼 이름 동일).
create table emp_blank
select * from employees
where 1 = 0; -- 만족하는 것이 없기 때문에 구조만 가져온다

-- 50번 부서의 사번(eid), 이름(name), 급여(sal), 부서번호(did)만 emp50이라는 이름으로 생성.
create table emp50
select employee_id eid, first_name name, salary sal, department_id did
from employees
where department_id = 50;
```

-------------

- <span style ="background-color:#fff5b1">INSERT</span>

```sql
-- employees table에서 부서번호가 80인 사원의 모든 정보를 emp_blank에 insert
insert into emp_blank
select * from employees
where department_id = 80;
```

----------------

- <span style ="background-color:#fff5b1">UPDATE</span>

```sql
-- employees table의 모든 사원의 평균 급여보다 적게 받는 emp50 table의 사원의 급여를 500 인상.
update emp50
set sal = sal + 500
where sal < (select avg(salary) from employees);
```

------------

- <span style ="background-color:#fff5b1">DELETE</span>

```sql
-- employees table의 모든 사원의 평균 급여보다 적게 받는 emp50 table의 사원은 퇴사.
delete from emp50
where sal < (select avg(salary) from employees);
```

<br>
