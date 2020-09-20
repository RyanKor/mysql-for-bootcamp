### 1. 명령어 정리하는 목적

- SQL 명령어 자체를 내가 너무 모른다. 정리해서 사전처럼 사용하게끔 배우는 명령어들을 모두 기록해놓자.

- 매번 스택 오버플로우 찾아가서 간단한 명령어나 배웠던 내용들을 서칭하지 말고, 내 깃헙을 사전처럼 사용할 수 있게 틈틈이 기록하는 것이 더 중요하다.

- 최신 SQL 명령어는 대문자가 아니라 소문자로 입력해도 명령어를 이해하니, 소문자로 쿼리를 보내도 무방하다.

- `CREATE DATABASE <DATABASE NAME>;`: 데이터베이스 생성하기

- `DROP DATABASE <DATABASE NAME>;` : 데이터베이스 삭제하기 (MongoDB에서도 명령어는 동일하게 작동)

- `DROP TABLE <TABLE NAME>;` : 테이블 삭제하기

- `SELECT database();` : 현재 사용 중인 데이터베이스 조회하기

- `CREATE TABLE <DATABASE NAME> (colum name1, colum name2, ...)` : 데이터베이스 테이블 선택하기

- `SHOW TABLES;` : 현재 사용 중인 데이터베이스의 테이블을 확인이 가능하다.

- `DESC <TABLE NAME>;` : 현재 데이터베이스 내에 있는 테이블을 지정하고, 내림차순으로 내부의 colum 값을 보여준다

- `INSERT INTO <TABLE NAME>(colum name, colum name) VALUES ("value1", value2), ("value1", value2), ("value1", value2);` : 테이블에 데이터 삽입하기

- `CREATE TABLE cats2 (name VARCHAR(100) NOT NULL, age INT NOT NULL);` : 값을 null (비워진 값)으로 둘 수 없다.

- `CREATE TABLE cats3 (name VARCHAR(100) DEFAULT 'unnamed', age INT DEFAULT 99);` : DEFAULT 값을 설정하기

- `SELECT * FROM <COLUM NAME>` : 선택한 칼럼 값에 있는 모든 내용물을 가져올 수 있는 명령어다.

- `SHOW WARNINGS;` : 저장한 데이터와 관련해 사용자에게 경고문 또는 에러 등에 대한 메세지를 볼 수 있게 지원해준다.

- `SELECT name AS 'cat name', breed AS 'kitty breed' FROM cats;`: as를 사용하면 colum의 이름을 좀 더 사용자가 이해하기 쉬운 형태로 바꿔줄 수 있다.
  (사실 파이썬이나 다른 언어에서도 많이 쓰이는 형태)

- `update cats set breed="Shorthair" where breed="tabby";` : Colum 업데이트를 위해 `update` 키워드를 사용하고, `set`을 사용해 변경할 값을 만든 후, where 조건문으로 변경할 값을 찾는다.

- `delete from <tables> where <colum condition>` : 테이블에서 삭제할 조건의 colum을 택하고 삭제 명령을 내린다.
