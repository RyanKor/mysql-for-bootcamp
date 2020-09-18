# udemy assignment

- udemy 과제 코드 정리하기

## 과제 명령어 정리하기

- `CREATGE TABLE unique_cats(cat_id INT NOT NULL, name VARCHAR(100), age INT, PRIMARY KEY (cat_id));` : primary key 설정해서 사용하기

- `create table unique_cats2(cat_id int not null auto_increment, name varchar(100));` : primary key를 사용할 때 auto_increment를 사용해서 column 값이 생성될 때마다 자동으로 cat_id라는 column이 증가할 수 있게 지원해준다.

- `create table employee(id int not null auto_increment, last_name varchar(100) not null, first_name varchar(100) not null, middle_name varchar(50) not null, age int not null, current_status varchar(100) not null default 'employed', primary key (id));` : primary key, auto_increment, 그리고 default value 설정까지 배운 내용들이 들어간 과제 명령어다
