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

# Persistence 영속성
- 데이터를 생성한 프로그램의 실행이 종료되더라도 사라지지 않는 데이터의 특성
- 특정 데이터 구조를 이전 상태로 복원할 수 있게 해주어 프로그램의 종료와 재개를 자유롭게 함
- JPA에서의 영속성 : 엔티티를 사용하고 바로 폐기하지 않고 저장 후 지속적으로 사용하며 이점을 얻는 것
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
- Non Thread-safety : per Thread로 바인딩됨
- eg. 회원 2명이 동시에 회원가입을 하려는 경우 엔티티 매니저 팩토리가 각각의 엔티티 매니저를 생성, 생성된 매니저가 가입 처리해 데이터베이스에 회원 정보를 저장함(필요한 시점에 데이터베이스와 연결한 뒤 쿼리를 처리함)

# Spring boot - Entity manager factory
- 스프링 부트는 내부에서 엔티티 매니저 팩토리를 하나만 생성해서 관리함
- @PersistenceContext / @Autowired 애노테이션을 사용해서 엔티티 매니저 사용함
  - 기본적으로 빈은 단일 생성 및 공유 사용 : 동시성 문제 발생 가능성 있음
  - 실제 엔티티 매니저와 연결하는 프록시(가짜) 엔티티 매니저 사용
  - 필요시 데이터베이스 트랜잭션과 관련된 실제 엔티티 매니저 호출
  - 실제 엔티티 매니저 : Spring Data JPA에서 생성 및 관리(개발자 직접 관리X)

```java
@PersistenceContext
EntityManager em; // 프록시 엔티티 매니저 : 필요시 실제 엔티티 매니저 호출
```
# Persistence Context
- 영속성 컨텍스트 : JPA의 중요한 특징 중 하나
- 엔티티 매니저가 엔티티를 저장하고 관리하는 가상의 공간
- 스프링 부트 : 자바 코드 작성 -JPA-> 자동 쿼리 변경
- 특징 : **데이터베이스의 접근을 최소화해 성능을 높일 수 있음**
  - 1차 캐시
    - 영속성 컨텍스트 내부에 있는 첫 번째 캐시
    - 각 Thread의 1차 캐시는 별도로 동작하는 것을 전제로 함
    - 엔티티 조회 : 1차 캐시에서 데이터 조회 -> 값이 있으면 반환 -> 값이 없으면 데이터베이스 조회 -> 1차 캐시 저장 후 반환
    - 캐시된 데이터 조회시 데이터베이스를 거치지 않아도 되기 때문에 매우 빠르게 조회할 수 있음
  - 쓰기 지연
    - Transactional write-behind
    - 트랜잭션을 커밋하기 전까지는 데이터베이스에 실제로 질의문을 보내지 않고 쿼리를 모았다가 커밋시 한번에 실행하는 것
    - 적당한 묶음으로 쿼리를 요청할 수 있어 데이터베이스 시스템의 부담 줄일 수 있음
  - 변경 감지
    - 트랜잭션을 커밋하면 1차 캐시에 저장되어 있는 엔티티의 값과 현재 엔티티의 값을 비교해서 변경된 값이 있다면 변경 사항을 감지해 변경된 값을 데이터베이스에 자동으로 반영함
    - 쓰기 지연과 동일 장점 : 적당한 묶음으로 쿼리를 요청할 수 있어 데이터베이스 시스템의 부담 줄일 수 있음
  - 지연로딩
    - Lazy Loading
    - 쿼리로 요청한 데이터를 애플리케이션에 바로 로딩하는 것이 아니라 필요할 때 쿼리를 날려 데이터를 조회하는 것
    - <-> 즉시로딩 : 조회할 때 쿼리를 보내 연관된 모든 데이터를 가져옴
- **캐시를 하거나, 자주 쓰지 않게 하거나, 변화를 감지해서 미리 준비하거나!**

# 엔티티의 4가지 상태
- 비영속(transient) : 영속성 컨텍스트와 전혀 관계가 없음(엔티티 처음 생성시)
- 관리(managed) : 엔티티 매니저가 관리함 : persist
- 분리(detached) : 영속성 컨텍스트에서 관리하지 않음 : detach
- 삭제(removed) : 영속성 컨텍스트와 데이터베이스에서 삭제됨 : remove

- 엔티티의 상태는 특정 메서드를 호출해 변경 가능!
- 필요에 따라 엔티티의 상태를 조절해 데이터를 올바르게 유지 및 관리 가능함

```java
public class EntityManagerTest {
  @Autowired
  EntityManager em;

  public void example() {
  // 비영속 transient : 영속성 컨텍스트와 전혀 관계가 없음(엔티티 처음 생성시)
  Member member = new Member(1L, "홍길동");

  // 관리 managed : 엔티티 매니저가 엔티티를 관리하는 상태
  em.persist(member);

  // 분리 detached : 엔티티를 영속성 컨텍스트에서 관리하지 않는 상태
  em.detach(member);

  // 삭제 removed : 영속성 컨텍스트와 데이터베이스에서 삭제됨
  em.remove(member);
  }
}
```

- 출처. https://goldenrabbit.co.kr/product/springboot3java/)https://goldenrabbit.co.kr/product/springboot3java/
