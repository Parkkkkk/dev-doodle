기출문제에 나온 것만 요약정리(전공자용???), 전체적인 내용은 [여기](http://www.dbguide.net/db.db?cmd=view&boardUid=148404&boardConfigUid=9&categoryUid=216&boardIdx=132&boardStep=1)에서 확인.


# Index 

1. 데이터 모델링의 이해 (10 문항)

    1.1 [데이터 모델링의 이해](#11-데이터-모델링의-이해)
    
    1.2 [데이터 모델과 성능](#12-데이터-모델링과-성능)

2. SQL 기본 및 활용 (40 문항)

   2.1 [SQL 기본](#21-SQL-기본)

   2.2 [SQL 활용](#22-SQL-활용)

   ~~2.3 [SQL 최적화 기본원리](#23-SQL-최적화-기본원리)~~
   > 1문제 정도 나오는 듯 100점이 목표가 아니라면 과감히 `SKIP!!`

3. [주관식 모음](#3-주관식-모음)

---

# 1. 데이터 모델링의 이해

## 1.1 데이터 모델링의 이해

---

## 엔터티(Entity)

### 엔터티의 개념
업무에 필요하고 유용한 정보를 저장하고 관리하기 위한 집합적인 것(Thing)

---

### 엔터티의 특징
- 반드시 해당 **업무에서 필요**하고 관리하고자 하는 정보이어야 한다.(예. 환자, 토익의 응시횟수, …)
- **유일한 식별자**에 의해 식별이 가능해야 한다.
- **영속적으로 존재**하는 인스턴스의 집합이어야 한다.(‘한 개’가 아니라 **‘두 개 이상’**)
- 엔터티는 **업무 프로세스**에 의해 이용되어야 한다.
- 엔터티는 **반드시 속성**이 있어야 한다.
- 엔터티는 다른 엔터티와 **최소 한 개 이상의 관계**가 있어야 한다.

----

### 엔터티의 명명
- **현업업무**에서 사용하는 용어를 사용한다.
- 약어를 사용하지 않는다.
- 단수명사를 사용한다
- 모든 엔터티에서 유일하게 이름이 부여되어야 한다. 
- 엔터티 생성의미대로 이름을 부여한다.

---

## 속성(Attribute)

### 속성의 개념
업무에서 필요로 하는 인스턴스로 관리하고자 하는 의미상 **더 이상 분리되지 않는 최소의 데이터 단위**

---

### 엔터티, 인스턴스, 속성, 속성값의 관계  (⭐️)
- 한 개의 엔터티는 **두 개 이상의 인스턴스의 집합**이어야 한다.
- 한 개의 엔터티는 **두 개 이상의 속성**을 갖는다.
- 한 개의 속성은 **한 개의 속성값**을 갖는다.

---

### 속성의 분류
- **기본속성** : 업무분석을 통해 바로 정의한 속성
- **설계속성** : 원래 업무상 존재하지는 않지만 설계를 하면서 도출해내는 속성 (코드성, 일련번호)
- **파생속성** : 다른 속성으로부터 계산이나 변형이 되어 생성되는 속성 (데이터 정합성을 위해 적게 정의하는 것이 좋다)

---

### 도메인(Domain)
- 각 속성은 **가질 수 있는 값의 범위**가 있는데 이를 그 속성의 도메인(Domain)이라 한다.
- 속성에 대한 **데이터타입**과 **크기** 그리고 **제약사항**을 지정하는 것

---

### 속성의 명명
- **해당 업무에서 사용하는 이름**을 부여한다.
- 서술식 속성명은 사용하지 않는다.
- **약어 사용(X)**은 가급적 제한한다.
- 전체 데이터 모델에서 **유일성**을 확보하는 것이 좋다.

---

## 관계(Relationship)

### 관계의 개념
엔터티의 **인스턴스 사이의 논리적인 연관성**으로서 존재의 형태로서나 행위로서 서로에게 연관성이 부여된 상태

---

### 관계의 표기법
- 관계명(Membership) : 관계의 이름
- **관계차수(Cardinality/Degree)** : 1:1, 1:M, M:N
  - ![1:N](http://www.dbguide.net/publishing/img/knowledge/SQL_043.jpg)
  - ![N:M](http://www.dbguide.net/publishing/img/knowledge/SQL_044.jpg)
- 관계선택사양(Optionality) : 필수관계(Mandatory), 선택관계(Optional)

---

### 관계의 분류
- 관계는 존재에 의환 관계와 행위에 의한 관계로 구분될 수 있으나 ERD에서는 관계를 연결할 때, 존재와 행위를 구분하지 않고 단일화된 표기법을 사용한다.
- UML(Unified Modeling Language)에는 클래스다이어그램의 관계 중 연관관계(Association)와 의존관계(Dependency)가 있고 이것은 실선과 점선의 표기법으로 다르게 표현이 된다.

---

### 관계 체크 사항
- 두 개의 엔터티 사이에 관심있는 **연관규칙**이 존재하는가?
- 두 개의 엔터티 사이에 **정보의 조합**이 발생되는가?
- 업무기술서, 장표에 **관계연결에 대한 규칙**이 서술되어 있는가?
- 업무기술서, 장표에 **관계연결을 가능하게 하는 동사(Verb)**가 있는가?

---

## 식별자(Identifiers)

### 식별자의 개념
하나의 엔터티에 구성되어 있는 여러 개의 속성 중에 엔터티를 대표할 수 있는 속성

---

### 주식별자의 특징 (⭐️)
- **유일성** : 주식별자에 의해 엔터티내에 **모든 인스턴스들이 유일하게 구분**되어야 한다.
- **최소성** : 주식별자를 구성하는 속성의 수는 **유일성을 만족하는 최소의 수**가 되어야 한다.
- **불변성** : 지정된 주식별자의 값은 자주 변하지 않는 것이어야 한다.
- **존재성** : 주식별자가 지정이 되면 **반드시 값**이 들어와야 한다.

---

### 식별자의 종류
![](http://www.dbguide.net/publishing/img/knowledge/SQL_051.jpg)  

- 엔터티 내에서 대표성을 가지는가에 따라 주식별자와, 보조식별자로 구분
- 엔터티 내에서 스스로 생성되었는지 여부에따라 내부식별자와 외부식별자로 구분
- 단일 속성으로 식별이 되는가에 따라 단일식별자와 복합식별자로 구분
- 원래 업무적으로 의미가 있던 식별자 속성을 대체하여 일련번호와 같이 새롭게 만든 식별자를 구분하기 위해 본질식별자와 인조식별자로 구분

---

### 주식별자 도출 기준
- 해당 업무에서 자주 이용되는 속성을 주식별자로 지정하도록 함
- 명칭, 내역 등과 같은 이름으로 기술되는 것은 피함
- 속성의 수가 많아지지 않도록 함

---

### 식별자/비식별자 관계 (⭐️)  
![](http://www.dbguide.net/publishing/img/knowledge/SQL_070.jpg)  

부모엔터티로부터 받은 외부식별자(FK)를 자신의 주식별자로 이용할 것인지 또는 부모와 연결이 되는 속성으로서만 이용할 것인지를 결정해야 한다.

- **식별자 관계** : 부모로부터 받은 식별자를 자식엔터티의 주식별자로 이용하는 경우는 Null값이 오면 안되므로 반드시 부모엔터티가 생성되어야 자기 자신의 엔터티가 생성되는 경우
- **비식별자 관계** : 부모엔터티로부터 속성을 받았지만 자식엔터티의 주식별자로 사용하지 않고 일반적인 속성으로만 사용하는 경우


  - **자식엔터티에서 받은 속성이 반드시 필수가 아니어도 무방하기 때문에 부모 없는 자식이 생성될 수 있는 경우이다.**
  - **엔터티별로 데이터의 생명주기(Life Cycle)를 다르게 관리할 경우이다. 예를 들어 부모엔터티에 인스턴스가 자식의 엔터티와 관계를 가지고 있었지만 자식만 남겨두고 먼저 소멸될 수 있는 경우가 이에 해당된다. 이에 대한 방안으로 물리데이터베이스 생성 시 Foreign Key를 연결하지 않는 임시적인 방법을 사용하기도 하지만 데이터 모델상에서 관계를 비식별자관계로 조정하는 것이 가장 좋은 방법이다.**
  -  **여러 개의 엔터티가 하나의 엔터티로 통합되어 표현되었는데 각각의 엔터티가 별도의 관계를 가질 때**
  -  **자식엔터티에 주식별자로 사용하여도 되지만 자식엔터티에서 별도의 주식별자를 생성하는 것이 더 유리하다고 판단될 때 비식별자 관계에 의한 외부식별자로 표현한다.**

## 1.2 데이터 모델링과 성능

# 2. SQL 기본 및 활용

## 2.1 SQL 기본

---

- SQL 문장들의 종류 (⭐ 이 명령어가 어떤 종류냐 묻는 문제가  많음 - 안 나오면 섭함)   

  ![](http://www.dbguide.net/publishing/img/knowledge/SQL_148.jpg)  


> DDL AUTOCOMMIT: (ORACLE) 자동 커밋 수행 / (SQL Server) 자동 커밋 수행 안함. - 53p.29

---

- 제약조건의 종류


  ![](http://www.dbguide.net/publishing/img/knowledge/SQL_166.jpg)  

> UNIQUE KEY의 경우 NULL 입력 가능(⭐️) - 44p.10, 47p.15

---

### DDL

- **ALTER TABLE**  (✓ 주관식이 출제될 수도 있음 쿼리문(**키워드**) 외우기)
  - **ADD COLUMN** : `ALTER TABLE 테이블명 ADD 추가할 칼럼명 데이터 유형;`
  - **DROP COLUMN** : `ALTER TABLE 테이블명 DROP COLUMN 삭제할 칼럼명;`
  - **MODIFY COLUMN** :  (ORACLE) MODIFY / (SQL Server) ALTER 차이
    - ORACLE : `ALTER TABLE 테이블명 MODIFY (칼럼명1 데이터 유형 [DEFAULT 식] [NOT NULL], 칼럼명2 데이터 유형 …);`
    - SQL Server : `ALTER TABLE 테이블명 ALTER (칼럼명1 데이터 유형 [DEFAULT 식] [NOT NULL], 칼럼명2 데이터 유형 …);`
    
  - **DROP CONSTRAINT** : `ALTER TABLE 테이블명 DROP CONSTRAINT 제약조건명;`
  - **ADD CONSTRAINT** :  `ALTER TABLE 테이블명 ADD CONSTRAINT 제약조건명 제약조건 (칼럼명);`
  
- **RENAME TABLE** : `RENAME 변경전 테이블명 TO 변경후 테이블명;`

--- 

### 테이블/컬럼 명명규칙
  - 반드시 문자로 시작
  - A-Z, a-z, 0-9, _, $, # 만 허옹햠.

---

### DROP TABLE, TRUNCATE TABLE, DELETE FROM TABLE 차이 (⭐️) - 51p.23, 51p.25, 52p.26

DROP | TRUNCATE | DELETE
:-- | :-- | :--
DDL | DDL(일부 DML의 성격을 가짐) | DML
ROLLBACK 불가능 |  ROLLBACK 불가능 | COMMIT 이전 ROLLBACK 가능
AUTO COMMIT | AUTO COMMIT | 사용자 COMMIT
테이블이 사용했던 Storage를 모두 Release | 테이블이 사용했던 Storage 중 최초 테이블 생성시 할당된 Storage만 남기고 모두 Release | 데이터를 모두 Delete 해도 사용했던 Storage는 Release 되지 않음
로그 안 남김 | 로그 안 남김 | 로그 남김
---

### 제약조건의 종류 (4지선다)

  ![](http://www.dbguide.net/publishing/img/knowledge/SQL_170.jpg)  

---

### 참조 무결성 규정 (* 위주로 보세요)

`DELETE/MODIFY` Action | Cascade / Set Null / Set Default / Restrict (부서<-사원)
:-- | :--
***Casecase** | **Master 삭제 시 Child 같이 삭제**
Set Null | Master 삭제 시 Child 해당 필드 Null
Set Default | Master 삭제 시 Child 해당 필드 Default 값으로 설정
***Restrict** | **Child 테이블에 PK 값이 없는 경우만 Master 삭제 허용**
No Action | 참조무결성을 위반하는 삭제/수정 액션을 취하지 않음

---

`INSERT` Action | Automatic / Set Null / Set Default / Dependent (부서->사원)
:-- | :--
***Automatic** | **Master 테이블에 PK가 없는 경우 Master PK를 생성 후 Child 입력**
Set Null | Master 테이블에 PK가 없는 경우 Child 외부키를 Null 값으로 처리
Set Default | Master 테이블에 PK가 없는 경우 Child 외부키를 지정된 기본값으로 입력
***Dependent** | **Master 테이블에 PK가 존재할 때만 Child 입력 허용**
No Action | 참조무결성을 위반하는 삭제/수정 액션을 취하지 않음


---

### 연산자의 종류

![](http://www.dbguide.net/publishing/img/knowledge/SQL_172.jpg)

---

### NULL (⭐️)

- NULL
  - 모르는 값을 의미
  - 값의 부재를 의미
  - NULL과의 모든 비교(**IS NULL** 제외)는 알 수 없음을 반환한다.

---

###  NULL값과의 연산

연산 | 리턴값
:-- | :--
사칙연산 등(+, -, *, /) | NULL
비교연산(=, >, >=, <, <=) | FALSE

> SELECT NULL + 1 FROM DUEL; SELECT * FROM DUAL WHERE COLUMN > NULL;

---

###  `INSERT INTO 컬럼 VALUES (''); 공백에 대한 처리 - 56p.37`

ORACLE | SQL Server
:-- | :--
NULL 로 입력됨 | '' 공백으로 입력됨

---

### NULL 관련 함수(주관식도 있고 문제도 많음;;) - 62p.44, 63p.45, 63p.46, 63p.47, 63p.48, 64p.49, 64p.50
![](http://www.dbguide.net/publishing/img/knowledge/SQL_192.jpg)

---

### SELECT 문장 실행 순서 - 72p.59

`FROM - WHERE  - GROUP BY - HAVING - SELECT - ORDER BY`

---

ORACLE | SQL Server
:-- | :--
NULL값을 가장 큰 값으로 간주(오름차순시 가장 마지막)  | NULL 값을 가장 작은값으로 간주 (오름차순시 가장 위)

### 집계함수 (NULL을 포함하는지 제외하는지에 집중)

![](http://www.dbguide.net/publishing/img/knowledge/SQL_193.jpg)
> COUNT(*), COUNT(표현식)의 차이를 알기 - 65p.50-51

COUNT(*) | COUNT(표현식)
:-- | :--
NULL 값을 **포함**한 행의 수 출력 | NULL값을 **제외**한 행의 수 출력

---

## 2.2 SQL 활용

---

### 순수 관계 연산자 (에 뭐가있는지 4지선다) - p78.65
![](http://www.dbguide.net/publishing/img/knowledge/SQL_201.jpg)

연산자 | 설명
:-- | :--
SELECT | SELECT 연산은 WHERE 절로 구현
PROJECT | PROJECT 연산은 SELECT 절로 구현
(NATURAL) JOIN | 연산은 다양한 JOIN 기능으로 구현
DIVIDE | DIVIDE 연산은 현재 사용되지 않음

---

### ANSI/ISO SQL 에서 표시하는 FROM 절 JOIN 형태

JOIN 형태 | 설명
:-- | :--
INNER JOIN | OUTER(외부) JOIN과 대비하여 내부 JOIN이라고 하며 JOIN 조건에서 동일한 값이 있는 행만 반환, `USING | ON 필수`
NATURAL JOIN (ORACLE만 지원) | 두 테이블 간의 동일한 이름을 갖는 모든 칼럼들에 대해 EQUI(=) JOIN을 수행 `USING | ON | WHERE 절 조건을 정의 할 수 없음`, `ALIAS나 테이블이름 같은 접두사 불일 수 없음 (DEPT.DEPTNO → DEPTNO)`
USING 조건절 (ORACLE만 지원) | FROM 절의 USING 조건절을 이용하면 같은 이름을 가진 칼럼들 중에서 원하는 칼럼에 대해서만 선택적으로 EQUI JOIN을 할 수가 있다.  `ALIAS나 테이블이름 같은 접두사 불일 수 없음 (DEPT.DEPTNO → DEPTNO)`
ON 조건절 | `ALIAS나 테이블이름 같은 접두사를 지정해야 함 (DEPTNO → DEPT.DEPTNO)`
CROSS JOIN | 집합 연산자의 PRODUCT의 개념으로 테이블 간 JOIN 조건이 없는 경우 생길 수 있는 모든 데이터의 조합을 말 함. `양쪽 집합의 M*N 건의 데이터 조합`
OUTER JOIN (LEFT, RIGHT, FULL) | JOIN 조건에서 동일한 값이 없는 행도 반환할 때 사용

> FULL OUTER JOIN : RIGHT OUTER JOIN과 LEFT OUTER JOIN의 결과를 합집합으로 처리한 결과와 동일하다.

![](http://www.dbguide.net/publishing/img/knowledge/SQL_203.jpg)


### ORACLE 에서의 OUTER JOIN - 89p.79
예시 | JOIN
A.ID = B.ID (+) | LEFT OUTER JOIN
A.ID (+) = B.ID  | RIGHT OUTER JOIN

> (+) 오른쪽에 있으면 LEFT / 왼쪽에 있으면 RIGHT

---

### 집합연산자

![](http://www.dbguide.net/publishing/img/knowledge/SQL_204.jpg)

집합연산자 | 설명
:-- | :--
UNION | 중복행은 하나로
UNION ALL | 중복행 `그대로`
INTERSECT | 교집합, 중복행은 하나로
EXCEPT/MINUS | 차집합, 중복행 하나로

--- 

### 일반 집합연산자 SQL 과 비교 - 93p.85
일반 집합연산자 | SQL
:-- | :--
UNION | UNION
INTERSECTION | INTERSECT 
DIFFERENCE | EXCEPT/MINUS
PRODUCT | CROSS JOIN

---

### (⭐️) 계층형 질의와 SELF JOIN (✓ 이 부분은 내용이 생소해서 가서 보세요 >>> [링크](http://www.dbguide.net/db.db?cmd=view&boardUid=148202&boardConfigUid=9&categoryUid=216&boardIdx=135&boardStep=1)<<<)

계층형 데이터 - 동일 테이블에 계층적으로 상위와 하위 데이터가 포함

![](http://www.dbguide.net/publishing/img/knowledge/SQL_207.jpg)

절 | 설명
:-- | :--
START WITH | 계층 구조 전개의 시작 위치를 지정하는 구문
CONNECT BY | 다음에 전개될 자식 데이터를 지정하는 구문, 자식 데이터는 CONNECT BY절에 주어진 조건을 만족해야 한다.(조인)
PRIOR | CONNECT BY절에 사용되며, 현재 읽은 칼럼을 지정한다.
ORDER SIBLINGS BY | 형제 노드(동일 LEVEL) 사이에서 정렬을 수행


`PRIOR 자식 = 부모(순방향)` 전개  

![](http://www.dbguide.net/publishing/img/knowledge/SQL_209.jpg)

`PRIOR 부모 = 자식(역방향)` 전개  

![](http://www.dbguide.net/publishing/img/knowledge/SQL_210.jpg)

---

### SELF JOIN - 98p.92
- 동일 테이블 사이의 조인
- FROM 절에 동일 테이블이 `두 번 이상` 나타난다
- 조인을 수행하면 테이블과 칼럼 이름이 모두 동일하기 때문에 식별을 위해 반드시 테이블 `별칭(Alias)를 사용`해야 한다.

---

### SUB QUERY
![](http://www.dbguide.net/publishing/img/knowledge/SQL_216.jpg)

> 다중 컬럼 서브쿼리: SQL Server에서 지원 안 됨.

---

### 서브쿼리 사용시 주의 사항
1. 서브쿼리를 괄호로 감싸서 사용한다.
2. 서브쿼리는 단일행(Single Row) 또는 복수행(Multiple Row) 비교 연산자와 함께 사용 가능하다.
3. 연산자는 서브쿼리의 결과가 반드시 1건 이하이어야 하고 복수행 비교 연산자는 서브쿼리의 결과 건수와 상관 없다.

### 그 밖의 위치에서 사용되는 서브쿼리

절 | 설명
:-- | :--
SELECT 절 | 스칼라 서브쿼리(Scalar Subquery), 단일 행 서브쿼리이기 때문에 결과가 2건 이상 반환되면 SQL문은 오류를 반환한다.
FROM 절 | 인라인 뷰 (Inline View) 또는 동적 뷰 (Dynamic View)
HAVING 절 | 그룹함수와 함께 사용될 때 그뤂핑된 결과에 대해 부가적인 조건을 주기 위해서 사용
UPDATE 문의 SET 절에서 사용하기 | 서브쿼리를 사용한 변경 작업을 할 때 서브쿼리의 결과가 NULL을 반환할 경우 해당 컬럼의 결과가 NULL이 될 수 있기 때문에 주의해야 한다.
INSERT문의 VALUES절 | 


---

### 뷰 (VIEW) - 4지선다

![](http://www.dbguide.net/publishing/img/knowledge/SQL_221.jpg)

- 테이블 구조가 변경되어도 뷰를 사용하는 응용 프로그램은 변경하지 않아도 된다.
- 뷰는 보안을 강화하기 위한 목적으로도 활용할 수 있다.
- 실제 데이터를 저장하고 있는 뷰를 생성하는 기능을 지원하는 DBMS도 있다.
- 뷰는 단지 정의만을 가지고 있으며, 실행 시점에 질의를 재작성하여 수행한다.


### 그룹함수 [예제 링크](https://docs.google.com/presentation/d/1JARYE3P8ebqTj3z4N0uiw4ZFiEKJjM_KBYJOzlWJ20I/edit#slide=id.g45998aabfd_0_9) - 예제를 봐야 이해가 돼요!

### ROLLUP

- ROLLUP에 지정된 Grouping Columns의 List는 `Subtotal` 생성하기 위해 사용됨
- Grouping Columns : Subtotal → N : N+1개 (일부 사용 제외)
- ROLLUP의 인수는 계층 구조이므로 인수 순서가 바뀌면 수행 결과도 바뀌게 됨

### GROUPING
 
- ROLLUP이나 CUBE에 의한 소계가 계산된 결과에는 GROUPING(EXPR)=1, 나머지는 0

### CUBE

- 결합 가능한 모든 값에 대하여 다차원 집계 생성
- CUBE를 사용할 경우에는 내부적으로는 Grouping Columns의 순서를 바꾸어서 또 한 번의 Query를 추가 수행해야 함
- Grand Total은 양쪽의 Query 에서 모두 생성이 되므로 한 번의 Query에서는 제거되어야만 함 → ROLLUP에 비해 시스템의 연산 대상이 많음
- Grouping Columns이 가질 수 있는 모든 경우에 대하여 Subtotal을 생성해야 하는 경우에는 CUBE를 사용하는 것이 바람직하나, ROLLUP에 비해 `시스템에 많은 부담`
- CUBE 함수의 경우 표시된 인수들에 대한 계층별 집계를 구할 수 있으며, 이때 표시된 인수들 간에는 계층 구조인 ROLLUP과는 달리 평등한 관계이므로 인수의 순서가 바뀌는 경우 행간에 정렬 순서는 바뀔 수 있어도 데이터 결과는 같음
- Grouping Columns : Subtotal → N : 2의 N제곱 개

### GROUPING SETS
- GROUP BY SQL 문장을 여러 번 반복하지 않아도 다양한 소계 집합 생성 가능
- GROUPING SETS에 표시된 인수들에 대한 개별 집계를 구할 수 있으며, 이때 표시된 인수들 간에는 계층 구조인 ROLLUP과는 달리 - 평등한 관계 → 인수의 순서가 바뀌어도 결과는 같음

### 윈도우 함수 - 116p.112
- Partition과 Group By 구문은 의미적으로 유사하다.
- Partition 구문이 없으면 전체 집합을 하나의 Partition으로 정의한다.
- 윈도우 함수는 결과에 대한 함수처리이기 때문에 결과 건수가 줄지 않는다.
- 윈도우 함수 적용 범위는 Partition을 넘을 수 없다.

### 그룹 내 순위함수 비교 (⭐️)
함수 | 설명
:-- | :--
RANK | 동일한 값에 대해서는 동일한 순위를 부여
DENSE_RANK | 동일한 값에 대해서는 동일한 순위를 부여하나, `동일한 순위를 하나의 건수로 취급`
ROW_NUMBER | 동일한 값이라도 고유한 순위를 부여

### DCL (Data Control Language)
DBMS에서 생성된 USER와 다양한 권한들 사이에서 중개 역할을 할 수 있도록 DBMS에서는 `ROLE`을 제공한다. 이러한 ROLE을 DBMS USER에게 부여하기 위해서는 `GRANT` 명령을 사용하며, ROLE을 회수하기 위해서는 `REVOKE` 명령을 사용환다.

### PL/SQL
![](http://www.dbguide.net/publishing/img/knowledge/SQL_231.jpg)
> 블록 전체는 하나의 트랜잭션으로 묶여 있지 `않음!`

# 저장 모듈 3가지

모듈 | 설명
:-- | :--
PROCEDURE | 
USER DEFINE FUNCTION | Procedure처럼 절차형 SQL을 로직과 함께 데이터베이스 내에 저장해 놓은 명령문의 집합을 의미한다. `(차이점:return값 있음)`
TRIGGER | 특정한 테이블에 INSERT, UPDATE, DELETE와 같은 DML문이 수행되었을 때, 데이터베이스에서 자동으로 동작하도록 작성된 프로그램이다.


![](http://www.dbguide.net/publishing/img/knowledge/SQL_238.jpg)

~~## 2.3 SQL 최적화 기본원리~~ 몇 개 안 나오니 포기

# 3. 주관식 모음

**문제 1.** 업무에서 필요로 하는 인스턴스에서 관리하고자 하는 의미상 더 이상 분리되지 않는 데이터의 단위를 무엇이라 하는가?

**답**: 속성(Attribute)

---

**문제 2.** 아래 설명을 읽고 다음 (ㄱ)에 들어갈 단어를 작성하시오.

```
첫번째, 데이터모델링을 할 때 정규화를 정확하게 수행한다.
두번째, 데이터베이스 용량산정을 수행한다.
세번째, 데이터베이스에 발생되는 트랜잭션의 유형을 파악한다.
네번째, 용량과 트랜잭션의 유형에 따라 (ㄱ)를 수행한다.
다섯번째, 이력모델의 조정, PK/FK조정, 슈퍼타입/서브타입 조정 등을 수행한다.
```

**답**: 반정규화

> ✓ 이 문제는 객관식으로 순서를 묻는 문제로도 나왔습니다.

**데이터 모델링의 순서**

1. 데이터모델링을 할 때 정규화를 정확하게 수행한다.
2. 데이터베이스 용량산정을 수행한다.
3. 데이터베이스에 발생되는 트랜잭션의 유형을 파악한다.
4. 용량과 트랜잭션의 유형에 따라 반정규화를 수행한다.
5. 이력모델의 조정, PK/FK조정, 슈퍼타입/서브타입 조정 등을 수행한다.
6. 성능관점에서 데이터 모델을 검증한다.

---

**문제 3.** 아래 설명에서 데이터 액세스 성능을 향상시키기 위해 적용하는 방법에 대해서 (ㄱ)을 채우시오.

```
하나의 테이블에 많은 양의 데이터가 저장되면 인덱스를 추가하고 테이블을 몇 개로 쪼개도 성능이 저하되는 경우가 있다. 이때 논리적으로는 하나의 테이블이지만 물리적으로는 여러 개의 테이블로 분리하여 데이터 액세스 성능도 향상시키고, 데이터 관리방법도 개선할 수 있도록 테이블에 적용하는 기법을 (ㄱ) 이라고 한다.
```

**답**: 파티셔닝(partitioning)

파티셔닝(대량데이터에 따른 분할) 관련 시험에 나올만한 다른 키워드

이름 | 설명
:-- | :--
로우체이닝(Row Chaining) | 로우 길이가 너무 길어서 데이터 블록 하나에 데이터가 모두 저장되지 않고 `두 개 이상의 블록에 걸쳐 하나의 로우가 저장`되어 있는 형태
로우 마이그레이션(Row Migration) | 데이터 블록에서 수정이 발생하면 수정된 데이터를 해당 데이터 블록에서 저장하지 못하고 `다른 블록의 빈 공간을 찾아 저장`하는 방식

---

**문제 4.** 아래 내용에 해당하는 SQL 명령어의 종류를 작성하시오.

```
논리적인 작업의 단위를 묶어 DML에 의해 조작된 결과를 작업단위(Transaction) 별로 제어하는 명령어인 Commit, Rollback, Savepoint 등이 여기에 해당하며, 일부에서는 DCL(Data Control Language)로 분류 하기도 한다.
```

**답**: TCL

> ✓ TRANSACTION, COMMIT, ROLLBACK 도 주관식 한 문제의 답으로 출제 되었습니다.
> ✓ SQL 문장들의 종류는 객관식으로 많이 출제 되었습니다. [SQL 문장들의 종류 보기](#21-SQL-기본)

---

**문제 5.** STADIUM 테이블의 이름을 STADIUM_JSC로 변경하는 SQL을 작성하시오. (ANSI 표준 기준)

**답**: RENAME TABLE STATIUM TO STADIUM_JSC

> ✓ DDL SQL [DDL 보기](#DDL)

---

**문제 6.** 아래 내용의 (ㄱ), (ㄴ), (ㄷ)에 해당하는 단어를 순서대로 작성하시오.

```
(ㄱ) 은 데이터베이스의 논리적 연산단위로서 밀접히 관련되어 분리될 수 없는 한 개 이상의 데이터 베이스 조작을 가리킨다.
(ㄱ) 의 종료를 위한 대표적 명령어로서는 데이터에 대한 변경사항을 데이터베이스에 영구적으로 반영하는 (ㄴ) 과 데이터에 대한 변경사항을 모두 폐기하고 변경전의 상태로 되돌리는 (ㄷ)이 있다.
```

**답**: TRANSACTION, COMMIT, ROLLBACK

---

**문제 7.** 아래의 (ㄱ)에 들어갈 내용을 적으시오.
SQL을 사용하여 데이터베이스에서 데이터를 조회할 때 원하는 데이터만을 검색하기 위해서 SELECT, FROM 절과 함께 (ㄱ) 을(를) 이용하여 조회되는 데이터의 조건을 설정하여 데이터를 제한할 수 있다.

**답**: WHERE

---

**문제 8.** 사원 테이블에서 MGR의 값이 7698과 같으면 NULL을 표시하고, 같지 않으면 MGR을 표시 하려고 한다. 아래의 SQL 문장의 (ㄱ) 안에 들어갈 함수명을 작성하시오.

```
SELECT ENAME, EMPNO, MGR, (ㄱ) (MGR, 7698) as NM FROM EMP;
```

**답**: NULL IF

**단일 행 NULL 관련 함수의 종류**
일반형 함수 | 함수 설명
:-- | :--
NVL(표현식1, 표현식2) - Oracle ISNULL(표현식1, 표현식2) - SQL Server | 표현식1의 결과값이 NULL이면 표현식2의 값을 출력한다. 단 표현식1과 표현식2의 결과 데이터 타입이 같아야 한다. NULL 관련 가장 많이 사용되는 함수이므로 상당히 중요하다.
NULLIF(표현식1, 표현식2) | 표현식1이 표현식2와 같으면 NULL을, 같지 않으면 표현식1을 리턴한다.
COALESCE(표현식1, 표현식2, ...) 코알레스씨이 ;; | 임의의 개수 표현식에서 NULL이 아닌 최초의 표현식을 나타낸다. 모든 표현식이 NULL이라면 NULL을 리턴한다.

---

**문제 9.** 아래의 사례1은 CATESIAN PRODUCT를 만들기 위한 SQL문장이며 사례 1과 같은 결과를 얻기 위해 사례 2 SQL 문장의 (ㄱ) 안에 들어갈 내용을 작성하시오.

```
[사례1]
SELECT ENAME, DNAME
FROM EMP, DEPT
ORDER BY ENAME;

[사례2]
SELECT ENAME, DNAME
FROM EMP (ㄱ) DEPT
ORDER BY ENAME;
```

**답**: CROSS JOIN

---

**문제 10.** 신규 부서의 경우 일시적으로 사원이 없는 경우도 있다고 가정하고 DEPT와 EMP를 조인하되 사원이 없는 부서 정보도 같이 출력하도록할 때, 아래 SQL 문장의 (ㄱ) 안에 들어갈 내용을 기술하시오.

```
SELECT E.ENAME, D.DEPTNO, D.DNAME
FROM DEPT D (ㄱ) EMP E
ON D.DEPTNO = E.DEPTNO;
```
**답**: LEFT JOIN / LEFT OUTER JOIN

JOIN 형태 | 설명
:-- | :--
INNER JOIN | OUTER(외부) JOIN과 대비하여 내부 JOIN이라고 하며 JOIN 조건에서 동일한 값이 있는 행만 반환, `USING | ON 필수`
NATURAL JOIN (ORACLE만 지원) | 두 테이블 간의 동일한 이름을 갖는 모든 칼럼들에 대해 EQUI(=) JOIN을 수행 `USING | ON | WHERE 절 조건을 정의 할 수 없음`, `ALIAS나 테이블이름 같은 접두사 불일 수 없음 (DEPT.DEPTNO → DEPTNO)`
USING 조건절 (ORACLE만 지원) | FROM 절의 USING 조건절을 이용하면 같은 이름을 가진 칼럼들 중에서 원하는 칼럼에 대해서만 선택적으로 EQUI JOIN을 할 수가 있다.  `ALIAS나 테이블이름 같은 접두사 불일 수 없음 (DEPT.DEPTNO → DEPTNO)`
ON 조건절 | `ALIAS나 테이블이름 같은 접두사를 지정해야 함 (DEPTNO → DEPT.DEPTNO)`
CROSS JOIN | 집합 연산자의 PRODUCT의 개념으로 테이블 간 JOIN 조건이 없는 경우 생길 수 있는 모든 데이터의 조합을 말 함. `양쪽 집합의 M*N 건의 데이터 조합`
OUTER JOIN (LEFT, RIGHT, FULL) | JOIN 조건에서 동일한 값이 없는 행도 반환할 때 사용

---
