# 트랜잭션(Transaction)과 동시성 제어



## 개인적으로 이 책에서 제일 어려운 파트

- 실무에서 단일 쿼리를 DB에 던질 일은 거의 없고, 한덩어리의 쿼리를 던져서 정보를 처리해달라고 요청하는 경우가 일상인데, 이 때 `한 덩어리의 쿼리 처리 단위를 '트랜잭션'`이라고 한다

- 관계형 데이터 베이스를 이해하는데 가장 큰 걸림돌이자 가장 기본이 되는 부분은 데이터 베이스 내의 테이블들이 서로 얽히고 섥혀 있어 서로가 서로의 PK(Primary Key, 쉽게 말해 테이블 내에서 값이 불변하는 기본키)로 되어 있는데 한 개의 테이블에만 트랜잭션을 보내는 것이 아니라, 동시에 여러개의 테이블에 쿼리를 보낼 때, 내 이해력의 