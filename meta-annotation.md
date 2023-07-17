# meta-annotation
- 사용할 어노테이션을 정의하는 어노테이션

# @Target
- Indicates the contexts in which an annotation type is applicable.
- 사용할 어노테이션의 적용 타입 환경(contexts)을 나타낸다.
- The declaration contexts and type contexts in which an annotation type may be applicable are specified in JLS 9.6.4.1, and denoted in source code by enum constants of java.lang.annotation.ElementType.
- 정의 및 타입 환경은 JLS 9.6.4.1에 지정되어있으며 java.lang.annotation.ElementType의 enum 상수로 표시된다. 
```
public enum ElementType {
    /** 타입(클래스, 인터페이스, enum)
     * Class, interface (including annotation type), or enum declaration */
    TYPE,
    /** 필드(멤버 변수, enum 상수)
     * Field declaration (includes enum constants) */
    FIELD,
    /** 메서드
     * Method declaration */
    METHOD,
    /** 매개변수(파라미터)
     * Formal parameter declaration */
    PARAMETER,
    /** 생성자
     * Constructor declaration */
    CONSTRUCTOR,
    /** 지역 변수
     * Local variable declaration */
    LOCAL_VARIABLE,
    /** 어노테이션 타입
     * Annotation type declaration */
    ANNOTATION_TYPE,
    /** 패키지
     * Package declaration */
    PACKAGE,
    /** 타입 매개변수(eg Gegeneric)
     * Type parameter declaration
     * @since 1.8
     */
    TYPE_PARAMETER,
    /** 타입 사용 대상
     * Use of a type
     * @since 1.8
     */
    TYPE_USE
}

```
* * *
- context : 문맥, 맥락, 환경
- denote : 표시하다
- enum (enumerated type) : 열거형 (서로 연관된 상수들의 집합)
- constant : 상수 (고정된 값)
- JSL (Java Language, Specification) : 자바 언어 사양 (언어가 구현되는 방법에 대한 기술적인 세부사항 설명)
* * *
- 멤버 변수 (member variable) : 클래스 영역에서 선언된 변수 (메서드 외부)
- (> 선언위치 구분; 지역 변수(local variable) : 메서드 내부 선언)
  - 클래스 변수 : 모든 객체 공통 속성 고정 (static)
  - (> 속성 구분; 인스턴스 변수(instance variable) : 개별 객체 속성 별개)
- generic
- parameter
