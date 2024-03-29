## 웹 소켓
웹 소켓은 클라이언트와 서버를 연결하고 실시간으로 통신이 가능하도록 하는 기술입니다.
HTTP에서 발생하는 것처럼 별도의 요청을 보내지 않고도 데이터를 수신할 수 있어, 연결이 설정되면 데이터는 요청을 보낼 필요 없이 저절도 불러와집니다.
웹 소켓은 정보를 동시에 송수신할 수 있어서 양방향 통신이 가능하므로 정보 교환이 더 빨라집니다.

클라이언트와 서버 간의 연결은 당사자 중 하나에 의해 종료되거나 시간 초과에 의해 닫힐 때 까지 열린상태로 유지됩니다.
클라이언트와 서버간의 연결을 설정하기 위해 핸드셰이크를 수행합니다.
설정된 연결은 당사자 중 하나에 의해 종료되거나 시간 초과에 의해 닫힐 때 까지 열린 상태로 유지됩니다.

웹 소켓을 사용하면 전송되는 데이터를 암호화할 수 있습니다. 
이를 위해 추가 기능인 WSS 프로토콜을 통해 사용되며, 송신측에서는 데이터를 인코딩하고 수신측에서는 디코딩합니다.
모든 중개자의 경우 정보가 암호화된 상태로 유지되고, 암호화가 없으면 데이터가 위협의 대상이 됩니다.

### WSS
WSS는 TSL(전송 계층 보안(Transport Layer Security))이라는 보안 계층을 통과해 전달되므로 송신자 측에서 데이터가 암호화되고, 복호화는 수신자 측에서 이뤄지게 됩니다.
따라서 데이터가 담긴 패킷이 암호화된 상태로 프록시 서버를 통과하므로 프록시 서버는 패킷 내부를 볼 수 없게 됩니다.

---
웹 소켓을 교환 플랫폼, 게임 애플리케이션, 챗봇, 푸시 알림, 소셜 네트워크, 채팅 애플리케이션, IoT 애플리케이션에서 사용합니다.
