## Database Applications

* DB 시스템의 특성
  * 최초 적재(Loading) > 이벤트 발생에 따른 잦은 변경(Interaction)
  * 대용량의 데이터를 다룸
    * 사용자들이 원하는 순간 데이터에 접근하기 위해서는 대용량의 데이터가 체계적으로 조직화되어 있어야 함



## Database System

* Database : 데이터 및 데이터 간 관계의 집합

    

* DBMS(Database Management Systems) : 사용자가 Database에 접근할 수 있도록 지원해주는 프로그램의 집합(DBMS의 경우에는 매우 많은 모듈이 필요하고 이들의 집합이라는 의미)

    

* 사용자가 쿼리를 보내면 DBMS software가 Database 구조를 파악하고 원하는 data를 사용자에게 전달
  * DBMS software : ORACLE, MS-SQL, MS-ACCESS



## Schemas versus Instances

* **데이터베이스 스키마(schema)**
  * 데이터베이스 구조, 데이터 타입, 그리고 계약조건에 대한 명세
  
  * 데이터베이스 설계 단계에서 명시되며, 자주 변경되지 않음
  
      
  
* 데이터베이스 인스턴스(Instance)
  * 특정 시점에 데이터베이스에 실제로 저장되어 있는 데이터
  
  * Database instance = Occurrence = Snapshot
  
      
  
* DB desigin = Data modeling



## SQL(Structured Query Language)

* DML / DDL

  * 데이터 정의어 (DDL : Data Defination Language)
    * 스키마를 기술하기 위해 사용, 주로 DB 설계자가 사용
    
  * 데이터 조작어 (DML : Data Manipulation Language)
    * 데이터의 조회(Retrieval), 삽입(Insertion), 삭제(Deletion), 갱신(Update)에 사용됨
    
  * DCL (Data Control Language), TCL(Transaction Control Language)

      

* 독립 실행형 / 내장형

  * 독립 실행형

    * SQL 인터페이스를 이용하여 SQL 쿼리를 직접 DBMS에 입력

  * 내장형

    * C, C++, Java 등의 프로그래밍 언어에 내장됨

    * Host language + Data sublanguage로 구성됨

        

## Overview of Database Design Process

* 요구사항 분석
  * 업무 기술서(업무에 대해 자세히 설명)
  
      
  
* 개념적 설계(Conceptual Design)
  * 업무에 대해서 도식화
  
  * Entity-Relationship Model(개체 관계 모형, ERM)
  
  * ERM에 대한 결과(Entity-Relationship Diagram, ERD)
  
      
  
* 논리적 설계(Logical Design)
  * 테이블 형태로 만들어진 모델
  
  * Relational Model(관계형 모델)
  
      
  
* 물리적 설계(Physical Design)
  * 관계형 모델을 실제로 구현하는 것
  
      
  
* Relationship : 관계, Relational: 테이블

  

## ER Model Concepts

* 개체(Entity)
  * 실세계에 존재하는 의미있는 하나의 정보 단위
  
  * 물리적 객체 뿐 아니라 개념적 객체도 포함
    * (학생, 자동차, 강의실, ...) / (프로젝트, 직업, 교과목, ...)
    
        
  
* 관계(Relationship)
  * 개체들 사이의 연관성
    * [학생 : 네모]과 [교과목 : 네모] 사이의 [수강 : 마름모] 관계
    
        
  
* 속성(Attribute)
  * 개체 또는 관계의 본질적 성질
  * [학생 : 네모]의 [학번 : 동그라미], [혈액형 : 동그라미]
  * Instance는 속성의 집합
  * Types of Attributes
    * Single-valued vs Multivalued
      * 나이 vs 취미
    * Simple vs Composite
      * Simple Attribute : 더 이상 쪼개지지 않는 원자값을 갖는 속성(나이, 학번 등)
      * Composite Attribute : 몇 개의 요소로 분해될 수 있는 속성(주소 > 시, 군, 구, 번지 등)
    * Stored vs Derived
      * Derived Attribute : 저장된 다른 데이터로부터 유도 가능한 속성(각 과목의 성적 > 총점, 주민등록번호 > 나이), Number of 로 표현 가능한 것
      * Stored의 경우에는 유도 가능하더라도 저장하는 것을 의미



## Entity Types and Key Attributes

* 키 속성(Key Attributes)
  * 어떤 개체에 대해서 항상 유일한 값을 갖는 속성 (또는 속성들의 집합)
    * 학생의 학번, 책의 ISBN, 자동차의 차량 번호...
    
  * 특정 Snapshot이 아닌, 해당 개체의 모든 가능한 Snapshot의 집합을 고려하여 파악 되어야 함
  
  * 복합 키(Composite Key)
    * Composite Attribute가 키 속성이 되는 경우
    * 복합 키는 최소성을 가져야 함
      * (팀명, 등번호) vs (팀명, 등번호. 선수명)
    
  * 각 개체는 하나 이상의 키를 가질 수 있음
  
  * 어떤 개체는 키를 갖지 않을 수도 있음
    * 약성 개체(Weak Entity)
    
        

:heavy_check_mark: Entity를 찾고 Entity의 속성을 찾은 뒤 각각의 관계를 파악하여 ERD를 생성한다.

  

* 관계(Relationship) 설정

  * 한 개체의 속성이 다른 개체를 참조할 때 관계가 형성됨

  * [직원]의 [프로젝트] 속성이 [프로젝트] 개체를 참조

  * [부서]의 [관리자] 속성은 [직원] 개체를 참조

      

* 관계의 차수(Degree)

  * 관계에 참여하는 개체의 수

  * Binary, Ternary, Unary

      

* 관계의 대응수(Cardinality)

  * 해당 개체가 해당 관계에서 참여할 수 있는 관계 인스턴스의 최대 수

  * 1:1, 1:N, M:N

  * M:N 관계에서만 관계가 속성을 가질 수 있다

      

* 약성 개체(Weak Entity)

  * 키 속성을 갖고 있지 않은 개체 > 부분키 (Partial Key)만을 가짐

  * 약성 개체는 개체를 식별할 수 있는 다른 개체와 식별 관계(Identifying Relationship)으로 맺어져야함

  * 약성 개체의 식별자는 다음의 속성의 조합으로 구성

    * 약성 개체의 부분키 속성 + 식별 개체의 키 속성

  * 안 만드는 게 좋음

      

* Ternary Relationship

  * 몇 대 몇 관계인지 파악하기 위해서는 두 개의 Entity를 고정시켜놓고 하나의 Entity와의 관계로 결정

  * Ternery Relationship의 경우에는 관계를 Entity로 설정하면 Binary relationships으로 표현 가능

    
