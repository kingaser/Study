## JSON
JSON(JavaScript Object Notation)
Javascript 객체 문법으로 구조화된 데이터교환 형식, python, javascript, java 등 여러 언어에서 데이터 
교환 형식으로 쓰이며 객체 문법 말고도 단순 배열, 문자열도 표현 가능

### Javascript 객체 문법
- key와 value로 구성됨 {key : value}
- 이미 존재하는 키를 중복 선언하면 나중에 선언된 해당 키에 대응한 값으로 덮어 쓰이게 됨

### 데이터 + 교환 형식
- 데이터는 추상적인 아이디어에서부터 시작해 구체적인 측정에 이르기까지 다양한 의미로 쓰임
- 실험, 조사, 관찰 등으로 부터 얻은 사실이나 자료 등을 의미

### 여러 언어에서의 쓰임
- 객체, 해시테이블, 딕셔너리 등으로 변환되어 쓰임
  - JS -> javascript object
  - Python -> dict
- 독립적

### 단순 배열, 문자열 표현 가능
- [1, 2, 3, 4], "aaaaaaaaaaaa"
- 하지만 주로 key, value 형태로 사용

### JSON 타입
- JS와 유사하지만 undefined, 메서드 등을 포함하지 않음
- 수(int, number)
- 문자열(String)
- 참/거짓(Boolean)
- 배역(Array)
- 객체(Object)
- null

### JSON 직렬화, 역직렬화
- 직렬화란 외부의 시스템에서도 사용할 수 있도록 바이트(byte) 형태로 데이터를 변환하는 기술
- 역직렬화는 반대를 의미
- JSON.parse()
- JSON.stringify()