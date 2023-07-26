# Oracle
- trunc(날짜) : 시간 절사
- trunc(숫자) : 소수점 절사
- CASE WHEN TEHN ELSE END : CASE 조건문
```
CASE
  WHEN 조건문 THEN 반환값
  ELSE 위의 조건이 아닐때 반환값
  END
```
- NVL(컬럼, NULL일때 반환값) : NULL인 경우 지정값 아닌 경우 원래 값 출력하는 함수
- NVL(MAX(증가시킬 컬럼명), 0) + 1 : NULL인 경우 0, 아닌 경우 최대값 + 1
