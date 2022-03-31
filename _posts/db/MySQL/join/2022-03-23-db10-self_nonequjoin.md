---
layout: single
title:  "MySQL 10 - Self Join, None-equi Join, Cross JOIN"
categories: MySQL
tags: [database,MySQL]
toc: true
toc_sticky: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 10
---

<br>

![image-20220322031630012](../../../images/db/image-20220322031630012.png)

👉 Source Link  : [Join Example 1](https://github.com/Jaehwany/Database/blob/036dc94a641e1156a4abbb18f3fbbba3a5cc7168/2.%20Join/1.%20Join_example.sql)

<br>

###### ✔ Self JOIN

------------------------------------------------------------------

- 같은 테이블 끼리 JOIN

``` sql
select e.employee_id as "사원번호", e.last_name as "사원이름", m.last_name as "관리자"
from employees e
left join employees m on(e.manager_id = m.employee_id);
```

<br>

###### ✔ None-Equi JOIN

------------------------------------------------------------------

-  Column 값이 같은 경우가 아닌 범위에 속하는지 여부를 확인할때
-  on (Column명 between Column1 and Column2)

``` sql
select last_name as "사원이름",salary as "급여", grade as "등급"
from employees 
left join salgrades on(salary between losal and hisal)
order by 2 desc;
```

<br>

###### ✔ Cross JOIN

------------------------------------------------------------------

- 모든 행에 대해 가능한 모든 조합을 생성하는 조인

``` sql
select count(*) from countries;     -- 25
select count(*) from locations;     -- 23

-- 방법1(MySQL구문)
select * 
from countries,locations;  -- 25 * 23 = 575건
```

