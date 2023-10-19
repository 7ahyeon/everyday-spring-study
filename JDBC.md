# setAutoCommit
```java
public void setAutoCommit(boolean value)
```
- java.sql.Connection
- true : 연결이 자동 커밋 모드이면 해당 연결의 모든 SQL 문이 개별 트랜잭션으로 실행되고 커밋됨(트랜잭션 도중에 이 메서드를 호출해도 트랜잭션이 커밋됨)
- false : JDBC 드라이버에서는 각 커밋 후에 새 트랜잭션을 암시적으로 시작함

# JNDI
- Tomcat/conf/context.xml
- WEB-INF/web.xml
