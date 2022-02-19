# SQL



## Data Table

* 기업에서 데이터는 테이블 형태로 저장됨 (흔히 말하는 표 형식으로 저장)

* 표는 열과 행으로 이루어져 있으며, 보통 컬럼(Column / 열)과 로우(Row / 행)라고 말하기도 함

  

### 예제로 알아보기

###### https://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all

* customers라고 하는 테이블에 존재하는 코든 데이터들을 빠짐없이 가져오기 원할때 명령어

  ```
  SELECT *
  FROM customers;
  ```

  * FROM : 어떤 테이블에서 원하는 데이터를 가지고 올 것인지를 보여주는 것
  * SELECT : 무엇을 가져올 것인지
  * SELECT * :  * 기호(Asterisk / 아스타)는 전체 컬럼의 모든 내용을 다 보여주는 약속된 기호

* CustomerName 컬럼만 보고 싶을 때

  ```
  SELECT customerName
  from customers;
  ```

* 다수의 컬럼을 보고 싶을 때

  ```
  SELECT customerName, address
  from customers;
  ```

  * SELECT 컬럼명, 컬럼명, ... : SELECT 다음에 컬럼명을 추가하여 다수의 원하는 컬럼을 볼 수 있음

* 데이터 양이 많을 때 원하는 데이터를 가져오는 팁

  ```
  SELECT customerName, Address
  from customers
  LIMIT 10
  ```

  * LIMIT 예약어를 활용하여 데이터를 10개만 가져오는 방법도 존재  -> 데이터 구조를 빠르게 파악하여 SQL문 작성

  