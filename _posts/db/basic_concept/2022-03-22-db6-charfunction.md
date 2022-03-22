---
layout: single
title:  "MySQL 6 - 문자 함수"
categories: MySQL
tags: [database,MySQL]
toc: true
toc_sticky: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 6
---

<br>

![image-20220322031630012](../../../images/db/image-20220322031630012.png)

👉 Source Link : [내장 함수](https://github.com/Jaehwany/Database/blob/036dc94a641e1156a4abbb18f3fbbba3a5cc7168/1.%20basic/4.%20function.sql)

<br>

### ✅ 내장 함수

- 숫자함수 : mod , round, trunc, ceil, truncate, etc

- 문자함수 : lower, upper, length, substr, ltrim, rtrim, trim, etc

<br>

###### ✔ 문자 함수

----------------

##### **▪** <span style="color:darkblue"> insert</span> 삽입

```sql
-- 결과 : hello ssafy !!!
select insert('helloabc!!!', 6, 3, ' ssafy ')
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> replace </span>교환

``` sql
-- 결과 : hello ssafy !!!
select replace('helloabc!!!', 'abc', ' ssafy ')
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> instr</span> 문자열 위치

``` sql
-- 결과 : 7
select instr('hello ssafy !!!', 'ssafy')
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue">lpad</span> 문자 출력

지정한 길이 만큼 왼쪽부터 특정문자로 채움

```sql
-- name을 맨 앞과 맨 뒤에 2글자를 제외하고 나머지는 *로 처리해서 출력
select name, concat(left(name,2), lpad('*',char_length(name)-4,'*'), right(name,2)) 
from country;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> mid, substring</span> 

특정 위치부터 갯수만큼 리턴

``` sql
-- 결과 : ssafy / ssafy
select mid('hello ssafy !!!', 7, 5), substring('hello ssafy !!!', 7, 5)
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue">left, right</span> 

왼쪽, 오른쪽에서 갯수만큼 추출 

``` sql
-- 결과 : hello  /   fy !!!
select left('hello ssafy !!!', 5), right('hello ssafy !!!', 6)
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> substr</span> 

``` sql
-- country에서 code가 모음으로 시작하는 나라의 정보 출력
select code, name 
from country
where substr(code, 1, 1) in ('a', 'e','i','o','u') 
order by name limit 2, 3;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> reverse</span> 반대로 나열

```sql
-- 결과 : hello ssafy !!!
select reverse('!!! yfass olleh')
from dual;
```

<br>

-----------------

##### **▪**  <span style="color:darkblue">ASCII 코드</span>

``` sql
select ASCII('0'), ASCII('A'), ASCII('a')
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue">Upper</span>

문자열을 대문자로

```sql
-- 문자열을 대문자로
select * from employees
where upper(last_name)='KING';  
```

<br>

-----------------

##### **▪** <span style="color:darkblue">Lower</span>

문자열을 소문자로

```sql
-- 문자열을 소문자로
select * from employees
where lower(last_name)='king';  
```

<br>

-----------------

##### **▪** <span style="color:darkblue">if, ifnull, nullif </span>

``` sql
-- if(논리식, v1, v2) true: v1, false : v2
-- ifnull(v, v2) v==NULL: v2,  v!=NULL: v
-- nullif(v1, v2) v1==v2 -> true: NULL / false: v1
select if(3 > 2, '크다', '작다'), if(3 > 5, '크다', '작다'),
		ifnull(null, 'b'), ifnull('a', 'b')
		nullif(3, 3), nullif(3, 5),
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue">시간 함수</span>

``` sql
-- 현재 시간
select now(), sysdate(), current_timestamp()
from dual;
```

![image-20220317020204818](../../images/db/2022-03-18-db-function/image-20220317020204818.png)

-----------------

``` sql
-- 현재 날짜(년월일) / 현재 날짜(년월일) / 현재 시간(시분초) /현재 시간(시분초)
select curdate(), current_date(), curtime(), current_time()
from dual;
```

![image-20220317020303928](../../images/db/2022-03-18-db-function/image-20220317020303928.png)

-----------------

``` sql
select now() 현재시간, 
date_add(now(), interval 5 second) 5초후,
date_add(now(), interval 5 hour) 5시간후, 
date_add(now(), interval 5 day) 5일후
from dual;
```

![image-20220317020404087](../../images/db/2022-03-18-db-function/image-20220317020404087.png)

-----------------

``` sql
-- dayofweek() : 일월화수목금토(1234567) 중
-- weekday(): 월화수목금토일(0123456) 중
-- dayofyear() :365 중 오늘이 몇번째날?
-- dayofyear : 52주 중 몇번째 주? (첫번째 주:0으로 시작)
select year(now()), month(now()), monthname(now()), 
dayname(now()), dayofmonth(now()), dayofweek(now()), 
weekday(now()), dayofyear(now()), week(now())
from dual;
```

![image-20220317020532232](../../images/db/2022-03-18-db-function/image-20220317020532232.png)

-----------------

``` sql
select now(), 
date_format(now(), '%Y %M %e %p %l %i %S'),
date_format(now(), '%y-%m-%d %H:%i:%s'),
date_format(now(), '%y.%m.%d %W'), 
date_format(now(), '%H시%i분%s초')
from dual;
```

![image-20220318001907647](../../images/db/2022-03-18-db-function/image-20220318001907647.png)
