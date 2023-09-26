# taskkill
- 서버가 정상 종료되지 않아 포트가 계속 사용중일 때
```
netstat -ano
taskkill /f /pid '해당 포트 PID'
```
