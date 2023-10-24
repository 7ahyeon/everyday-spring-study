# MySQL
- STR_TO_DATE(문자열, 문자열 형식)
  - STR_TO_DATE('20231024', '%Y%m%d') : 2023-10-24
  - STR_TO_DATE('2023-10-24', '%Y%m%d') : 2023-10-24
  - STR_TO_DATE('22:30:18', '%H%i%s') : 22:30:18
  - STR_TO_DATE('22:30:18', '%H%i%s') : 10:30:18
- DATE_FORMAT(날짜, 출력 형식)
  - DATE_FORMAT(now(), '%Y%m%d %H%i%s') : 20231024 11:03:12
