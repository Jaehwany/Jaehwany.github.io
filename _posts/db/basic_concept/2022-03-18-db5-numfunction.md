---
layout: single
title:  "MySQL 5 - 숫자 함수"
categories: MySQL
tags: [database,MySQL]
toc: true
toc_sticky: true
author_profile: false
sidebar:
    nav: "docs"
search: false
order : 5
---

<br>

![image-20220322031630012](../../../images/db/image-20220322031630012.png)

👉 Source Link : [내장 함수](https://github.com/Jaehwany/Database/blob/036dc94a641e1156a4abbb18f3fbbba3a5cc7168/1.%20basic/4.%20function.sql)

<br>

### ✅ 내장 함수

- 숫자함수 : mod , round, trunc, ceil, truncate, etc

- 문자함수 : lower, upper, length, substr, ltrim, rtrim, trim, etc

<br>

###### ✔ 숫자 함수

----------------

##### **▪** <span style="color:darkblue">abs </span>절대값 

``` sql
select abs(-5), abs(0), abs(+5)
from dual;
```

<bR>

-----------------

##### **▪** <span style="color:darkblue">ceil</span> 올림

``` sql
select ceil(12.2), ceiling(12.2), ceil(-12.2), ceiling(-12.2)
from dual;
```

<br>

------------

##### **▪** <span style="color:darkblue"> floor</span> 내림

``` sql
select floor(12.6), floor(-12.2)
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> round</span> 반올림

``` sql
select round(1526.159), round(1526.159, 0), round(1526.159, 1), 
round(1526.159, 2), round(1526.159, -1), round(1526.159, -3)
from dual;
```

![image-20220317015024910](../../images/db/2022-03-18-db-function/image-20220317015024910.png)

<br>

-----------------

##### **▪** <span style="color:darkblue"> truncate</span> 버림

``` sql
select truncate(1526.159, 0), truncate(1526.159, 1), truncate(1526.159, 2), 
truncate(1526.159, -1), truncate(1526.159, -3)
from dual;
```

![image-20220317015156254](../../images/db/2022-03-18-db-function/image-20220317015156254.png)

<br>

-----------------

##### **▪** <span style="color:darkblue"> format</span> 세자리마다 콤마찍기

``` sql
-- format(컬럼명,소수점이하 자리수) : 소수이하는 절삭,세자리마다 콤마(,)
select format(avg(salary),0) as "사원급여평균"
from employees;
```

![image-20220317015156254](../../images/db/2022-03-18-db-function/image-20220317015156254.png)

<br>

-----------------

##### **▪** <span style="color:darkblue"> mod, %</span> 나머지 구하기

``` sql
select mod(8, 3), 8 % 3
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> pow</span> 거듭제곱 구하기

``` sql
select pow(2,3), power(2,3)
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue"> greatest / least </span>최댓값 / 최솟값

``` sql
select greatest(4, 3, 7, 5, 9), least(4, 3, 7, 5, 9)
from dual;
```

<br>

-----------------

##### **▪** <span style="color:darkblue">count, sum, avg, max, min</span>

``` sql
-- 사원의 총수, 급여의 합, 급여의 평균, 최고급여, 최저급여
select count(employee_id), sum(salary), avg(salary), max(salary), min(salary)
from employees;
```

