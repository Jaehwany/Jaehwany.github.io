---
layout: single
title:  "MySQL - 중첩 서브 쿼리 (Nested Subquery)"
categories: MySQL
tags: [database,MySQL]
toc: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 11
---

<br>

Source Link : [Nested Subquery](https://github.com/Jaehwany/Database/blob/971445372ea1b0907426997825eb4779dce7b224/Subquery/subquery_where)

### ✔ 중첩 서브 쿼리 - 단일 행

------------------------------------------------------------------

- 단일 행 서브쿼리 (단일 행 반환) :  > , < , >=, <= , <>            

``` sql
select department_id, department_name
from departments
where location_id = (
			select location_id
			from locations
			where binary upper(city) = upper('seattle')
			);
```

<br>

### ✔ 중첩 서브 쿼리 - 다중 행

------------------------------------------------------------------

- 다중 행 서브쿼리 (여러 행 반환) : in, any, all

  - ' < any' : 비교 대상 중 최대값보다 작음 (ex. 과장직급의 최대급여보다 적게 받는 사원조회)
  - ' > any' : 비교 대상 중 최소값보다 큼 (ex. 과장직급의 최소급여보다 많이 받는 사원조회)             
  - ' = any' : in 연산자와 동일 (ex. 과장 직급과 동일한 급여를 받는 사원조회)
  - '  <  all' : 비교 대상 중 최소값보다 작음 (ex. 과장직급의 최소 급여보다 적게 받는 사원조회)
  - ' >  all' : 비교대상중 최대값보다 큼   (ex. 과장직급의 최대 급여보다 많이 받는 사원조회)

```sql
-- 다중행 any
select employee_id, first_name,salary,department_id
from employees
where salary> any (
		select salary
		from employees
		where department_id=30
		);
```

``` sql
-- 다중행 all
select employee_id, first_name,salary,department_id
from employees
where salary> all (
		select salary
		from employees
		where department_id=30
		);
```



<br>

### ✔ 중첩 서브 쿼리 - 다중 열

------------------------------------------------------------------

- 다중 열 서브쿼리 (다중 열반환)

``` sql
-- 다중열
select employee_id,first_name
from employees
where (salary,department_id) in (
				select salary, department_id
				from employees
				where commission_pct is not null 
				and manager_id=148
				);
```



<br>

