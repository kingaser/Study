## HttpServletRequest
### HttpServletRequest 역할
HTTP 요청 메시지를 개발자가 직접 파싱해서 사용해도 되지만, 매우 불편함. 서블릿은 개발자가 HTTP 요청 메시지를
편리하게 사용할 수 있도록 개발자 대신에 HTTP 요청 메시지를 파싱하고 그 결과를 HttpServletRequest 객체에 담아서 제공

HttpServletRequest를 사용하면 다음과 같은 HTTP 요청 메시지를 편리하게 조회할 수 있음
![Untitled (1).png](..%2F..%2F..%2F..%2F..%2F..%2FDownloads%2FUntitled%20%281%29.png)

- START LINE
  - HTTP 메서드
  - URL
  - 쿼리 스트링
  - 스키마, 프로토콜
- 헤더
  - 헤더 조회
- 바디
  - form 파라미터 형식 조회
  - message body 데이터 직접 조회
HttpServletRequest 객체는 추가로 여러가지 부가기능도 함께 제공

### 임시 저장소 기능
- 해당 HTTP 요청이 시작부터 끝날 때 까지 유지되는 임시 저장소 기능
  - 저장 : request.setAttribute(name, value)
  - 조회 : request.getAttribute(name)

### 세션 관리 기능
- request.getSession(create: true)
- 중요 : HttpServletRequest, HttpServletResponse를 사용할 때 가장 중요한 점은 이 객체들이 HTTP요청 메시지, HTTP 응답
메시지를 편리하게 사용하도록 도와주는 객체라는 점
따라서 이 기능에 대해서 깊이 있는 이해를 하려면 HTTP 스펙이 제공하는 요청, 응답 메시지 자체를 이해해야 함

---
### HttpServletRequest 기본 제공 기능
로컬에서 테스트하면 IPv6정보가 나오는데, IPv4 정보를 보고 싶으면 다음 옵션을 VM option에 추가   
-Djava.net.preferIPv4Stack=true

### HTTP 요청 데이터
- GET - 쿼리 파라미터
  - /url?username=hello&age=20
  - 메시지 바디 없이, URL의 쿼리 파라미터 형식으로 전달 username=hello&age=20
  - 예) 회원 가입, 상품 주문, HTML Form 사용
- POST - HTML Form
  - content-type: application/x-www-form/urlencoded
  - 메시지 바디에 쿼리 파라미터 형식으로 전달 username=hello&age=20
  - 예) 회원 가입, 상품 주문, HTML Form 사용
- HTTP message body에 데이터를 직접 담아서 요청
  - HTTP API에서 주로 사용, JSON, XML, TEXT
- 데이터 형식은 주로 JSON사용
  - POST, PUT, PATCH

POST - HTML Form 예시
![Untitled (2).png](..%2F..%2F..%2F..%2F..%2F..%2FDownloads%2FUntitled%20%282%29.png)

### HTTP 요청 데이터 - GET 쿼리 파라미터
- 검색, 필터, 페이징 등에서 많이 사용하는 방식
- 쿼리 파라미터는 URL에 ?를 시작으로 보냄. 추가 파라미터는 &으로 구분
- http://localhost:8080/request-param?username=hello&age=20
- 복수 파라미터에서 단일 파라미터 조회
  - username=hello&username=kim
  - request.getParameter()는 하나의 파라미터 이름에 대해서 단 하나의 값만 있을때 사용
  - 중복일 때는 request.getParameterValues()를 사용
  - 중복일 때 request.getParameter()를 사용하면 request.getParameterValues()의 첫 번째 값을 반환

### HTTP 요청 데이터 - POST HTML Form
- 특징
  - content-type: application/x-www-form-urlencoded
  - 메시지 바디에 쿼리 파라미터 형식으로 데이터를 전달

웹 브라우저가 결과를 캐시하고 있어서, 과거에 작성했던 html결과가 보이는 경우가 있음
이때는 웹 브라우저의 새로 고침을 직접 선택
서버를 재시작 하지 않은 결과일 수 있음
- POST의 HTML Form을 전송하면 웹 브라우저는 다음 형식으로 HTTP메시지를 만듬(웹 브라우저 개발자 모드 확인)
  - 요청 URL: http://localhost8080/request-param
  - content-type: application/x-www-form-urlencoded
  - message body: username=hello&age=20

application/x-www-form-urlencoded형식은 앞서 GET에서 살펴본 쿼리 파라미터 형식과 같음
쿼리 파라미터 조회 메서드 그대로 사용하면 됨

클라이언트(웹 브라우저) 입장에서는 두 방식에 차이가 있지만, 서버 입장에서는 둘의 형식이 동일하므로 request.getParameter()로
편리하게 구분없이 조회 가능

정리하면 request.getParameter()는 GET URL 쿼리 파라미터 형식도 지원하고, POST HTML Form 형식 둘다 지원

참고
- content-type은 HTTP 메시지 바디의 데이터 형식을 지정
- GET URL 쿼리 파라미터 형식으로 클라이언트에서 서버로 데이터를 전달할 때는 HTTP 메시지 바디를 사용하지 않기 때문에 content-type 이 없음
- POST HTML Form 형식으로 데이터를 전달하면 HTTP 메시지 바디에 해당 데이터를 포함해서 보내기 때문에
바디에 데이터가 어떤 형식인지 content-type을 꼭 지정해야 함
- 이렇게 폼으로 데이터를 전송하는 형식을 application/x-www-form-urlencoded라 함

### HTTP 요청 데이터 - API 메시지 바디 - 단순 텍스트
- HTTP message body에 데이터를 직접 담아서 요청
  - HTTP API에서 주로 사용, JSON, XML, TEXT
  - 데이터 형식은 주로 JSON사용
  - POST, PUT, PATCH
- HTTP 메시지 바디의 데이터를 inputStream을 사용해서 직접 읽을 수 있음
- inputStream은 byte 코드를 반환
- byte코드를 문자(String)로 보려면 문자표(Charset)를 지정해 줘야 함
- 문자 전송
  - POST http://localhost:8080/reqeust-body-string
  - content-type: text/plain
  - message body: hello
  - 결과: messageBody = hello

### HTTP 요청 데이터 - APi 메시지 바디 - JSON
JSON 형식 전송
- POST http://localhost:8080/reqeust-body-json
- content-type: application/json
- message body: {"username": "hello", "age": 20}
- 결과: messageBody = {"username": "hello", "age": 20}

### HttpServletResponse - 기본 사용법
HttpServletResponse 역할
- HTTP 응답 메시지 생성
  - HTTP 응답코드 지정
  - 헤더 생성
  - 바디 생성
- 편의 기능 제공
  - Content-Type, 쿠키, Redirect

### HttpServletResponse - 단순 텍스트, HTML
- HTML반환 시 content-type: text/html로 지정
- http://localhost:8080/response-html
- 페이지 소스보기를 사용하면 결과 HTML을 확인할 수 있음

### HTTP 응답 데이터 - API JSON
HTTP 응답으로 JSON을 반환할 때는 content-type을 application/json로 지정해야 함. Jackson 라이브러리가 제공하는
objectMapper.writerValueAsString()를 사용하면 객체를 JSON문자로 변결할 수 있음

참고 : application/json은 스펙상 utf-8 형식을 사용하도록 정의되어 있음. 그래서 스펙에서 charset-utf-8과 같은 추가 파라미터를
지원하지 않음. 따라서 application/json 이라고만 사용해야지 application/json;charset=utf-8 이라고 전달하는 것은
의미없는 파라미터를 추가한 것이 됨
response.getWriter()를 사용하면 추가 파라미터를 자돌으로 추가해버림. 이때는
response.getOutputStream()으로 출력하면 그런 문제가 없음