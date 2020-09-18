# SQL Study with Mysql Coures

## 학습 자료

- Udemy MySQL Bootcamp

- MySQL 자체가 워낙 DBMS 제품 중에서는 꽤 많이 사용되었던 소프트웨어이기 때문에 운영와 유지에 있어서 안정성을 보이는 장점이 분명히 있다.

- 데이터 저장 타입을 워낙 엄격하게 지정해서 사용하다 보니, 데이터가 누락되거나 자료형에 맞지 않는 데이터들을 저장할 수 없기 때문에 완결성이라 해야할까? 데이터 타입이 왜곡되거나 맞지 않는 형태가 저장되는 것을 허락하지 않는다.

- MySQL의 경우, 규모가 어느정도 있는 업체에서 활용도가 높고 (실제로 많은 스마트 팩토리, 그리고 IT 기업, 물류 업체에서 활용하는 것 같다) ERP 처럼 회사 규모가 큰 업체들에서도 활용도가 적극적으로 높은 것 같다.

- 아직 배우는 초보자지만, 데이터베이스에서 다루는 데이터 규모가 커질수록 데이터베이스의 설계 부분에 대한 고민이 많이 담겨야한다는 글들을 종종 목격한다. 단순히 쿼리를 보내서 결과 값을 받는 것 이상으로 데이터베이스를 다루는 일은 꽤 가치가 있는 일인 것 같다.

- 아마 이 Udemy Course에서는 쿼리를 어떻게 조합해서 사용할지에 대해 능숙하게 배우는 것이 목표가 될 것이다.

- 평생학습이 필요하다는 말이 제일 어울리는 직군이 개발자가 아닐까 싶다.

- Slides : [Getting Started with MySQL](http://webdev.slides.com/coltsteele/mysql-97-98#/0/0/0)

## SQL 학습하면서 기록할 때, 유의사항

- 프로그래밍 언어처럼 VS CODE를 IDE로 사용할 수는 없고, 콘솔과 Workbench를 이용해서 작업하는 상황이라, 코드 자체를 깃헙으로 업로드 할 수는 없다.

- 그래서 명령어 위주로, 그리고 복잡한 쿼리 등을 사용하는 경우 (MySQL Join 등) 해당 내용들을 즉각 기록하는 형태로 배우는 것이 제일 좋을 것 같다.

- 문득드는 생각은, MySQL 하나를 잘 파놓으면 결국엔 Oracle이나 SQL Server 등과 같은 다른 SQL 학습에도 매우 용이할 것이고,

- 무엇보다 ORM 등 객체지향 프로그래밍 언어에서 사용할 때 어떤 프로그래밍 언어로 프로젝트를 진행하더라도 러닝 커브가 매우 높아질 것이란 생각이 든다.

- 거기다 Mongo DB와 같은 NoSQL 진영을 학습하는 상황에서도 이해도 자체가 많이 다를 것이란 생각이 든다 (NoSQL 자체가 SQL과 경쟁관계거나 반대의 개념이 아니기 때문에)

- 게다가 인공지능 등에 학습에도 활용도가 무궁무진하다 (전처리 등에 SQL이 활용되니)

- 일반적인 웹이나 모바일 개발자보다 데이터베이스 쪽으로 개발 커리어를 잡는 게 미래를 생각하면 더 나을지도? (데이터를 가공하는 직군은 시간이 지날 수록 수요는 더 커질 것이니)

## 명령어 정리하기

1. 명령어 정리하는 목적

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
