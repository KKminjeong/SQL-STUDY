# SQL



### 예제로 알아보기

https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all



#### ORDER BY (정렬하기)

* 데이터 정렬을 하기 위해서는 ORDER BY 구문을 이용

* ORDER BY 명령 자체는 데이터베이스에 저장된 순서를 변경하지는 않음. 저장되어 있는 데이터는 순서대로 쌓여있는 것. 

* SELECT 문을 수행해서 데이터를 보여줄 때만 순서를 변경해서 보여줌

  

```
SELECT *
FROM customers
ORDER BY customerID DESC
```

* DESC : 내림차순 (큰 수 부터 정렬) / ASC : 오름차순 (작은 수 부터 정렬)
* DESC나 ASC를 적지 않으면, default로 ASC 정렬이 됨.
* WHERE 절을 추가하고 싶다면 순서는 **SELECT -> FROM -> WHERE -> ORDER BY 순으로 작성**한다.



#### MySQL 문자열 자르기 함수

* **LEFT** (컬럼명 또는 문자열, 문자열의 길이)

  * SELECT LEFT("20140323", 4)  -> 2014

* **RIGHT **(컬럼명 또는 문자열, 문자열의 길이)

  * SELECT RIGHT("20140323", 4) -> 0323

* **SUBSTRING** (컬럼명 또는 문자열, 시작 위치, 문자열의 길이)  = **SUBSTR()**

  * SUBSTR("20140323",1,4) -> 2014

  * SUBSTR("20140323", 5) -> 0323

    

#### MySQL 소수점 처리

* **CEIL( )** : 올림 

  * SELECT CEIL(5.5) -> 6

* **FLOOR( )** : 내림

  * SELECT FLOOR(5.5) -> 6

* **ROUND( )** : 반올림

  * ROUND(5.556901, 4)  -> 5.5569

    

#### ORDER BY 응용

* 최대값 상위 3개 뽑아보기

```
SELECT *
FROM products
ORDER BY price DESC
LIMIT 3          # 가격 비싼 순으로 상위 3개 뽑기
```

* 최소값 하위 3개 뽑아보기

```
SELECT *
FROM products
ORDER BY price ASC
LIMIT 3         # 가격 싼 순으로 하위 3개 뽑기
```



* 해커랭크 문제 1)

  Write a query that prints a list of employee names (i.e.: the *name* attribute) for employees in **Employee** having a salary greater than per month who have been employees for less than months. Sort your result by ascending *employee_id*.

  **Input Format**

  The **Employee** table containing employee data for a company is described as follows:

  ![img](https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png)

  where *employee_id* is an employee's ID number, *name* is their name, *months* is the total number of months they've been working for the company, and *salary* is the their monthly salary.

  **Sample Input**

  ![img](https://s3.amazonaws.com/hr-challenge-images/19630/1458558612-af3da3ceb7-ScreenShot2016-03-21at4.32.59PM.png)

```
SELECT name
FROM employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id ASC 
```



* 해커랭크 문제 2)

Query the *Name* of any student in **STUDENTS** who scored higher than *Marks*. Order your output by the *last three characters* of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending *ID*.

**Input Format**

The **STUDENTS** table is described as follows: ![img](https://s3.amazonaws.com/hr-challenge-images/12896/1443815243-94b941f556-1.png) The *Name* column only contains uppercase (`A`-`Z`) and lowercase (`a`-`z`) letters.

**Sample Input**

![img](https://s3.amazonaws.com/hr-challenge-images/12896/1443815209-cf4b260993-2.png)

```
SELECT name
FROM students
WHERE marks > 75
ORDER BY RIGHT(name,3), id ASC
```



* 해커랭크 문제 3)

  Query the *Western Longitude* (*LONG_W*) for the largest *Northern Latitude* (*LAT_N*) in **STATION** that is less than . Round your answer to decimal places.

  **Input Format**

  The **STATION** table is described as follows:

  ![Station.jpg](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

  where *LAT_N* is the northern latitude and *LONG_W* is the western longitude.

  ```
  SELECT ROUND(LONG_W,4)       # 4자리까지만 남기고 반올림
  FROM station                 # 테이블명
  WHERE LAT_N < 137.2345
  ORDER BY LAT_N DESC          # LAT_N을 가진 데이터를 뽑기 위해 내림차순 정렬
  LIMIT 1                      # 내림차순 정렬 중에 가장 상위의 것을 가져오면 LAT_N
  ```

  



