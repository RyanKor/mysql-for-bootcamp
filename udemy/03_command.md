### 3. SQL 함수 사용법 정리 (1편 - STRING FUNCTION)

- `SELECT author_fname AS first, author_lname AS last, CONCAT(author_fname, ' ', author_lname) AS full FROM books;` : `CONCAT`을 사용해서 서로 다른 colum을 연결해 값을 보여주는 기능을 제공한다.

- `SELECT CONCAT_WS(' - ', title, author_fname, author_lname) FROM books;` : `CONCAT_WS`를 사용해서 중복되어 사용되는 문자열이 있다면, 한번만 입력해 사용할 수 있게 지원하는 함수가 있다. 이걸 풀어서 사용한다면 아래와 같은 명령어가 될 것이다.

`SELECT CONCAT(title, '-', author_fname, '-', author_lname) FROM books;` -> 불필요하게 '-'를 2번이나 사용했다.

- `SELECT SUBSTRING('Hello World', 1, 4);` : CONCAT 말고도 함수가 많다. 이번에 활용할 함수는 SUBSTRING이다. 문자열을 몇 개까지 사용자에게 보여줄 것인가에 대해 지정해주는 함수인데, 보기의 `1,4`처럼 구간을 지정할 수 있고,

`SELECT SUBSTRING('Hello World', 3);` : 갯수를 지정할 수도 있다

- 눈여겨 볼 점은 콜백처럼 함수 내에 함수를 또 넣어서 사용할 수 있다는 점인데

예시)

```sql
    SELECT CONCAT
        (
            SUBSTRING(title, 1, 10),
            '...'
        ) AS 'short title'
    FROM books;
```

- 이런 형태로 보여줄 단어 수를 SUBSTRING으로 줄이고, CONCAT으로 ...이라는 문자열을 추가해 활용하는 방식이 가능하다.

- `SELECT REPLACE('Hello World', 'Hell', '%$#@');` : Replace는 어떤 프로그래밍 언어를 배우더라도 항상 나오는 메소드이고, SQL에서도 빠지지 않고 등장했다.

- 자 여길 보면, 'Hello'의 Hell 부분을 '%\$#@' 의 내용으로 바꿔서 사용하게끔 지시한다.

예시)

```sql
SELECT REPLACE(title, 'e ', '3') FROM books;

-- SELECT
--    CONCAT
--    (
--        SUBSTRING(title, 1, 10),
--        '...'
--    ) AS 'short title'
-- FROM books;

SELECT
    SUBSTRING(REPLACE(title, 'e', '3'), 1, 10)
FROM books;
```

- 마찬가지로 Nested하게 함수를 사용할 수 있고, 문자열을 대체한 이후에 substring으로 일부만 보여줄 수 있게 활용하는 것도 가능하다.

- `SELECT CONCAT(author_fname, REVERSE(author_fname)) FROM books;` : Reverse라는 메소드가 따로 있는데, Python / JS 같은 경우 코드 자체를 활용해 작업이 되지만, SQL로 하면 쿼리가 더러워질 것 같으니 별도의 메소드를 만들었다는 느낌이 든다.

- `SELECT CONCAT(author_lname, ' is ', CHAR_LENGTH(author_lname), ' characters long') FROM books;` : 쿼리 값에 대항하는 문자열의 길이를 숫자형으로 알려주는 `CHAR_LENGTH`라는 함수

- `SELECT CONCAT('MY FAVORITE BOOK IS ', UPPER(title)) FROM books;` : UPPER를 사용하면 대문자로,

- `SELECT CONCAT('MY FAVORITE BOOK IS ', LOWER(title)) FROM books;` : LOWER를 사용하면 소문자로 문자를 변환한다.

예시)

```sql
--UPPER only takes one argument and CONCAT takes two or more arguments, so they can't be switched in that way.
--Upper, Lower는 한 개의 매개변수만을 받기 때문에 사용시 주의해야한다.

SELECT CONCAT(UPPER(author_fname, ' ', author_lname)) AS "full name in caps" FROM books;
SELECT CONCAT(UPPER(author_fname), ' ', UPPER(author_lname)) AS "full name in caps" FROM books;
```

### 4. SQL FUNCTION (2편 - Refining Our Selection)

- `SELECT DISTINCT author_fname, author_lname FROM books;` : 데이터베이스 내에 중복되는 값을 제거하고 값을 보여줄 수 있게 지원하는 쿼리는 `DISTINCT`를 사용한다.

- `SELECT released_year FROM books ORDER BY released_year DESC;` : `ORDER BY` 명령어를 사용하면 특정 colum을 기준으로 값을 정렬할 수 있다. 오름/내림차순으로 정렬하는 것이 가능하다.

- `SELECT released_year FROM books ORDER BY released_year ASC;` : 오름차순 정렬

- `SELECT title, author_fname, author_lname FROM books ORDER BY 1 DESC;` : 숫자를 ORDER BY에 입력한 것은 select에서 선택한 colum의 몇번째 값을 택했는지를 보여주는 값이다.

- `SELECT author_lname, title FROM books ORDER BY 2;` : 2번째, 그러니까 여기선 title을 선택해 정렬한다는 쿼리

- `SELECT author_fname, author_lname FROM books ORDER BY author_lname, author_fname;` : 2개 이상의 colum을 선택해 정렬할 수도 있다.

- `SELECT title, released_year FROM books ORDER BY released_year DESC LIMIT 1;` : `LIMIT` 를 사용해서 가져오는 쿼리 값을 제한할 수 있다

예시)

```sql

SELECT title, released_year FROM books
ORDER BY released_year DESC LIMIT 14;

SELECT title, released_year FROM books
ORDER BY released_year DESC LIMIT 0,5;

SELECT title, released_year FROM books
ORDER BY released_year DESC LIMIT 0,3;

SELECT title, released_year FROM books
ORDER BY released_year DESC LIMIT 1,3;

SELECT title, released_year FROM books
ORDER BY released_year DESC LIMIT 10,1;

SELECT * FROM tbl LIMIT 95,18446744073709551615;
```

- `SELECT title, author_fname FROM books WHERE author_fname LIKE '%da%';` : `LIKE`를 where과 사용하면 특정 colum에 있는 LIKE에 관련한 데이터를 모두 찾아서 반환해준다.

- 여기서 `% %`를 2번 사용하는 이유는 2개의 wildcard가 감싸고 있는 값과 매칭되는 결과값을 모두 서칭하기 위해서다.

```sql

SELECT title, author_fname FROM books WHERE author_fname LIKE '%da%';

SELECT title FROM books WHERE  title LIKE 'the';

SELECT title FROM books WHERE  title LIKE '%the';

SELECT title FROM books WHERE title LIKE '%the%';
```

- `SELECT title, stock_quantity FROM books WHERE stock_quantity LIKE '____';` : underscore를 4개 사용하면 4자리 숫자 자릿 수를 의미함. 갯수가 줄 때마다 한 자리씩 자릿 수를 줄이는 형태임

예시)

```sql

SELECT title, stock_quantity FROM books;

SELECT title, stock_quantity FROM books WHERE stock_quantity LIKE '__';

(235)234-0987 LIKE '(___)___-____'

-- 전화번호, ISBN 등 서칭할 때 사용하는 방법

SELECT title FROM books;

SELECT title FROM books WHERE title LIKE '%\%%'

SELECT title FROM books WHERE title LIKE '%\_%'
```
