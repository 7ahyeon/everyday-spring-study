# hamcrest
- JUnit에 사용되는 Matcher 라이브러리
- 테스트 표현식 작성 시 문맥적으로 자연스러운 문장을 만들도록 도와줌
- ex : assertEquals(expected, actual) > assertThat(expected, is(actual))

# Matcher Library
- 필터나 검색 등을 위해 값을 비교할 때 좀 더 편리하게 사용 가능하도록 도와주는 라이브러리

# hamcrest package
|패키지|설명|
|:-:|:-:|
|org.hamcrest.core|Object, 값들에 대한 기본 Matchers|
|org.hamcrest.beans|Java Bean과 그 값 비교에 사용되는 Matchers|
|org.hamcrest.collection|배열과 컬렉션 Matchers|
|org.hamcrest.number|수 비교를 하기 위한 Matchers|
|org.hamcrest.object|Object, Class 비교하는 Matchers|
|org.hamcrest.test|문자열 비교 Matchers|
|org.hamcrest.xml|xml 문서 비교 Matchers|

# org.hamcrest.core
|메서드|설명|클래스명|
|:-:|:-:|:-:|
|anything|어떤 오브젝트가 사용되는 일치한다고 판별|IsAnything|
|describedAs|테스트 실패 시에 보여줄 추가적인 메시지를 만들어주는 메시지 데코레이터|DescribedAs|
|equalTo|두 오브젝트가 동일한지 판별|IsEqual|
|is|내부적으로 eqaulTo와 동일|Is|
- assertThat(entity, equalTo(expectedEntity));
- assertThat(entity, is(equalTo(expectedEntity)));
- assertThat(entity, is(expectedEntity));

- 나머지 더 확인할 것 https://www.crocus.co.kr/1658
