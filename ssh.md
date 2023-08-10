# ssh
- 1995.07 first release : 대학 네트워크에서 ID/Password를 낚아채는 일이 발생하여 개발 시작
- public key 암호 방식 사용
  - 비대칭 암호 방식
  - 암호화/복호화 사용 키 서로 다름
  - public key / private key 사용
    - public key : 암호화(평문 → 암호문)
    - private key : 복호화(암호문 → 평문)
  - 클라이언트에서 public & private key 생성
  - 해킹 시 public키 획득 : 클라이언트 요청 정보 확인 가능
  - 복호화 시 private키 필요 : 서버 응답 정보 확인 불가능

# ssh key 생성
- -t : 암호화 타입 설정
  - public key 방식으로 동작할 수 있는 다수의 암호화 알고리즘 차용
  - rsa : 암호화뿐만 아니라 전자서명이 가능한 최초의 알고리즘
- -b : 생성할 키의 비트수 지정
  - rsa : 최소 768비트 필요 / default 2048비트 / 안정성 4096
- -C : 주석
  - GitHub 권장사항 : 사용자 로그인 ID
 
- private key : ~/.ssh/id_rsa 파일 저장됨(default)
- public key : ~/.ssh/id_rsa.pub 파일 저장됨(default)

- passphrase : 키에 접근할 때마다 추가로 암호를 요구하게 함
