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

### Basic Structure of SQL Queries

#### Relational Algebra(관계대수)

- `Selection` - $\sigma$
    - 선택 연산
    - 선택 조건을 만족하는 관계의 튜플들을 출력
    - $\sigma_{condition}(Relation)$
    - $\wedge$: and, $\vee$: or

- `Projection` - $\sqcap$
    - 추출 연산
    - 관계에서 선택된 속성들을 출력
    - $\sqcap_{attribute-list}(Relation)$

- `Natural Join` - $\Join$
    - 자연 조인
    - 같은 이름을 가지고 있는 속성들에서 두 관계가 같은 값을 가지고 있는 튜플의 쌍을 출력
    - Relation1 $\Join$ Relation2

- `Cartesion product` - $\times$
    - 카티션 곱
    - 두 관계로부터 가능한 모든 튜플의 쌍을 출력
    - Relation1 $\times$ Relation2

- `Union` - $\cup$
    - 합집합
    - 두 관계의 튜플에 대하여 합집합 수행
    - Relation $\cup$ Relation2

- `Intersection` - $\cap$
    - 교집합
    - 두 관계의 튜플에 대하여 교집합 수행
    - Relation1 $\cap$ Relation2

- `Set difference` - -
    - 차집합
    - 두 관계의 튜플에 대하여 차집합 수행
    - Relation1 - Relation2

#### Basic Query Structure

**select** A1, A2, ..., An   
**from** r1, r2, ..., rm   
**where** P   

- Ai: 속성
- ri: 관계
- P: 서술어
- SQL 쿼리의 결과는 관계!

#### The select Clause

- 쿼리 결과에서 원하는 속성 나열
- 관계대수의 추출 연산에 해당
- `distinct`
    - 쿼리 결과에서 관계의 중복 제거
    - select distinct
- `all`
    - 쿼리 결과에서 관계의 중복 허용
    - select all = select
- `*`
    - 모든 속성을 나타냄

- select 절에 +, -, *, /와 관련된 산술 식을 포함하여 튜플의 상수 또는 속성에 대해 연산 가능

#### The where Clause

- 결과가 만족해야 하는 조건 지정
- 관계대수의 선택 연산에 해당
- **and** 또는 **or** 사용 가능

#### The from Clause

- 쿼리와 관련된 관계 나열
- 관계대수의 카티션 곱 연산에 해당
- 카티션 곱은 그다지 유용하지 않지만 ,where절의 조건과 결합하면 유용

#### Join

- select ... from A, B ... where A.att = B.att

#### Natural Join

- 모든 공통 속성에 대해 동일한 값을 갖는 튜플과 일치
- 각 공통 열에 대해 하나의 복사본만 유지
- select ... from A `natural join` B

### Additional Basic Operations

#### The Rename Operation

- `as`
    - 관계 및 속성 이름 변경 가능
    - select A `as` B
    - 긴 관계 이름을 사용하기 쉽게 단축할 수 있다
    - 같은 관계에 있는 튜플을 비교해야 할 때 사용할 수 있다(self join)

#### String Operations

- `like`
    - %: 부분 문자열과 일치하는 모든 문자
        - str%: str로 시작하는 문자열
        - %str%: str이 포함되어 있는 문자열
    - _: 문자와 일치하는 문자
    - where A `like` '%str%'

#### Ordering the Display of Tuples

- `order by`
    - `order by` A
    - A에 대해 정렬
    - `desc`: 내림차순
    - `asc`: 오름차순, 기본값

#### Where Clause Predicates

- `between`
    - where A `between` 90000 and 100000
    - 90000 이상 100000 이하

### Set Operaions

- `union`, `intersect`, `except`
- 자동으로 중복을 제거한다

- `union`
    - (select ... from ... where ...) `union` (select ... from ... where ...)
    - `union all`
        - 모든 중복을 보존한다

- `intersect`
    - (select ... from ... where ...) `intersect` (select ... from ... where ...)

- `except`
    - (select ... from ... where ...) `except` (select ... from ... where ...)
