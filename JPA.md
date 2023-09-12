# ORM
- Object-relational mapping
- 자바의 객체와 데이터베이스를 연결하는 프로그래밍 기법
- eg. ![ORM](https://github.com/7ahyeon/everyday-spring-study/assets/107123698/38384629-4d50-4dd5-b4c6-3513497079ca)
- **SQL** 없이 자바 언어로만 데이터베이스에 접근해서 원하는 데이터를 받아올 수 있음
- 자바 코드를 통해 데이터베이스의 값을 객체처럼 사용함
- 장점
  - SQL을 직접 작성하지 않고 사용하는 언어로 데이터베이스에 접근 가능함
  - 객체지향적으로 코드를 작성할 수 있기 때문에 비즈니스 로직에만 집중 가능함
  - 데이터베이스 시스템에 대한 종속성 감소! 데이터베이스 시스템이 추상화되어 있기 때문에 DB 전환이 쉬움(eg.MySQL -> PostgreSQL) 
  - 매핑 정보 명확 : ERD에 대한 의존도를 낮출 수 있고 유지보수 시 유리함
- 단점
  - 프로젝트 복잡성이 커질수록 사용 난이도 증가함
  - ORM으로 해결 불가능한 경우 존재 : 복잡하고 무거운 쿼리

 # PostgreSQL vs MySQL
 - PostgreSQL
   - 복잡한 쿼리와 대규모 데이터베이스를 다룰 수 있는 기능이 풍부함
   - 테이블 상속, 함수 오버로딩 등의 기능을 갖춘 오픈소스 객체 관계형 데이터베이스(ORDBMS)
- MySQL
  - 설치와 관리가 비교적 쉽고 빠르며 신뢰할 수 있고 쉽게 파악할 수 있는 간단한 데이터베이스
  - 순수 관계형 데이터베이스(RDBMS)

# JPA
- Java Persistence API
- 자바에서 관계형 데이터베이스(RDB)를 사용하는 방식을 정의한 인터페이스
- 실제 사용을 위해서는 ORM 프레임워크 사용이 필요함(JPA = 인터페이스)
- 역할
  - 자바 객체와 데이터베이스를 연결해 데이터를 관리함
  - 객체 지향 도메인 모델과 데이터베이스의 다리 역할
- Persistence 영속성
  - 데이터를 생성한 프로그램의 실행이 종료되더라도 사라지지 않는 데이터의 특성
  - 특정 데이터 구조를 이전 상태로 복원할 수 있게 해주어 프로그램의 종료와 재개를 자유롭게 함
  - |Persistent object|영속성이 필요한 객체|
    |:--:|:--:|
    |Ephemeral object|영속성이 불필요한 객체|

# Hibernate
- JPA 인터페이스를 구현한 구현체이자 자바용 ORM 프레임워크
- 내부적으로 JDBC API 사용
- 목표 : 자바 객체를 통해 데이터베이스 종류에 상관없이 데이터베이스를 자유자재로 사용할 수 있게 함
![JPA](https://github.com/7ahyeon/everyday-spring-study/assets/107123698/cf59aa9e-9342-4e5e-a523-c4df8696695f)

# Entity
- 데이터베이스의 테이블과 매핑(직접 연결)되는 자바 객체
- 데이터베이스에 영향을 미치는 쿼리를 실행하는 객체

# Entity manager factory
- 엔티티 매니저를 생성함

# Entity manager
- 엔티티를 관리해 데이터베이스와 애플리케이션 사이에서 객체를 생성, 수정, 삭제하는 역할
- eg. 회원 2명이 동시에 회원가입을 하려는 경우 엔티티 매니저 팩토리가 각각의 엔티티 매니저를 생성, 생성된 매니저가 가입 처리해 데이터베이스에 회원 정보를 저장함(필요한 시점에 데이터베이스와 연결한 뒤 쿼리를 처리함)

# Spring boot - Entity manager factory
- 스프링 부트는 내부에서 엔티티 매니저 팩토리를 하나만 생성해서 관리함
- @PersistenceContext / @Autowired 애노테이션을 사용해서 엔티티 매니저 사용함



- 출처. https://goldenrabbit.co.kr/product/springboot3java/)https://goldenrabbit.co.kr/product/springboot3java/
