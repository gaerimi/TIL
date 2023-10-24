# database(데이터베이스) 학습

## Chapter 1

### 관계형 모델 소개

- 관계형 데이터베이스는 테이블(table)의 모임으로 구성
- Table
    - 고유한 이름을 가지고 있음

- Table = Relation
    - 테이블은 관계
- Column = Attribute
    - 열은 속성
- Row = Tuple
    - 행은 튜플

#### Attribute Types

- domain
    - 각 속성에 대해 허용되는 값의 집합
- 속성 값은 원자적(더 나누어질 수 없음)
    - 값이 하나 있어야 함(하나 또는 null)
- null
    - 모든 domain의 멤버
        - 모르는 값
        - 존재하지 않는 값

#### Relation Schema

- $A_1, A_2, ..., A_n$ 은 속성일 때
- $R(A_1, A_2, ..., A_n)$ 은 relation schema!
    - 예) instructor (ID,  name, dept_name, salary)

#### Keys

- Primary Key(기본키)
    - 테이블에 한 개 존재
    - 한 테이블에서 레코드를 유일하게 식별할 수 있는 속성
    - null 값을 가질 수 없음
    - 중복된 값을 가질 수 없음
    - 밑줄로 구분


- Foreign Key(외래키)
    - 다른 테이블의 기본키를 참조하는 키
    - 한 테이블에 여러 개의 외래키 존재 가능
    - 외래키에서 나타나는 값은 기본키에 있는 값이어야 함
    - 외래키에서 기본키로 향하는 화살표로 표시

## Chapter 2

### SQL Data Definition

#### Basic Types in SQL

- `char(n)`
    - 사용자가 지정한 길이가 n인 고정 길이 문자열
- `varchar(n)`
    - 사용자가 지정한 최대 길이가 n인 가변 길이 문자열
- `int`
    - 정수
- `smallint`
    - 작은 정수
- `numeric(d, p)`
    - 사용자가 지정한 전체 자릿수 p자리, 소수점 자릿수 d자리의 고정 소수점 숫자
- `real`, `double precision`
    - 부동 소수점 및 이중 정밀 부동 소수점 숫자

#### Create Table Construct

- `create table`
    - 관계를 정의할 때 사용
    - **create table** r (A1 D1, A2 D2, ..., An, Dn, (제약 조건));
        - r: 관계의 이름
        - Ai = 관계 r의 속성
        - Di = Ai의 데이터 타입(도메인)

#### Insert Statement

- `insert into` 관계 이름 `values` (튜플);
    - 속성을 테이블에 추가할 때 사용

#### Alter Table

- `alter table` 관계 이름 `add` 관계에 추가할 속성 이름&nbsp;&nbsp;&nbsp;&nbsp;추가할 속성의 도메인
    - null을 새 속성 값으로 할당한다

- `alter table` 관계 이름 `drop` 관계에서 삭제할 속성 이름
    - 속성을 삭제한다

#### Drop Table

- `drop table` 관계 이름
    - 관계에 대한 모든 튜플 및 테이블 삭제, 관계 삭제

- `delete from` 관계 이름
    - 관계의 모든 튜플 삭제, 하지만 관계는 보존

#### Integrity Constraints

- `not null`
    - 해당 특성에 null 값이 허용되지 않음

- `primary key`(속성)
    - 기본키로 선언 시 not null과 unique 보장
    - null값이 없으며 값이 중복되지 않음
    - 제약 조건으로써 선언해도 되고, 속성의 도메인 뒤에 선언해도 됨

- `foreign key`(속성...) `reference` 관계(속성...)
    - 참조하는 값이 존재해야 참조할 수 있음

#### 기본 기능

- `show databases`
    - 존재하는 데이터베이스들을 보여준다
- `use` 데이터베이스 이름
    - 데이터베이스를 선택
- `show tables`
    - 데이터베이스 내에 존재하는 테이블들을 보여준다
