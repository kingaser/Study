## PSA(Portable Sevice Abstraction)
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
