## 애플리케이션 계층(application)
- HTTP, SMTP, SSH, FTP가 대표적이며 웹 서비스, 이메일 등 서비스를 실질적으로 사람들에게 제공하는 층

### HTTP
- HTTP(Hypertext Transfer Protocol)은 처음에는 서버와 브라우저간에 데이터를 주고 받기 위해 설계된 프로토콜
- 지금은 브라우저 뿐만 아니라 서버와 서버간의 통신할 때도 많이 이용
1. HTTP는 헤더를 통한 확장이 쉬움
   - 헤더값에다가 어떠한 값을 넣어서 HTTP 요청을 할 때 쉽게 다른 값을 추가할 수 있음
2. HTTP는 stateless
   - 동일한 연결에서 연속적으로 수행되는 두 요청 사이에 연속적인 상태(state)값은 없음

### SSH
- SSH(Secure Shell Protocol)는 보안되지 않은 네트워크에서 네트워크 서비스를 안전하게 운영하기 위한
암호화 네트워크 프로토콜
- 보통 프라이빗 키가 있는 경로에서 키를 명시하고 실행함
  - ssh <pem>   <user>@<serverIP>
- SCP를 이용해서 SSH를 이용해 파일을 전송할 수 있음
  - scp <source> <destination>

### FTP
- FTP(File Transfer Protocol)는 노드와 노드간의 파일을 전송하는데 사용되는 프로토콜
- 지금은 파일을 암호화해서 전송하는 FTPS 또는 SFTP로 대체되고 있음

### SMTP
- 인터넷을 통해 메일을 보낼 때 사용되는 프로토콜(Simple Mail Transfer Protocol)
- 보통 서비스를 운영하면 메일링 서비스를 하게 되는데 node.js를 통해 메일을 보낸다면 nodemailer를 통해 보내야 함
- 자바스크립트 진영에서는 Nodemailer라는 라이브러리가 있는데 JS를 기반으로 SMTP를 통해 메일을 보낼 수 있는 라이브러리