# SQL



## SQL 실행 순서



## SELECT 실행 순서



### 문법 순서

* SELECT - 1

* FROM - 2

* WHERE - 3

* GROUP BY - 4

* HAVING - 5

* ORDER BY - 6

  

------



### 실행 순서

* FROM - 1   (해당 데이터가 있는 곳을 찾아가서 (FROM))

* WHERE - 2    (조건에 맞는 데이터만 가져와서 (WHERE))

* GROUP BY - 3   (원하는 데이터로 집계 (GROUP BY))

* HAVING - 4   (집계한 데이터에서 조건에 맞는 것만 (HAVING))

* SELECT - 5    (뽑아내서 (SELECT))

* ORDER BY - 6    (정렬 (ORDER BY))

  

------



### 실행순서는 문법, 권한 검사 순서이면서 Alias 등록 순서

* 별칭(Alias)
* FROM 절에서 테이블에 Alias를 사용했다면 (FROM Table1 AS T1)
* SELECT, ORDER BY 절에서 사용할 수 있고 (SELECT T1.Col1, ORDER BY T1.Col1)
* SELECT 절에서 컬럼에 Alias를 사용했다면 (SELECT T1.Col1 AS a)
* ORDER BY 절에서 사용할 수 있다. (ORDER BY AS a)
* ORDER BY절에 T1.a가 안되는 것으로 보아 a는 T1.col1을 대신!