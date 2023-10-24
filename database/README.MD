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
