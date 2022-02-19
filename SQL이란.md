# SQL

* 데이터베이스와 통신을 하기 위한 언어
* 크게 Data Query Language, Data Manipulation Langage로 나눌 수 있음

| **SELECT**                         | **DQL(Data Query Langage) 질의어**<br />데이터 꺼내오기 위한 질의어 |
| ---------------------------------- | ------------------------------------------------------------ |
| **INSERT<br />UPDATE<br />DELETE** | **DML(Data Manipulation Language) 조작어**<br />INSERT 데이터베이스에 데이터를 쌓기 위한 것<br />UPDATE 데이터를 수정하기 위한 것<br />DELETE 데이터를 지우기 위한 것 |

* SQL에서는 예약어(SQL에서 미리 설정해놓은 문법을 윈한 예약어)는 대문자로 쓰고,  나머지 문자들은 소문자로 많이 씀.

  ```
  SELECT city, state
  FROM station
  ```

  