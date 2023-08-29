# 엑셀 데이터 자동 Insert 쿼리 생성 서식
- CONCATENATE() : 문자열 합치는 함수 (Excel v2016 이후부터는 CONCAT 사용 권장)
  - INT : "&숫자&"
  - CHAR, VARCHAR : """&문자열&"""
  - DATE : """&TEXT(날짜, "형식(YYYY-MM-DD)")&"""
  - EXACT(A, B) : A=B면 TRUE, A!=B면 FALSE
  - IF(TRUE/FALSE, A, B) : TRUE면 A, FALSE면 B
```
=CONCATENATE("INSERT INTO table (seq, name, birth, gender) VALUES ("&A2&", """&B2&""", """&TEXT(C2, "YYYYMMDD")&""", """&IF(EXACT(D2, "여"), "1", "2")&""");")
```

# 큰 따옴표 / 작은 따옴표 in Oracle
- 큰 따옴표 "" : 테이블명 혹은 컬럼명 표시
- 작은 따옴표 '' : 문자열 표시
```
="INSERT INTO table (seq, name, birth, gender) VALUES ("&A2&", '"&B2&"', '"&TEXT(C2, "YYYYMMDD")&"', '"&IF(EXACT(D2, "여"), "1", "2")&"');"
```
