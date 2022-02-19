

# SQL



### 조건에 맞는 데이터 검색하기

* 실제 데이터를 가져올 때 컬럼 속의 모든 데이터를 볼 일은 사실 자주 없음

* 특정 이름을 가진 Customer를 데리고 오거나 특정 가격 이상인 물건들만 출력해서 본다거나하는 작업들을 훨씬 많이 함. SQL로 이런 작업들을 하기 위해서 알아야하는 것이 바로 **WHERE절**!

  

------



### 예제로 알아보기

#### 비교연산자와 논리연산자

##### https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all

```
SELECT *
FROM customers
WHERE country = 'Germany'              # Germany에 관련된 것만 뽑아냄
```

| **비교 연산자** |           설명            |
| :-------------: | :-----------------------: |
|        =        |           같다            |
|       <>        |          다르다           |
|        <        |        미만(작다)         |
|        >        |        초과(크다)         |
|       <=        | 이하(또는 보다 크지 않음) |
|       >=        | 이상(또는 보다 작지 않음) |

* 비교연산자는 특정 컬럼이 특정 값을 가지는 데이터만 불러오기 위해서 사용함
* =, <>, >= , <= , >, < 형태로 사용

* 숫자뿐만 아니라 문자도 비교 가능

  ```
  SELECT *
  FROM customers
  WHERE customerName < "B"
  ```

  * 알파벳 순서에 따라서 문자 'B' 이전에 오는 데이터들만 검색하게 됨 

* 다양한 조건을 결합하고 싶을 때

  ```
  SELECT *
  FROM customers
  WHERE customerName < "B" AND country = 'Germany'
  ```

  * 비교연산자 AND : 조건을 둘 다 만족하는 행만 보여줌

  ```
  SELECT *
  FROM customers
  WHERE customerName < "B" OR country = 'Germany'
  ```

  * 비교연산자 OR : 둘 중에 하나라도 만족하는 행만 보여줌

    

------



####  LIKE, IN, BETWEEN, IS NULL

```
SELECT *
FROM customers
WHERE country LIKE 'Br%'   # % : wildcard(와일드카드) 어떤 것이 와도 상관 없다.
```

* country라는 컬럼에 들어있는 값이 'Br'로 시작하는 국가명을 보고 싶다

* 'Br%' 에서 % 기호는 뒤에 어떤 문자가 와도 혹은 문자가 안와도 상관없다는 뜻 ( % 기호는 원하는 문자 앞, 뒤에 넣을 수도 있음)
* % 기호도 예약어임
* 만약,  찾고 싶어하는 키워드가 명확하다 즉, 패턴을 가지고 데이터를 불러오고 싶은게 아니라면 'LIKE' 말고  ' = ' (비교연산자)를 사용하는 게 속도면에서는 훨씬 빠름

```
SELECT *
FROM customers
WHERE country IN ('germany', 'France')
```

* Germany를 country로 가진 사람과 France를 country로 가진 사람을 함께 보고 싶다

* **WHERE country = 'Germany' OR country = "France"** 이렇게 조건문을 써도 동일한 결과를 반환함

```
SELECT *
FROM customers
WHERE customerID BETWEEN 3 AND 5
```

* customerID가 3과 5를 포함하고 3과 5사이에 들어가는 값을 가질 때 결과를 출력해라

* **WHERE customerID >= 3 AND customerID <= 5** 이렇게 조건문을 써도 동일한 결과를 반환함

```
SELECT *
FROM customers
WHERE customerID IS NULL
```

* IS NULL :  테이블 내에 데이터가 입력되지 않는 부분을 검색할 때 쓰는 예약어

* WHERE customerID  = NULL 이렇게 하면 검색 안됨. 비어있는 값인 null은 조금 특별한 값이므로 일반적인 비교연산자로 검색하면 안됨.

* NULL (= NaN) : 숫자도 아니고 문자도 아니다. 비어있는 값!

  

------



#### LIKE 심화

```
SELECT *
FROM customers
WHERE country LIKE 'B_ _ _ _ _'
```

* _ 의 의미 : B로 시작하면서 B뒤에 5글자가 따라온다.

```
SELECT *
FROM customers
WHERE discount LIKE '50\%' 
```

* 50% 할인율을 가지는 고객을 찾아라
* \ : 이스케이프 문자 (백슬래시) 예약어로부터 탈출한다 (Mysql)
* 50%에서 %를 그대로 쓰면  %는 예약어이므로 %앞에 \ 를 써주면 된다.

```
SELECT *
FROM customers
WHERE discount LIKE '_ _\%' 
```

* 두 자릿수 디스카운트를 받는 사람을 찾아 보고 싶다

* _ _ : 어떤 숫자가 들어가도 상관없다

  

------



### 예제로 알아보기

#### DISTINCT

* 해커랭크 문제 1 ) 

  Query the list of *CITY* names starting with vowels (i.e., `a`, `e`, `i`, `o`, or `u`) from **STATION**. Your result *cannot* contain duplicates.

  **Input Format**

  The **STATION** table is described as follows:

  ![Station.jpg](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

  where *LAT_N* is the northern latitude and *LONG_W* is the western longitude.

```
SELECT DISTINCT city
FROM station
WHERE city LIKE'a%' 
OR city LIKE'e%' 
OR city LIKE'i%' 
OR city LIKE'o%' 
OR city LIKE'u%'
```

* 중복된 city가 나오지 않게 하려면 **DISTINCT 예약어** 활용!

  

* 해커랭크 문제 2 )

Query the list of *CITY* names from **STATION** that *do not start* with vowels and *do not end* with vowels. Your result cannot contain duplicates.

**Input Format**

The **STATION** table is described as follows:

![Station.jpg](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where *LAT_N* is the northern latitude and *LONG_W* is the western longitude.

```
SELECT DISTINCT city
FROM station
WHERE city NOT LIKE 'a%' 
AND city NOT LIKE 'e%' 
AND city NOT LIKE 'i%' 
AND city NOT LIKE 'o%'
AND city NOT LIKE 'u%'
AND city NOT LIKE '%a'
AND city NOT LIKE '%e'
AND city NOT LIKE '%i'
AND city NOT LIKE '%o'
AND city NOT LIKE '%u'
```

