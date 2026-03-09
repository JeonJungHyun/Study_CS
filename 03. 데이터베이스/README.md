# 💾 03. 데이터베이스

<details> <summary>1. 데이터베이스란?</summary> </br>
  
❶ 데이터베이스 </br>
: 데이터를 체계적으로 저장하고 관리하기 위한 시스템 </br>
단순히 데이터를 저장하는 공간이 아니라, 데이터를 효율적으로 저장하고 조회하며 여러 사용자가 동시에 사용할 수 있도록 관리하는 구조. </br>

예를 들어 쇼핑몰 서비스에서는 다음과 같은 데이터가 존재한다. </br>
- 회원 정보
- 상품 정보
- 주문 정보
- 리뷰
- 장바구니

</br>

❷ 데이터베이스가 필요한 이유 </br>
데이터를 단순한 파일 형태로 저장하면 여러 문제가 발생한다. </br>

  - 데이터 중복 문제 </br>
  예를 들어 주문 데이터를 저장할 때 사용자 정보까지 함께 저장한다면 </br>
  주문이 많아질수록 같은 사용자 정보가 계속 반복 저장된다. </br>
  -> 저장 공간이 낭비된다. </br>

  - 데이터 불일치 문제 </br>
  사용자의 주소가 변경되었는데 주문 데이터에는 예전 주소가 그대로 남아 있을 수 있다. </br>
  이처럼 `서로 다른 데이터가 존재하게 되는 문제`를 데이터 불일치라고 한다. </br>

  - 데이터 검색 속도 문제 </br>
  파일에서 데이터를 찾으려면 전체 파일을 하나씩 모두 탐색해야 한다. </br>
  데이터가 많아질수록 `검색 속도는 매우 느려진다`. </br>

  이러한 문제를 해결하기 위해 데이터를 체계적으로 저장하고 관리하는 시스템인 데이터베이스가 사용된다. </br>

</details>

<details> <summary>2. DBMS(Database Management System)</summary> </br>

❶ DBMS란? </br> 
DBMS(Database Management System)는 `데이터베이스를 생성하고 관리하는 소프트웨어`이다. </br>
즉, 사용자가 데이터베이스를 직접 다루는 것이 아니라 `DBMS를 통해 데이터를 저장하고 조회한다.` </br>

DBMS는 다음과 같은 역할을 수행한다. </br>
1️⃣ 데이터를 저장하고 관리 </br>
2️⃣ SQL을 해석하고 실행 </br>
3️⃣ 결과를 어플리케이션에 전달 </br> 
4️⃣ 동시성 제어 (Concurrency Control) </br>
여러 사용자가 동시에 데이터에 접근할 때 데이터 일관성을 유지한다. </br>

❸ 대표적인 DBMS </br>
- MySQL
- PostgreSQL
- Oracle
- SQLite
- MariaDB

<img width="2318" height="1428" alt="image" src="https://github.com/user-attachments/assets/bcfa4aa1-be8d-4c33-8d60-e6ec0f1ce183" /> </br>
위의 그림처럼 데이터베이스 위에 DBMS 가 있고, 그 위에 응용 프로그램이 있으며, 이러한 구조를 기반으로 데이터를 주고받는다. </br>
예를 들어 MySQL 이라는 DBMS가 있고 그 위에 응용 프로그램에 속하는 Node.js나 php 에서 해당 데이터베이스 안에 있는 데이터를 끄집어내 </br>
해당 데이터 관련 로직을 구축할 수 있는 것이다. </br>

</details>

<details> <summary>3. 관계형 데이터베이스(RDB)</summary> </br>
  
❶ 관계형 데이터베이스 </br>
관계형 데이터베이스(Relational Database)는 데이터를 테이블(Table) 형태로 저장하는 데이터베이스다. </br>
각 테이블은 서로 관계(Relation) 를 통해 연결된다. </br>
예를 들어 다음과 같은 구조가 있을 수 있다. </br>

User 테이블 </br>
| id | name | email                           |
| -- | ---- | ------------------------------- |
| 1  | 정현   | [a@test.com](mailto:a@test.com) |
| 2  | 민수   | [b@test.com](mailto:b@test.com) |

</br>

Order 테이블 </br>
| id | user_id | price |
| -- | ------- | ----- |
| 1  | 1       | 20000 |
| 2  | 1       | 5000  |

</br>

여기서 user_id를 통해 주문 정보와 사용자 정보가 연결된다. </br>
이처럼 여러 테이블이 서로 연결되는 구조를 관계(Relation) 라고 한다. </br>
그래서 이러한 데이터베이스를 관계형 데이터베이스(RDB) 라고 부른다. </br>

</details>

<details> <summary>4. 테이블 구조 (Table / Row / Column)</summary> </br>
관계형 데이터베이스는 기본적으로 다음과 같은 구조를 가진다. </br>

</br>

❶ Table </br>
데이터를 저장하는 표 형태의 구조이다. </br>
- Users
- Products
- Orders

❷ Row (Record) </br>
테이블에 저장된 하나의 데이터 단위이다. </br>
  ex) </br>
1 | 정현 | a@test.com

❸ Column (Field) </br>
데이터의 속성 또는 항목을 의미한다. </br>
  ex) </br>
- id
- name
- email
</details>

<details> <summary>5. Key (Primary Key / Foreign Key)</summary> </br>
❶ Primary Key (PK) </br>

후보키(candidate key) 중에서 선택된 키로, 테이블의 각 행을 유일하게 식별할 수 있는 키이다. </br>
테이블에서 각 데이터를 유일하게 식별할 수 있는 값이다. </br>
개체 무결성 제약조건을 만족해야 한다. </br>

❷ Foreign Key (FK) </br>

다른 테이블의 Primary Key를 참조하는 값이다. </br>
릴레이션 간 관계(Relationship)을 표현한다. </br>
참조 무결성 제약조건을 만족해야 한다. </br>

</details>

<details> <summary>6. 무결성 제약조건 </summary> </br>
데이터베이스에 저장된 데이터의 무결성을 보장하고, 상태를 일관되게 유지하기 위한 제약 조건들. </br>

</br>

❶ 개체 무결성 제약조건 </br> 
기본키를 구성하는 모든 속성은 NULL값을 가지면 안되는 규칙 </br>
--> 전체 혹은 일부가 널값을 가지면 유일하게 판단할 수 없기 때문

❷ 참조 무결성 제약조건 </br>
외래키 값은 NULL이거나 참조 릴레이션의 기본키 값과 동일해야 한다는 규칙 </br>
추가로 부모 릴레이션의 삭제 / 수정시 제약을 받는다 </br>

</details>

<details><summary>7. SQL</summary> </br>

1️⃣ SQL이란? </br>
SQL(Structured Query Language)은 데이터베이스에 저장된 데이터를 조회, 삽입, 수정, 삭제하기 위해 사용하는 표준 언어이다. </br>
데이터베이스 관리 시스템(DBMS)은 SQL을 통해 데이터를 관리한다. </br>
예를 들어, 사용자 정보를 조회하거나 새로운 데이터를 추가할 때 SQL을 사용한다. </br>

2️⃣ SQL의 종류 </br>
SQL은 크게 3가지 종류로 나뉜다. </br>

  ❶ DDL (Data Definition Language) </br>
  테이블이나 관계의 구조를 생성하는데 사용되는 데이터 정의어 </br>
  - CREATE
  - ALTER
  - DROP

  ❷ DML(Data Manipulation Language) </br>
  테이블의 데이터를 검색, 삽입, 수정, 삭제하는데 사용되는 데이터 조작어 </br>
  - SELECT
  - INSERT
  - UPDATE
  - DELETE

  ❸ DCL(Data Control Language) </br>
  데이터의 사용 권한을 관리하는데 사용되는 데이터 제어어 </br>
  - GRANT
  - REVOKE

  🌟 삭제 명령어들의 차이 </br>
   - DROP </br>
    - 테이블 자체를 삭제 </br>
    - Rollback 불가능 </br>
   - DELETE </br>
    - 데이터만 삭제 </br>
    - Commit 이전에는 Rollback 가능 </br>
   - TRUNCATE </br>
    - 테이블을 최초 생성된 초기 상태로 만듬 </br>
    - Rollback 불가능 </br>
    - 자동 증가값(auto increment)이 초기화된다 </br>

3️⃣ CRUD </br>
CRUD는 데이터베이스에서 데이터를 처리할 때 사용하는 기본적인 4가지 작업을 의미한다. </br>

| 작업 | 설명 | SQL |
|-----|-----|-----|
| Create | 데이터를 생성 | INSERT |
| Read | 데이터를 조회 | SELECT |
| Update | 데이터를 수정 | UPDATE |
| Delete | 데이터를 삭제 | DELETE |

예시) </br>
SELECT * FROM users; </br>
INSERT INTO users(name) VALUES('홍길동'); </br>
UPDATE users SET name='김철수' WHERE id=1; </br>
DELETE FROM users WHERE id=1; </br>
 
</details>

<details><summary>8. 정규화 (Normalization)</summary> </br>

1️⃣ 정규화란? </br>
정규화(Normalization)는 데이터베이스 설계 과정에서 </br>
`데이터의 중복을 최소화하고 데이터 무결성을 유지하기 위해 테이블을 구조적으로 분해하는 과정`이다. </br>

정규화를 통해 다음과 같은 문제를 방지할 수 있다.

- 데이터 중복
- 데이터 수정 이상 
- 데이터 삽입 이상 
- 데이터 삭제 이상 

2️⃣ 이상현상 </br>
정규화를 하는 이유는 **이상 현상(Anomaly)** 을 방지하기 위해서이다. </br>

❶ 삽입 이상 (Insertion Anomaly) </br>
불필요한 데이터가 함께 입력되지 않으면 원하는 데이터를 추가할 수 없는 문제. </br>

예를 들어  
강의 정보와 교수 정보가 하나의 테이블에 있을 경우

| 강의 | 교수 |
|----|----|
| DB | 김교수 |

새로운 교수를 추가하려고 해도  
강의 정보가 없으면 데이터를 넣을 수 없는 문제가 발생한다.

</br>

❷ 수정 이상 (Update Anomaly) </br>
같은 데이터가 여러 곳에 중복 저장되어 있을 때 하나만 수정하면 **데이터 불일치가 발생하는 문제**. </br>
예를 들어 교수 이름이 여러 행에 저장되어 있다면 모든 데이터를 수정해야 한다. 

❸ 삭제 이상 (Deletion Anomaly) </br>
데이터를 삭제할 때 **원하지 않는 정보까지 함께 삭제되는 문제**. </br>
예를 들어 강의를 삭제했는데 해당 교수 정보도 함께 사라질 수 있다. </br>

3️⃣ 정규화의 종류 </br>

❶ 제 1정규화(1NF) </br>
제1정규형은 **모든 컬럼 값이 원자값(Atomic Value)을 가져야 한다**는 규칙이다. </br>
즉 하나의 컬럼에는 **하나의 값만 저장되어야 한다.** </br>

✏️ 정규화 전

| id | 이름 | 전화번호 |
|----|----|----|
| 1 | 전정현 | 010-1111, 010-2222 |

✏️ 정규화 후

| id | 이름 | 전화번호 |
|----|----|----|
| 1 | 전정현 | 010-1111 |
| 1 | 전정현 | 010-2222 |

</br>

❷ 제 2정규화(2NF) </br>
기본키가 아닌 속성들은 기본키에 대해 완전 함수적 종속인 관계 </br>
즉 기본키의 **일부에만 종속되는 컬럼을 분리한다.** </br>

💬 예시

| 학생ID | 강의ID | 학생이름 | 강의이름 |
|-------|-------|-------|-------|

여기서

- 학생이름 → 학생ID에만 의존
- 강의이름 → 강의ID에만 의존

따라서 테이블을 분리한다.

학생 테이블

| 학생ID | 학생이름 |
|------|------|

강의 테이블

| 강의ID | 강의이름 |
|------|------|

수강 테이블

| 학생ID | 강의ID |
|------|------|

❸ 제 3정규화(3NF) </br>
제3정규형은 **이행적 함수 종속을 제거하는 것**이다. </br>

💬 예시

| 학생ID | 학과ID | 학과이름 |
|------|------|------|

여기서

학생ID → 학과ID  
학과ID → 학과이름

즉 학과이름은 학생ID에 **간접적으로 의존**한다.
따라서 테이블을 분리한다.

학생 테이블

| 학생ID | 학과ID |
|------|------|

학과 테이블

| 학과ID | 학과이름 |
|------|------|

</br>

🌟 깜짝퀴즈 </br>

Q : 정규화를 하는 이유는 무엇인가요? </br>
A : 데이터 중복을 줄이고 삽입/삭제/수정 이상을 방지하기 위해 정규화를 수행합니다. </br>

Q: 1NF / 2NF / 3NF에 대해 설명해주세요. </br>
A : 1NF → 원자값. 2NF → 부분 함수 종속 제거. 3NF → 이행 함수 종속 제거 </br>

</details>

<details><summary>9. 비정규화 (Denormalization)</summary> </br>

1️⃣ 비정규화란? </br>
비정규화(Denormalization)는  
정규화된 테이블을 다시 **통합하거나 중복 데이터를 허용하여 성능을 향상시키는 과정**이다.

정규화는 데이터 중복을 줄이고 데이터 무결성을 높이지만  
테이블이 많이 분리되면서 **JOIN 연산이 많아져 성능이 저하될 수 있다.**

이러한 문제를 해결하기 위해 의도적으로 데이터 중복을 허용하는 것을 비정규화라고 한다. </br>

2️⃣ 비정규화가 필요한 이유 </br>

정규화를 하면 다음과 같은 문제가 발생할 수 있다. </br>

- 테이블이 너무 많이 분리됨
- JOIN 연산 증가
- 조회 성능 저하

특히 **조회(Read)가 많은 서비스**에서는 비정규화를 통해 성능을 개선하기도 한다. </br>

✏️ 정규화된 구조

User 테이블

| user_id | name |
|--------|------|

Order 테이블

| order_id | user_id | price |
|---------|--------|------|

사용자 이름을 조회하려면
SELECT *
FROM order o
JOIN user u
ON o.user_id = u.user_id

JOIN 연산이 필요하다.

✏️ 비정규화 구조

Order 테이블

| order_id | user_id | user_name | price |
|---------|--------|-----------|------|

이렇게 사용자 이름을 함께 저장하면 JOIN 없이 조회할 수 있다. </br>

4️⃣ 비정규화 장점 </br>
- 빠른 데이터 조회 --> JOIN 비용이 줄어듬
- 데이터 조회 쿼리가 간단해짐 --> 버그 발생 가능성 하락










</details>

<details><summary>10. Index</summary> </br>

1️⃣ Index란? </br>
Index는 데이터베이스에서 `데이터 검색 속도를 빠르게 하기 위해 사용하는 자료구조`이다. </br>
책의 목차(Index)와 같은 역할을 한다. </br>
<키 값, 포인터> 쌍으로 구성되어 있다. </br>

2️⃣ Index가 필요한 이유 </br>
Index가 없다면 데이터 검색 시 테이블의 모든 데이터를 하나씩 확인해야 한다. </br>
인덱스를 걸고자 하는 필드의 값이 다양한 값을 가지는 경우 사용한다. </br>

3️⃣ Index의 동작 방식 </br>
대부분의 DBMS는 Index를 **B-Tree 구조**로 관리한다. </br>
B-Tree는 데이터를 정렬된 상태로 저장하여 검색 속도를 빠르게 하는 자료구조이다. </br>

4️⃣ Index의 장점 </br>
- 데이터 검색 속도 향상 </br>
- 대용량 데이터에서 빠른 조회 가능 </br>
- WHERE / JOIN / ORDER BY 성능 향상 </br>

5️⃣ Index의 단점 </br>
- 추가 저장 공간이 필요하다 </br>
- INSERT / UPDATE / DELETE 성능이 느려질 수 있다 </br>

데이터가 변경될 때마다 Index도 함께 수정되어야 하기 때문이다. </br>

6️⃣ Index 사용 예시 </br>

예를 들어 users 테이블에서 email로 자주 검색한다면 Index를 생성할 수 있다. </br>

CREATE INDEX idx_user_email </br>
ON users(email); </br>

이렇게 Index를 생성하면 email 컬럼을 이용한 검색 속도가 빨라진다. </br>

🌟 깜짝퀴즈 </br>

Q : Index가 무엇인가요? </br>
A : Index는 데이터베이스에서 검색 성능을 향상시키기 위해 사용되는 자료구조입니다. </br>
    데이터를 빠르게 조회할 수 있도록 도와줍니다. </br>

Q : Index의 단점은? </br>
A : 추가 저장 공간이 필요하고 데이터 삽입, 수정, 삭제 시 Index도 함께 갱신되어 성능이 저하될 수 있습니다. </br>

Q : 언제 Index를 사용해야 하나요? </br>
A : 검색이 자주 발생하는 컬럼. JOIN에 사용되는 컬럼. WHERE 조건에 자주 사용되는 컬럼 시 주로 사용합니다. </br>

</details>






























  
