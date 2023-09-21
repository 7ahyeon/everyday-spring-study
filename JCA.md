# JCA
- Java Cryptography Architecture
- JAVA 보안 플랫폼(Java 보안 기능 중 핵심)
- Provider 구조를 사용하여 보안과 관련된 다양한 API를 제공함
- eg. 전자서명(Digital Signature), 메시지 다이제스트(Message Digest), 인증서 유효성 검사(Certificate Validation), 키 생성 etc.

# 설계원칙
- Java 플랫폼 기반 애플리케이션 정보보호 기술 적용 시 JAVA 보안 플랫폼(JCA) API를 통해 보안 서비스 요청
- JCA에서 제공하는 보안 서비스는 JAVA 보안 플랫폼에 장착된 Provider로 구현됨
- Provider 목록 : jre/lib/security/java.security 파일에 기술되어있음

# 아키텍쳐
- Cryptographic Service Providers
- 모든 Provider : java.security.Provider 클래스의 구현체
- 특정 알고리즘의 인스턴스 필요 시 Provider 저장소에서 해당 알고리즘에 적합한 구현체 클래스를 찾아 클래스 인스턴스를 생성함
- JCA 사용법 : 특정 객체 타입(eg.MessageDigest)과 알고리즘 또는 서비스를 요청하면 됨(특정 Provider의 객체도 요청 가능)
```java
MessageDigest md = MessageDigest.getInstance("SHA-256");
MessageDigest md = MessageDigest.getInstance("SHA-256", "ProviderC");
```
![provider](https://github.com/7ahyeon/everyday-spring-study/assets/107123698/c922dd54-b4f3-41d9-9ce1-db7a8f6d22a7)
