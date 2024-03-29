# HTTPS
- HTTPS(하이퍼텍스트 전송 프로토콜 보안, Hypertext Transfer Protocol Secure)는 웹 서버와 웹 브라우저 간의 통신을 보안하는 프로토콜
- HTTPS는 일반적인 HTTP와 달리 데이터의 암호화와 인증을 제공하여 데이터의 기밀성과 무결성을 보호
- HTTP 프로토콜에서 암호구간(SSL/TLS)을 얹은 프로토콜

## 동작 원리

![image](https://github.com/kingaser/Study/assets/104209781/57a83109-76fd-403e-8cd5-62e867fcfb45)

> SSL/TLS는 응용계층(HTTP)과 전송계층(TCP) 사이에서 동작
>
> SSL/TLS 핸드셰이크에 필요한 연결을 생성하기 위해 TCP 3-way 핸드셰이크 진행
>
> 서버와 클라이언트 간 TCP 연결이 맺어지고 나면, 아래와 같은 패킷 전달을 통해 암호화 통신 준비

1. 클라이언트는 Client Hello 단계에서 사용가능한 암호화/해시 알고리즘과 random 값을 전달
  random값은 추후 공통키를 만드는 과정에서 사용

2. 서버는 전달받은 암호화/해시 방식 중 우선순위가 높은 옵션을 선택해서 이를 클라이언트에 전달
  이때 서버고 random값을 하나 만들어서 전달
  클라이언트와 서버 모두 2개의 random값을 보유

3. 서버는 자신을 증명하기 위해서 서버 인증서를 전달
  사전에 인증기관(CA)으로부터 받은 디지털 서명을 함께 전달. 자신의 인증서가 위조되지 않았음을 증명하기 위함
  클라이언트는 공개된 Root CA의 퍼블릭 키를 통해 디지털 서명을 복호화
  복호화가 가능하면 해당 인증서는 공인된 기관으로부터 인증받은 인증서임을 확신할 수 있음
  검증이 끝났으니 클라이언트는 해당 인증서에 적힌 Public 키를 믿고 사용

4. 서버는 자신이 보낼 정보를 모두 보냈음을 알림

5. 클라이언트는 암호화에 사용할 키를 만들기 위해 재료를 생성. 이를 Pre Master Secret 이라 함
  클라이언트는 임의로 만든 Pre Master Secret을 서버의 Public 키로 암호화하여 서버에 전달
  서버는 자신의 Private 키를 통해 Pre Master Secret 추출 가능
6 ~ 9. 서버와 클라이언트는 Pre Master Secret과 이전에 주고받았던 random 값을 통해 Master Secret을 생성
  이 Master Secret으로 Session 키와 MAC 키를 생성
  이제부터는 이 공통키를 사용하자고 서로 마지막 확인

- 위 작업이 끝나면 클라이언트는 패킷을 보낼 때 암호화 과정을 진행
- MAC 키를 통해 데이터의 MAC 값을 구함. 데이터 변조 가능성이 있으므로 확인하기 위함
- 이후 MAC 값과 데이터를 Session 키로 암호화
- 암호화된 데이터를 헤더와 함께 서버로 전달

- 서버는 Session 키를 통해서 데이터와 MAC 값을 추출
- 데이터를 자신의 MAC 키로 MAC 값을 계산하고, 이를 클라이언트로부터 받은 값과 비교
- 만약 MAC 값이 같다면 데이터가 변조되지 않았음을 의미
- 검증을 마치면 데이터를 애플리케이션으로 올려 보냄

> 좀더 쉬운 이미지

![image](https://github.com/kingaser/Study/assets/104209781/34419ca2-f7ce-46ad-99e1-4dcb0b4629d0)

```
CA(Cerificate Authority)

- 공개키를 저장해주는 신뢰성이 검증된 민간기없
- CA 기업의 공개키는 브라우저가 이미 알고 있음
- 세계적으로 신뢰할 수 있는 기업으로 등록되어 있기 때문에, 브라우저가 인증서를 탐색하여 해독이 가능

- HTTPS도 무조건 안전한 것은 아님
- 신뢰받는 CA 기업이 아닌 자체 인증서를 발급한 경우가 이에 해당함
- 이때는 HTTPS지만 브라우저에서 '주의 요함', '안전하지 않은 사이트'와 같은 알림으로 주의받게 됨

```

### 데이터 암호화
- HTTPS는 데이터를 암호화하여 중간자 공격과 같은 보안 위협으로부터 보호
- 데이터가 암호화되면 제 3자가 데이터를 해석하거나 수정하는 것이 더 어려움

### 인증
- HTTPS는 서버의 신원을 확인하는 인증 과정을 포함
- 클라이언트(웹 브라우저)는 서버의 디지털 인증서를 받아 검증하며, 이를 통해 서버가 신뢰할 수 있는 엔터티임을 확인

### 무결성 보호
- HTTPS는 데이터의 무결성을 보장
- 데이터가 정송 중에 변경되지 않도록 하는 무결성 검사를 수행하여 데이터 변조를 방지

### 보안 통신 채널
- HTTPS는 TLS(Transport Layer Security) 또는 SSL(Secure Sockets Layer) 프로토콜을 사용하여 안전한 통신 채널을 설정
- 이 채널을 통해 클라이언트와 서버 간의 데이터 교환이 이루어짐

### HTTPS의 사용
- 주로 웹사이트에서 사용
- 로그인 정보, 결제 정보, 민감한 개인 정보 등을 전송해야 할 때 중요하게 사용

### URL앞에 "https://"
- HTTPS로 액세스하는 웹 페이지의 URL은 "https://"로 시작
- 일반적인 HTTP는 "http://"로 시작

### 비용 및 설정
- HTTPS를 사용하려면 SSL/TLS 인증서를 구입하고 웹 서버에 설치
- 그러나 Let's Encrypt와 같은 서비스를 통해 무료 인증서를 획득할 수도 있음

```
HTTPS는 사용자의 개인 정보와 데이터 보안을 강화하는 데 중요한 역할   
웹 브라우징, 온라인 쇼핑, 온라인 뱅킹 등과 같은 웹 활동 중에는 항상 HTTPS를 사용하고 있는지 확인하여 개인 정보를 안전하게 보호해야 함
```
