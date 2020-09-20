### SQL Function (3편 - Aggregate Function)

**주로 수학적인 연산과 GROUP BY라는 2개의 주제를 갖고 해당 강의를 진행하는 파트**

- `SELECT COUNT(*) FROM books;` : 테이블 내에 있는 데이터를 카운트 해줄 수 있게 도와주는 함수는 Count라는 함수를 사용한다.

예시) Count

```sql
SELECT COUNT(*) FROM books;

SELECT COUNT(author_fname) FROM books;

SELECT COUNT(DISTINCT author_fname) FROM books;

SELECT COUNT(DISTINCT author_lname) FROM books;

SELECT COUNT(DISTINCT author_lname, author_fname) FROM books;

SELECT title FROM books WHERE title LIKE '%the%';

SELECT COUNT(*) FROM books WHERE title LIKE '%the%';
```

---

- `SELECT title, author_lname FROM books GROUP BY author_lname;`: 특정 칼럼을 그룹화해서 값을 조회하게끔 도와주는 명령어다

예시) Group By

```sql
SELECT title, author_lname FROM books;

SELECT title, author_lname FROM books
GROUP BY author_lname;

SELECT author_lname, COUNT(*)
FROM books GROUP BY author_lname;


SELECT title, author_fname, author_lname FROM books;

SELECT title, author_fname, author_lname FROM books GROUP BY author_lname;

SELECT author_fname, author_lname, COUNT(*) FROM books GROUP BY author_lname;

SELECT author_fname, author_lname, COUNT(*) FROM books GROUP BY author_lname, author_fname;

SELECT released_year FROM books;

SELECT released_year, COUNT(*) FROM books GROUP BY released_year;

SELECT CONCAT('In ', released_year, ' ', COUNT(*), ' book(s) released') AS year FROM books GROUP BY released_year;
``
```

---

- `SELECT MIN(released_year) FROM books;` : 조회하는 테이블 내에 특정 칼럼의 최솟값 찾기

- `SELECT MAX(pages) FROM books;`: 조회하는 테이블 내에 특정 칼럼의 최댓값 찾기

예시) Min/Max

```sql
SELECT MIN(released_year)
FROM books;

SELECT MIN(released_year) FROM books;

SELECT MIN(pages) FROM books;

SELECT MAX(pages)
FROM books;

SELECT MAX(released_year)
FROM books;

SELECT MAX(pages), title
FROM books;
```

---

- `SELECT * FROM books WHERE pages = (SELECT Min(pages) FROM books);` : 서브쿼리라는 개념을 사용하는데, 하나의 쿼리문 내에 `WHERE pages = (SELECT Min(pages) FROM books)`처럼 쿼리문을 한 번 더 사용하는 것이다. 다만, 문제가 있다. 데이터가 많아지면 속도가 느리다. 그리고 Min, Max 자체도 사용하는데 속도가 느려서 이를 우회해서 사용하는 방법을 써야한다. 쿼리문을 보면 어떤 기능을 사용하기 위한 문장인지 바로 이해는 되지만 속도에 영향을 주기 때문에 사용하기에 따라 성능에 지장이 있을 수 있다.

```sql
-- 기존에 이미 충분히 활용했지만, 아래 쿼리문들은 Max, Min의 기능을 동일하게 작업하면서 속도에 영향을 주지 않는 쿼리문으로 활용 가능하다.
SELECT * FROM books
ORDER BY pages ASC LIMIT 1;

SELECT title, pages FROM books
ORDER BY pages ASC LIMIT 1;
```

예시) SubQuery

```sql

SELECT * FROM books
WHERE pages = (SELECT Min(pages)
                FROM books);

SELECT title, pages FROM books
WHERE pages = (SELECT Max(pages)
                FROM books);

SELECT title, pages FROM books
WHERE pages = (SELECT Min(pages)
                FROM books);

SELECT * FROM books
ORDER BY pages ASC LIMIT 1;

SELECT title, pages FROM books
ORDER BY pages ASC LIMIT 1;

SELECT * FROM books
ORDER BY pages DESC LIMIT 1;
```

---

- Group By & Min/Max를 함께 사용한 쿼리문 예시

예시) Group By & Min/Max

```sql
SELECT author_fname,
       author_lname,
       Min(released_year)
FROM   books
GROUP  BY author_lname,
          author_fname;

SELECT
  author_fname,
  author_lname,
  Max(pages)
FROM books
GROUP BY author_lname,
         author_fname;

SELECT
  CONCAT(author_fname, ' ', author_lname) AS author,
  MAX(pages) AS 'longest book'
FROM books
GROUP BY author_lname,
         author_fname;
```

---

- 특정 Colum의 값을 모두 더하는 연산, SUM

```sql

SELECT SUM(pages)
FROM books;

SELECT SUM(released_year) FROM books;

SELECT author_fname,
       author_lname,
       Sum(pages)
FROM books
GROUP BY
    author_lname,
    author_fname;

SELECT author_fname,
       author_lname,
       Sum(released_year)
FROM books
GROUP BY
    author_lname,
    author_fname;
```

---

- 특정 Colum의 평균값을 구하기 위해 사용하는 함수, AVG

```sql
SELECT AVG(released_year)
FROM books;

SELECT AVG(pages)
FROM books;

SELECT AVG(stock_quantity)
FROM books
GROUP BY released_year;

SELECT released_year, AVG(stock_quantity)
FROM books
GROUP BY released_year;

SELECT author_fname, author_lname, AVG(pages) FROM books
GROUP BY author_lname, author_fname;
```
