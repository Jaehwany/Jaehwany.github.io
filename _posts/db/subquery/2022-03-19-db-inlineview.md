---
layout: single
title:  "MySQL - 인라인뷰(Inline View)"
categories: MySQL
tags: [database,MySQL]
toc: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 12
---

<br>

Source Link : [InlineView Subquery](https://github.com/Jaehwany/Database/blob/dfc4d97cbc1316d203692f947d239f3f41beae7a/Subquery/Inlineview_Subquery%202.sql)

### ✔ 인라인 뷰

------------------------------------------------------------------

- FROM 절에 사용되는 서브 쿼리를 인라인 뷰(Inline View)라 한다
- 서브 쿼리가 FROM 절에 사용되면 뷰(View) 처럼 결과가 동적으로 생성된 테이블로 사용 가능.
- 임시적인 뷰이기 때문에 데이터베이스에는 저장되지 않는다.
- 동적으로 생성된 테이블이기 때문에 column을 자유롭게 참조 가능

``` sql
select e.employee_id, e.first_name, e.salary, e.department_id
from (
	  select distinct department_id
	  from employees
	  where salary < (select avg(salary) from employees)
	 ) d join employees e
on d.department_id = e.department_id;
```

<br>

### ✔ 인라인 뷰 - TopN 질의

-----------------------------------------------

```sql
set @pageno = 3;

select b.rn, b.employee_id, b.first_name, b.salary
from (
	  select @rownum := @rownum + 1 as rn, a.*
	  from (
		    select employee_id, first_name, salary
		    from employees
		    order by salary desc
		   ) a, (select @rownum := 0) tmp
	 ) b
where b.rn > (@pageno * 5 - 5) and b.rn <= (@pageno * 5);
```

<br>

### ✔ 인라인 뷰 - limit 활용 

------------------------------------------------------------------

- MySQL 기능

``` sql
select a.*
from (
	  select @rownum := @rownum + 1 as rn, employee_id, first_name, salary
	  from employees e, (select @rownum := 0) tmp
	  order by salary desc 
	 ) a limit 10, 5;
```

<br>

