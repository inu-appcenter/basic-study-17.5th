APP Center_Study_Week 7
---
# 데이터베이스
---
![](https://velog.velcdn.com/images/dlwjd8023/post/219d3249-3cfc-447f-8a1b-fb44a21a16f9/image.png)

### 데이터
- 현실 세계에서 사건이나 사물의 특징을 관할하거나 측정하여 기술하는 가공되지 않은 사실이나 값
- **단순 수집한 원시 자료**

### 정보
- 데이터를 의미있고 쓸모있는 내용으로 가공하여 체계적으로 조직한 것
- **데이터에 목적, 의미, 의도가 포함된 것**

### 데이터베이스
- 어떤 특정한 조직에서 여러 명의 사용자 또는 응용 시스템들이 공유하고 동시에 접근하여 사용할 수 있도록 통합하여 저장한 운영 데이터의 집합
- **전자적으로 저장된 체계적인 데이터 모음**

---
## 데이터베이스의 필요성

![](https://velog.velcdn.com/images/dlwjd8023/post/f13c028d-00e6-4fe7-bb8f-2a8f6559cc66/image.png)
### 기존: 파일 시스템
- 응용 프로그램별로 필요한 데이터를 별도의 파일로 관리
- 특정 경로에 파일을 저장
- 응용 프로그램별로 파일을 따로 유지 및 관리

### 문제점
#### 데이터의 중복
- 같은 고객에 대한 정보가 고객이름, 연락처, 아이디 파일에 각각 존재할 경우, 데이터의 일관성과 무결성을 지키기 어려움
- 데이터 일관성: 같은 시간에 조회하는 데이터는 항상 동일한 데이터임을 보증
- 데이터 무결성: 모든 데이터의 완전성, 일관성, 
 정확성을 나타냄

#### 데이터 파일에 종속적
- 프로그램 개발 시 데이터 파일의 양식에 맞추어 개발을 해야 함

#### 데이터 파일에 대한 동시 공유의 어려움
  - 하나의 기기에 데이터를 저장해야 함
  - 동시 수정이 발생하면, 데이터 중복 발생

#### 보안 회복이 어려움
  - 수정 삭제가 쉽고, 장애 발생 시 복구가 어려움

-> 이러한 문제를 해결하기 위해 데이터베이스가 사용됨

### 데이터베이스의 상세한 정의
- 통합된 데이터(Intergrated Data): 자료의 중복을 배제한 데이터의 모임
- 저장된 데이터(Stored Data): 컴퓨터가 접근할 수 있는 저장 매체에 저장된 자료
- 운영 데이터(Operational Data): 조직의 고유한 업무를 수행하는 데 없어서는 안 될 자료
- 공용 데이터(Shared Data): 여러 응용 시스템들이 공동으로 소유하고 유지하는 자료

### 특징
1. **실시간 접근성(Real-Time Accessibility)**: 수시적이고 비정형적인 질의(query)에 대해 실시간 처리에 의한 응답이 가능해야 함
2. **계속적인 변화(Continuous Evolution)**: 새로운 데이터가 삽입 삭제 갱신될 때 항상 최신의 데이터를 유지해야 함
3. **동시공유(Concurrent Sharing)**: 다수의 사용자가 동시에 같은 내용의 데이터를 이용할 수 있어야 함
4. **내용에 의한 참조(Content Regerence)**: 데이터베이스에 있는 데이터를 참조할 때, 레코드의 주소나 위치에 의해서가 아닌, 사용자가 요구하는 데이터 내용으로 데이터를 찾을 수 있어야 함

---
## 데이터베이스의 종류
![](https://velog.velcdn.com/images/dlwjd8023/post/1a0e19cc-3ee2-4a6b-a6ec-cc1a49aad586/image.png)


### 관계형 데이터베이스(SQL)
#### 특징
- 데이터를 표(Table) 형태로 저장하고, 각 테이블은 행(Row)과 열(Column)로 구성
- SQL이라는 표준 언어를 사용하며, 데이터의 일관성과 정확성이 중요할 때 사용됨
#### 예시
- MySQL
- PostgreSQL
- MariaDB
- Oracle Database
- etc
---
### 비관계형 데이터베이스(NoSQL)
#### 특징
- RDB의 엄격한 구조에서 벗어나 유연하고 확장성이 뛰어남 
- 다양한 방식으로 데이터를 저장 가능 -> 여러 유형 존재
#### 주요 유형
  - **key-value DB**: key, value 쌍으로 데이터 저장(예시: Redis)
  - **Document DB**: JSON, XML 등의 문서로 데이  터 저장(예시: MongoDB)
  - **Graph DB**: Node와 Edge를 이용하여 데이터를 표현하고 관계를 저장(예시: Amazone Neptune)
  - **Column-family DB**: Column을 기준으로 데이터를 저장(예시: Cassandra)
  - **Search engine DB**: 빠른 검색에 특화된 DB(예시: Elasticsearch)
---
## 관계형 데이터베이스의 구조
![](https://velog.velcdn.com/images/dlwjd8023/post/3887f8e2-ab7b-4f44-b1d2-d15abc038d7f/image.png)
### 대표적인 용어들
- **릴레이션(Relation)**: 데이터들을 2차원 테이블의 구조로 저장한 것
- **속성(Attribute)**: 릴레이션의 열. 개체를 구성하는 속성
- **튜플(Tuple)**: 릴레이션의 행. 속성들의 집합이며 레코드(Record)라고도 부름
- **차수(Degree)**: 릴레이션을 구성하는 속성의 수
- **카디널리티(Cardinality)**: 릴레이션에 입력된 튜플의 수
- **도메인(Domain)**: 하나의 속성이 가질 수 있는 값들의 범위
- **널(Null)**: 정보 부재를 나타내기 위해 사용되는 특수한 데이터 값
- **릴레이션 스키마(Relation Schema)**: 릴레이션의 이름과 속성 이름의 집합
- **릴레이션 인스턴스(Relation Instance)**: 릴레이션의 어느 시점까지 입력된 튜플들의 집합

### 릴레이션(Relation)
![](https://velog.velcdn.com/images/dlwjd8023/post/3887f8e2-ab7b-4f44-b1d2-d15abc038d7f/image.png)
- 릴레이션(Relation): 데이터들의 표(Table)의 형태로 표현한 것
- 구조를 나타내는 **릴레이션 스키마**와 실제 값들인 **릴레이션 인스턴스**로 구성

### 키(Key)

![](https://velog.velcdn.com/images/dlwjd8023/post/7bf503d1-3aca-4c30-9807-7d63f1487d94/image.png)

데이터베이스에서 다른 튜플들과 구별할 수 있는 기준이 되는 속성(Attribute)

### 키의 종류
- **후보키 (Candidate Key)**
  - 릴레이션을 구성하는 속성들 중 튜플을 유일하게 식별할 수 있는 속성들의 부분집합
  - 슈퍼키 중 어느 한 속성이라도 제거하면 튜플을 유일하게 식별할 수 없는 속성들의 부분집합
  - 모든 릴레이션은 반드시 하나 이상의 후보키를 가져야 함
  - 예시: <학생> 릴레이션에서의 '학번', '주민번호' 속성
- **기본키 (Primary Key)**
  - 후보키 중에서 선택한 주키(Main Key)
  - 한 릴레이션에서 특정 튜플을 유일하게 구별할 수 있는 속성
  - Null 값을 가질 수 없음
  - 동일한 값을 중복하여 저장할 수 없음
  - 예시: <학생> 릴레이션에서의 '학번'이나 '주민번호'키가 기본키가 될 수 있음
- **대체키 (Alternate Key)**
  - 후보키가 둘 이상일 때 기본키를 제외한 나머지 후보키
  - 예시: <학생> 릴레이션에서의 '학번'이 기본키가 됐을 경우,'주민번호' 속성
- **슈퍼키 (Super Key)**
  - 한 릴레이션 내에 있는 속성들의 집합으로 구성된 키
  - 예시: <학생> 릴레이션에서는 '학번', '주민번호', '학번'+'주민번호', '학번'+'주민번호'+'성명' 등으로 슈퍼키를 구성할 수 있음
  - 특징: 각 속성은 최소성을 만족시키지 못할 수 있음 (가령 '성명' 속성에서의 동명이인이 있을 경우)
- **외래키 (Foreign Key)**

  - 관계(Relation)를 맺고 있는 릴레이션 R1, R2에서 릴레이션 R1이 참조하고 있는 릴레이션 R2의 기본키와 같은 R1 릴레이션의 속성
  - 예시: <수강> 릴레이션이 <학생> 릴레이션을 참조할 때 <학생> 릴레이션의 '학번'은 기본키이고, <수강> 릴레이션의 '학번'은 외래키임
  - <수강> 릴레이션의 '학번'에는 <학생> 릴레이션의 '학번'에 없는 값은 입력할 수 없음






---
## DBMS
![](https://velog.velcdn.com/images/dlwjd8023/post/f2658636-0d9c-4124-9308-16dbc2d2aff8/image.png)

### 데이터베이스 관리 시스템(Database Management System: **DBMS**)
데이터베이스를 관리하며 응용 프로그램들이 데이터베이스를 공유하며 사용할 수 있는 환경을 제공하는 소프트웨어

### 주요 기능
- **데이터 정의**
데이터베이스의 구조를 정의하고 수정
- **데이터 조작**
데이터를 검색, 삽입, 수정, 삭제(CRUD)
- **데이터 제어**
데이터의 보안, 무결성, 복구 등을 관리


---
# SQL
---
## SQL(Structure Query Language)
관계형 데이터베이스에서 데이터를 정의, 조회, 수정, 삭제하는 다양한 작업을 수행할 수 있는 표준 언어

## 구성 요소
### - DDL (Data Definition Language): DB 구조 정의
- create: 테이블, 인덱스, 데이터베이스 등을 생성
- alter: 기존 데이터베이스 객체를 수정
- drop: 데이터베이스 객체를 삭제
### - DML (Data Manipulation Language): DB 내 데이터 조작
- select: 데이터를 조회
- insert: 데이터를 삽입
- update: 데이터를 수정
- delete: 데이터를 삭제
### - DCL (Data Control Language): DB에 대한 접근 권한 제어
- grant: 사용자에게 권한 부여
- revoke: 사용자로부터 권한 회수
### - TCL (Transaction Control Language): 트랜잭션 관리
- commit: 트랜잭션 영구 저장
- rollback: 트랜잭션 취소

---
## 기본 문법
1. **Create**
2. **Alter**
3. **Drop**
4. **Select**
5. **Insert**
6. **Update**
7. **Delete**

---
### 1. CREATE: 데이터베이스 객체 생성
새로운 데이터베이스 객체(테이블, 인덱스 등)를 생성할 때 사용

#### 1-1. 기본 구조
```sql
CREATE TABLE burgers (
	id SERIAL PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    price INT,
    gram INT,
    kcal INT,
    protein INT
);
```
---
### 2. ALTER: 테이블 구조 수정
기존 테이블의 구조를 변경할 때(컬럼 추가, 삭제, 변경) 사용

#### 2-1. 기본 구조
```sql
ALTER TABLE burgers
ADD COLUMN description TEXT;
```
---
### 3. DROP: 데이터베이스 객체 삭제
데이터베이스 객체를 완전히 제거할 때 사용

#### 3-1. 기본 구조
```sql
DROP TABLE burgers;
```
---
### 4. SELECT: 데이터 조회
테이블에서 데이터를 조회할 때 사용

#### 4-1. 기본 구조
```sql
SELECT 필드이름 FROM 테이블
```
#### 4-2. 여러 필드를 조회하는 경우
```sql
SELECT 필드이름1, 필드이름2 FROM 테이블
```
#### 4-3. 모든 필드를 조회하는 경우
```sql
SELECT * FROM 테이블
```
#### 4-4. 중복된 데이터를 없애고 조회하는 경우
```sql
SELECT DISTINCT 필드이름 FROM 테이블
```
#### 4-5. 조건식을 적용하는 경우
```sql
SELECT * 
FROM 테이블 
WHERE 필드이름 =0
```
#### 4-6. 여러 조건식을 적용하는 경우
```sql
SELECT * 
FROM 테이블 
WHERE 필드이름1 = 0
AND 필드이름2 = 0
```
#### 4-7. 정렬 기준이 여러개인 경우
```sql
SELECT 필드이름
FROM 테이블
ORDER BY 필드이름1, 필드이름2 DESC, 필드이름3 ASC
```
#### 4-8. 내부조인한 결과를 출력하는 경우
```sql
SELECT 테이블1.필드이름
FROM 테이블1, 테이블2
WHERE 테이블1.필드이름 = 테이블2.필드이름
```
#### 4-9. 별칭을 이용해 코드 간소화하는 경우(위 코드와 동일)
```sql
SELECT A.필드이름
FROM 테이블1 A, 테이블2 B
WHERE A.필드이름 = B.필드이름
```
---
### 5. INSERT: 데이터 삽입
테이블에 새 데이터를 삽입할 때 사용

#### 5-1. 기본 구조
```sql
INSERT INTO 테이블 (필드이름1, 필드이름2)
VALUES (값1, 값2)
```
#### 5-2. 예시 코드
```sql
INSERT INTO burgers (name, price, gram, kcal, protein)
VALUES ('Cheese Burger', 5000, 150, 300, 20);
```
---
### 6. UPDATE: 데이터 수정
테이블의 기존 데이터를 수정할 때 사용

#### 6-1. 기본 구조
```sql
UPDATE 테이블 SET 필드이름1 = 값1, 필드이름2 = 값2
WHERE 조건문
```
#### 6-2. 예시 코드
```sql
UPDATE burgers
SET price = 5500
WHERE name = 'Cheese Burger';
```
---
### 7. DELETE: 데이터 삭제
테이블에서 데이터를 삭제할 때 사용

#### 7-1. 기본 구조
```sql
DELETE FROM 테이블
WHERE 조건문
```

#### 7-2. 예시 코드
```sql
DELETE FROM burgers
WHERE price > 6000;
```

#### - 관계형 데이터베이스(RDBMS)는 대부분 SQL을 기반으로 하지만, 각 시스템마다 아래의 기준에 따른 구현의 차이가 존재함
- 데이터 타입
- 함수 및 연산자
- 제약 조건 및 인덱스
- 조인 및 하위 쿼리
- 특수 기능 및 확장 기능

--- 
## 트랜잭션

### 트랜잭션(Transaction)
#### 개념
- 컴퓨터 과학 분야에서의 트랜잭션
  - 더이상 분할이 불가능한 업무처리의 단위
  - 한꺼번에 수행되어야 할 일련의 연산 모음
  - 예시: 은행 송금과 입급은 동시에 수행되지 않으면 안됨 -> 계좌이체는 송금과 입금이 구성하는 하나의 트랜잭션
- **데이터베이스에서의 트랜잭션**
  - 데이터베이스에서 여러 작업을 논리적으로 묶은 하나의 단위
  
### 트랜잭션의 성질(ACID)
- **ACID**로 나타남
- **원자성(Atomicity)**: 트랜잭션의 연산은 데이터베이스에 모두 반영되거나, 전혀 반영되지 않아야 함
- **일관성(Consistency)**: 트랜잭션이 성공적으로 완료되면 일관성을 유지해야 함
- **고립성(Isolation)**: 트랜잭션 수행 시 다른 트랜잭션으로부터 영향을 받지 않아야 함 (하나의 트랙잭션 실행이 연속적이어야 함)
- **지속성(Durability)**: 성공적으로 수행된 트랜잭션은 데이터베이스에 영구적으로 반영되어야 함

### 무결성
#### 개념
- **사전적 정의**: 정보에 결점이 없도록 유지하는 성질
- **데이터 무결성**: 데이터의 정확성, 일관성, 유지성이 유지되는 것
- **정확성**: 중복이나 누락이 없는 상태
- **일관성**: 원인과 결과의 의미가 연속적으로 보장되어 변하지 않는 상태
- **유효성**: 사용자로부터 정확한 값만을 입력받는 특성

#### 데이터 무결성 제약조건
- 데이터베이스의 무결성을 보장하기 위해, 저장, 삭제, 수정 등을 제약하기 위한 조건

#### 무결성 제약조건의 종류
- **개체 무결성**: 각 릴레이션의 기본키를 구성하는 속성은 Null이나 중복된 값을 가질 수 없음
- **참조 무결성**: 외래키 값은 Null이거나 참조하는 릴레이션의 기보
- **도메인 무결성**: 속성들의 값은 정의된 도메인에 속한 값이어야 함
- **고유 무결성**: 특정 속성에 대해 고유한 값을 가지도록 조건이 주어진 경우, 릴레이션의 각 튜플이 가지는 속성 값들은 서로 달라야 함
- **Null 무결성**: 릴레이션의 특정 속성값은 Null 될 수 없음
- **키 무결성**: 각 릴레이션은 최소한 한 개 이상의 키가 존재해야함

---
# ERD
---
## 데이터 모델링
업무 내용을 분석하여 이해하고 약속된 표기법에 의해 표현하는 것
분석된 모델을 바탕으로 실제 데이터베이스를 생성 -> 보다 효율적인 데이터베이스 구성에 용이

## 데이터모델링의 절차
![](https://velog.velcdn.com/images/dlwjd8023/post/63dacbff-9dc8-446d-bb26-456410a41001/image.png)
1. 업무 파악(요구사항 수집 및 분석)
해당하는 업무에 대해 파악

2. 개념적 데이터 모델링
일과 데이터 간의 관계를 구상
각 개체들과 그들간의 관계를 발견하고 표현하기 위해 **ERD** 다이어그램을 생성

3. 논리적 데이터 모델링
개념적인 데이터 모델을 통해 구체화된 업무 중심의 데이터 모델을 생성
업무에 대한 key, 속성, 관계 등을 표시, **정규화** 등을 수행
개념적 ERD 다이어그램을 테이블형태로 재구성

4. 물리적 데이터 모델링
최종적으로 데이터를 관리할 데이터베이스를 선택하고, 선택한 데이터베이스에 실제 테이블을 생성
실제 코딩을 통해 데이터베이스를 완성


## ERD(Entity Relationship Diagram)
데이터베이스의 개체(Entity)와 개체 간의 관계(Relationship)를 시각화하요 표현한 다이어그램(Diagram)

사용 근거
- 데이터베이스의 구조를 한눈에 알아보기 쉬움
- 쿼리문 작성 시 구조화된 다이어그램을 참고할 수 있음
- 데이터의 다양한 특징 파악에 용이


### 구성 요소
개체(Entity)
- 정의 가능한 사물 또는 개념
- 유무형의 정보 모두 데이터화 가능
- 데이터베이스에서의 릴레이션에 해당

속성(Attribute)
- 개체가 갖는 속성의 의미
- 물리적 설계 단계에서 컬럼으로 변환
- 데이터베이스에서의 속성에 해당

관계(Relationship)
- 두 개 이상의 개체 사이에 존재하는 연관성
- 일대일, 일대다, 다대다 관계로 존재


---
# ERD 키와 제약 조건 표기법 (스크랩)
(출처: https://inpa.tistory.com/entry/DB-%F0%9F%93%9A-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8%EB%A7%81-1N-%EA%B4%80%EA%B3%84-%F0%9F%93%88-ERD-%EB%8B%A4%EC%9D%B4%EC%96%B4%EA%B7%B8%EB%9E%A8)

---
## 주 식별자(PK)
![](https://velog.velcdn.com/images/dlwjd8023/post/5a19047f-345b-4092-a96c-f8724e9ed64a/image.png)
![](https://velog.velcdn.com/images/dlwjd8023/post/b5ab08a1-2283-4f03-a715-accd033f3583/image.png)
- 데이터베이스 테이블의 Primary Key를 표현
- 중복이 없고 NULL 값이 없는 유일한 값에 지정하는 식별자
- ◆ (다이아몬드), 열쇠로 표현
- 주 식별자는 유일한 속성이므로 다른 속성과의 명확한 구분을 위해 구분선을 두기도 함
- 해당 속성에 들어갈 값에 Null 을 비허용한다면, N 혹은 NN을 작성

---
## 외래 식별자 (FK)
![](https://velog.velcdn.com/images/dlwjd8023/post/a2f1e053-a42e-42f3-8061-27abddda00db/image.png)
- 데이터베이스 테이블의 Foreign Key를 표현
- 외래 식별자 역시 key의 일종이기 때문에 ERD 엔티티에도 열쇠 아이콘으로 표시 (프로그램별 상이)
- 외래 식별자를 표시할 때에는 선을 이어주는데, 개체와 관계를 따져 표시

---
## ERD 엔티티 관계 표기법
각 엔티티 유형 생성 후, 엔티티 사이에 선을 이어 관계를 표현
![](https://velog.velcdn.com/images/dlwjd8023/post/96188b80-659e-4e93-b045-2ac263e7cd73/image.png)

### 식별자 관계 
![](https://velog.velcdn.com/images/dlwjd8023/post/83bbcefb-32e1-4256-9622-9661dc35c84d/image.png)
- 실선으로 표현
- 부모 자식 관계에서 자식이 부모의 주 식별자를 외래 식별자로 참조해서 자신의 주 식별자로 설정

### 비식별자 관계
![](https://velog.velcdn.com/images/dlwjd8023/post/2e89a29f-fdd8-4b33-8622-dc945ae3e3d1/image.png)
- 점선으로 표현
- 부모 자식 관계에서 자식이 부모의 주 식별자를 외래 식별자로 참조해서 일반 속성으로 사용

---
## ERD 관계의 카디널리티
관계가 존재하는 두 entity사이에 한 entity에서 다른 entity 몇개의 개체와 대응되는지 제약조건을 표기하기위해 선을 그어 표현

## 대표적인 Mapping Cardinality의 종류
![](https://velog.velcdn.com/images/dlwjd8023/post/2331b1cd-9ed6-401b-bd1e-878992d49d9c/image.png)
- **One to one** : 일대일 대응
- **One to many** : 일대다 대응
- **Many to one** : 다대일 대응
- **Many to many** : 다대다 대응
- ERD 다이어그램에 선 들을 막 그으면 가독성 저하 -> 엔티티 간 일대다 관계의 표기를 위해 ERD에서는 선의 끝 모양을 다르게 표시

---
## One-to-One Cardinality (일대일 관계)
![](https://velog.velcdn.com/images/dlwjd8023/post/b1b116b1-288f-4048-aaad-f2e876522bff/image.png)
- 학생과 신체정보는 1:1로 매칭
- 한명의 학생은 하나의 신체정보를 가짐

---
## One-to-Many Cardinality (일대다 관계)
![](https://velog.velcdn.com/images/dlwjd8023/post/c1a3b8eb-31c1-49f9-a20a-194e23fc8998/image.png)
- 한명의 학생은 여러개의 취미를 가질 수 있음

---
## Many-to-Many Cardinality (다대다 관계)
![](https://velog.velcdn.com/images/dlwjd8023/post/69738245-5b10-4c2f-af45-07885419ab1d/image.png)
- 제품 엔티티 입장에서, TV 제품은 대우 티비, 삼성 티비, 애플 티비 같은 여러 제조업체 제품이 있을 수 있음
- 제조업체 엔티티 입장에서, 한 제조업체는 여러 종류의 제품을 생산할 수 있음

---
## Many-to-Many Cardinality 관계의 해소
![](https://velog.velcdn.com/images/dlwjd8023/post/43a991da-1614-4d9a-a2f8-e4f443b1ef8b/image.png)
1. 두 엔티티가 다 대 다 관계에 있는 경우, 두개의 엔티티만으로는 서로를 완전히 표현할 수 없음
2. 데이터 모델링에서는 M:N 관계를 완성되지 않은 모델로 간주하고, 두 엔티티의 관계를 1:N, N:1 로 조정할 것을 요구
3. 두 엔티티의 관련성을 표현하기 위해 중간에 새로운 엔티티를 삽입. 이 중간 엔티티(업체별 제품)가 두 엔티티의 공유 속성 역할을 함
4. ERD 프로그램에서 M:N을 잡게 된다면 자동으로 이 과정이 실행됨

---
## ERD 관계의 참여도
![](https://velog.velcdn.com/images/dlwjd8023/post/5194857e-e1fc-4f6b-b78b-4f425b7844c5/image.png)
- 관계선 각 측의 끝자락에 기호를 표시
- '|' 표시가 있는 곳은 반드시 있어야 하는 개체 (필수)
- 'O' 표시가 있다면 없어도 되는 개체 (선택)

---
## 관계의 필수 기호 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/282a3787-98f4-4e77-9900-da7abc29ab70/image.png)

---
## 관계의 선택 기호 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/dd21674c-3ffe-4b99-8ff3-b127747f272a/image.png)

---
## ERD 연습 예제: 도서 관리 시스템
![](https://velog.velcdn.com/images/dlwjd8023/post/d43a491b-e20e-4439-888f-e5461a8478e2/image.png)

### 회원 ↔ 대여
- 회원번호가 대여 테이블에서 일반속성으로 쓰임 (점선)
- 회원은 대여를 여러개 할 수 있음 (1:N)
- 아예 대여하지 않은 회원이 있을 수 있음 (1:N(선택))
- 대여를 할 때에는 반드시 회원 정보가 필수로 존재해야한다. (1(필수):N(선택))

### 도서 ↔ 대여
- 도서번호가 대여 테이블에서 일반속성으로 쓰임 (점선)
- 과거에 여러번 대여된 도서가 있을 수 있음 (1:N)
- 대여하지 않은 도서가 있을 수 있음 (1:N(선택))
- 대여를 할 때에는 반드시 도서 정보가 존재해야 함 (1(필수):N(선택))

### 회원 ↔ 예약
- 회원번호가 예약 테이블에서 FK이자 PK로 쓰이고 있음 (실선)
- 회원은 예약을 여러개 할 수 있음 (1:N)
- 아예 예약하지 않은 회원이 있을 수 있음 (1:N(선택))
- 예약을 할 때에는 반드시 회원 정보가 필수로 존재해야 함 (1(필수):N(선택))
---
# 정규화
---
## 정규화(Nomalization)
테이블 간의 중복된 데이터를 허용하지 않는것 (데이터의 중복성 해소)

### 실행 근거
- 데이터베이스를 정규화함으로써 데이터의 무결성 유지 가능
- 데이터베이스의 저장 용량 감소

---
## 일반적인 정규화 단계
- 제1정규화
- 제2정규화
- 제3정규화
- BCNF 정규화

---
## 제1정규화
테이블의 속성이 원자값을 가지도록 테이블을 분해

### 제1정규화 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/627d7bec-303c-4e59-bdba-6c37eb3600a4/image.png)
![](https://velog.velcdn.com/images/dlwjd8023/post/a6b83618-2029-4d70-821b-2ac7d46d1e33/image.png)

---
## 제2정규화
제1정규화가 완료된 테이블에 대해, 완전 함수 종속을 만족하도록 테이블을 분해
완전함수종속: 기본키의 부분집합이 결정자가 되어서는 안된다는 것

### 제2정규화 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/c9c7445e-3b38-4623-a603-f7e9b602115d/image.png)
![](https://velog.velcdn.com/images/dlwjd8023/post/54cf800c-8e81-4df6-b58b-fd39ef6a36e9/image.png)

---
## 제3정규화
제2정규화가 완료된 테이블에 대해, 이행적 종속을 없애도록 테이블을 분해
이행적 종속: A -> B, B -> C가 성립할 때, A -> C

### 제3정규화 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/cbee332f-bea1-4875-8378-eedc3b5f13fd/image.png)
![](https://velog.velcdn.com/images/dlwjd8023/post/e6dbec2e-f2b1-4363-8446-832eb48d5583/image.png)

---
## BCNF 정규화
제3정규화가 완료된 테이블에 대해, 모든 결정자가 후보키가 되도록 테이블을 분해

### BCNF 정규화 예시
![](https://velog.velcdn.com/images/dlwjd8023/post/a0839485-ef33-4ad5-89d6-d2fe82b30211/image.png)
![](https://velog.velcdn.com/images/dlwjd8023/post/3fb5b505-e941-4e75-a6b3-8108635be0c7/image.png)

---
# ERD 설계 실습 캡쳐(주문관리)
![](https://velog.velcdn.com/images/dlwjd8023/post/bb0d5244-b092-4f08-9e2d-f65391a57e8f/image.png)

---
# MySQL Workbench 실습 캡쳐

1. 데이터베이스 생성
![](https://velog.velcdn.com/images/dlwjd8023/post/fa89c297-ec7e-44d8-8a10-c1f398242120/image.png)

2, 3. 테이블 생성 및 확인
![](https://velog.velcdn.com/images/dlwjd8023/post/467ac780-ff4b-4867-9fca-d0f937968198/image.png)

4, 5. 데이터 삽입 및 조회
![](https://velog.velcdn.com/images/dlwjd8023/post/122b6c21-285b-437c-a229-1bdfc4716c5c/image.png)

6. 데이터 수정
![](https://velog.velcdn.com/images/dlwjd8023/post/dbb68cd7-ab61-449d-aef4-8d4dbdbbdf0e/image.png)

7. 데이터 삭제
![](https://velog.velcdn.com/images/dlwjd8023/post/8206f33b-0985-4ace-9832-c5310cfae147/image.png)

8. 테이블 및 데이터베이스 삭제
![](https://velog.velcdn.com/images/dlwjd8023/post/768f5b1a-b1eb-486c-9659-1f68ea1a48fb/image.png)


