## PSA(Portable Sevice Abstraction)
- 환경의 변화와 관계없이 일관된 방식의 기술로의 접근 환경을 제공하는 추상화 구조를 말합니다.
- 특정 클래스가 추상화된 상위 클래스를 일관되게 바라보며 하위 클래스의 기능을 사용하는 것이 PSA의 기본 개념입니다.
- PSA가 적용된 코드는 개발자가 기존에 작성된 코드를 수정하지 않으면서 확장할 수 있으며, 어느 특정 기술에 특화되어있지 않은 코드입니다.
- Spring에서 동작할 수 있는 라이브러리들은 POJO 원칙을 지키기 위해 PSA 형태의 추상화가 되어있으며
Spring Web MVC, Spring Transaction, Spring Cache, Spring Data, 메일 서비스 등의 다양한 PSA를 제공하고 있습니다.

### 서비스에 적용하는 PSA 기법
![image](https://github.com/kingaser/Study/assets/104209781/60d8c45f-e688-4d10-8de2-08d2ed6151dd)
- 서비스 추상화는 추상화의 개념을 애플리케이션에서 사용하는 서비스에 적용하는 기법입니다.
- 위 그림에서처럼 구현체에 직접적으로 연결해서 얻는 것이 아닌 인터페이스를 통해 간접적으로 연결되어 객체를 얻을 수 있게 됩니다.
- 또한, DbClient 클래스에서 JdbcConnector 구현체를 사용하더라도 Connection을 얻는 방식은 getConnection() 메서드로 다른 구현체와 동일합니다.
- 일관된 방식으로 해당 서비스의 기능을 사용할 수 있습니다.
- 이처럼 애플리케이션에서 특정 서비스를 이용할 때, 서비스의 기능을 접근하는 방식 자체를 일관되게 유지하면서 기술 자체를 유연하게
사용할 수 있도록 하는 것을 PSA(일관된 서비스 추상화)라고 합니다.
---
PSA는 어떤 서비스를 이용하기 위한 접근 방식을 일관된 방식으로 유지하여 애플리케이션에서 사용하는 기술이 변경되더라도
최소한의 변경만으로 변경된 요구 사항을 반영하기 위해 사용합니다.

PSA를 통해서 애플리케이션의 요구 사항 변경에 유연하게 대처할 수 있습니다.

### Spring PSA
- Spring Framework에서 제공하는 개발 페러다임으로, 여러 개의 기술과 기능을 통합하고 추상화하여 개발자에게 일관된 프로그래밍 모델을 제공합니다.
- PSA는 특정 기술에 종송되지 않도록 설계되어 있어 개발자가 특정 기술의 세부 사항에 직접 종속되지 않고, 편리하게 다양한 기술을 사용할 수 있도록 도와줍니다.

### 기술적 영역
- 데이터 엑세스(Data Access)
  - Spring JDBC, Hibernate, MyBatis 등 다양한 데이터 액세스 기술을 추상화하여 일관된 데이터 액세스 계층을 제공합니다.
- 트랜잭션 관리(Transaction Management)
  - Spring은 선언적 트랜잭션 관리를 통해 여러 트랜잭션 매니저와 통합될 수 있도록 지원하며, 트랜잭션 관리에 대한 추상화를 제공합니다.
- ORM(Object-Relational Mapping)
  - Spring은 여러 ORM 프레임워크와 통합되어 객체와 데이터베이스 간의 매핑을 단순화하고 표준화합니다.
- AOP(Aspect-Oriented Programming)
  - Spring AOP는 애플리케이션에서 관심사를 분리하고 모듈화하기 위한 AOP 기능을 제공합니다.
- 메시징(Messaging)
  - Spring은 JMS(Java Message Service)를 비롯한 다양한 메시징 기술에 대한 추상화를 제공하여 메시지 기반의 통신을 지원합니다.
- 이벤트 처리(Event Handling)
  - Spring은 이벤트 리스너와 함께 이벤트 기반의 프로그래밍을 지원합니다.
- 캐시(Caching)
  - Spring은 캐싱 추상화를 통해 여러 캐시 프로바이더와 통합되어 쉽게 캐싱을 사용할 수 있도록합니다.
--- 
Spring PSA는 이러한 추상화 계층을 통해 개발자가 특정 기술의 구체적인 구현에 종속되지 않도록하며, 유연성과 확장성을 제공합니다.
PSA는 Spring의 핵심 철학 중 하나로, 코드의 재사용성과 유지보수성을 높이고 다양한 환경에서 쉽게 적용할 수 있도록 도와줍니다.
