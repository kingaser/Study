## MyBatis / JPA
MyBatis와 JPA(Java Persistence API)는 데이터베이스와의 상호 작용을 간편하게 처리하고 객체와 데이터베이스 간의 매핑을 지원하는 두 가지 데이터 액세스 기술

### MyBatis
- 데이터베이스 연동을 단순화하고자 하는 목적으로 개발된 자바 기반의 오픈소스 ORM프레임워크 입니다.
SQL 매핑을 XML 파일이나 어노테이션을 사용해서 처리하고, JDBC 코드의 반복 작성을 줄여줌으로써 개발자가 데이터베이스와의 상호작용을 더 편리하게 할 수 있도록 지원합니다.

- 역할
  - MyBatis는 SQL쿼리를 XML  파일 또는 어노테이션을 통해 매핑하고, 데이터베이스의 CRUD(생성, 조회, 갱신, 삭제) 작업을 수행하는 역할

- 특징
  - SQL 쿼리를 직접 작성하고 관리하므로, 개발자가 직접 쿼리를 최적화하고 제어
  - 객체와 데이터베이스 간의 매핑은 XML파일을 사용하거나 어노테이션을 통해 수동으로 정의
  - SQL 매핑과 객체 매핑을 세밀하게 조정할 수 있는 유연성 제공
  - 복잡한 쿼리나 데이터베이스와 밀접한 상호 작용이 필요한 경우 유용

- 장점
  - 유연성 : SQL을 직접 작성할 수 있기 때문에 개발자가 데이터베이스와의 상호 작용을 높은 수준으로 제어할 수 있습니다.
복잡한 쿼리나 특수한 요구사항에 대해 뛰어난 유연성을 제공합니다.
  - 단순성 : 개발자가 직접 SQL을 작성하고 매핑하기 때문에 간단한 설정으로 빠르게 개발을 시작할 수 있습니다.
  - 캐시 관리 : 캐시를 효과적으로 관리하여 동일한 쿼리의 반복 수행 시 성능을 향상시킬 수 있습니다.
  - 프로시저 및 커서 지원 : 저장 프로시저와 커서를 효과적으로 다룰 수 있는 기능을 제공합니다.
  - 동적 SQL 지원 : 동적 SQL을 지원하여 조건에 따라 동적으로 SQL을 생성할 수 있습니다.

- 단점
  - 객체-관계 매핑 : 객체-관계 매핑을 지원하지만, JPA나 Hibernate와 같은 다른 ORM 프레임워크에 비해 객체 지향적인 프로그래밍에 제약이 있습니다.
  - SQL 작성 부담 : SQL을 직접 작성해야 하므로 복잡한 비즈니스 로직이나 다양한 연관 관계를 가진 엔티티에 대한 작업이 상대적으로 번거로울 수 있습니다.
  - 높은 학습 곡선 : SQL 작성 및 매핑에 대한 이해가 필요하므로 초기 학습 곡선이 다소 높을 수 있습니다.
  - 자동화된 객체 매핑 부족 : JPA와 같은 다른 ORM 프레임워크에 비해 객체와 데이터베이스 테이블 간의 자동화된 매핑 기능이 부족할 수 있습니다.
  - 일부 개발자들에게는 불편함 : SQL을 직접 다루는 것이 익숙하지 않은 개발자들은 ORM을 선호할 수 있습니다.

### JPA(Java Persistence API)
- Java에서 데이터베이스와의 상호 작용을 간편하게 할 수 있도록 도와주는 자바 ORM 표준입니다.
JPA는 객체와 데이터베이스 간의 매핑을 지원하며, 개발자가 SQL 쿼리를 직접 작성하지 않고도 데이터를 데이터베이스에 저장하고 검색할 수 있게 해줍니다.

- 역할
  - JPA는 자바 객체와 데이터베이스 간의 매핑을 통해 객체 지향 프로그래밍 패러다임을 유지하면서 데이터베이스 조작을 처리하는 역할

- 특징
  - 객체와 데이터베이스 간의 매핑은 어노테이션을 통해 자동으로 수행. 개발자가 매핑을 세부적으로 정의하지 않아도 기본 매핑 규칙에 따라 매핑
  - JPQL(Java Persistence Query Language)을 사용하여 객체 지향적인 방식으로 쿼리를 작성
  - 객체 그래프 탐색과 지연 로딩 등과 같은 ORM(Object-Relational Mapping) 특징을 통해 객체 간의 관계를 더욱 자연스럽게 다룸
  - JPA 구현체(예 : Hibernate)는 쿼리 최적화와 데이터베이스와의 성능 향상을 위한 다양한 기능을 제공
  - JPA는 표준 인터페이스이므로 다양한 JPA 구현체를 선택하여 사용

- 장점
  - 객체-관계 매핑(ORM) : 객체와 데이터베이스 테이블 간의 매핑을 지원하여 객체 지향 프로그래밍과 관계형 데이터베이스 간의 불일치를 해소합니다.
  - 객체 지향적인 프로그래밍 : 자바 객체 지향 프로그래밍 스타일에 더 가깝게 개발할 수 있도록 도와줍니다.
객체 지향 모델을 유지하면서 데이터베이스에 데이터를 저장하고 조회할 수 있습니다.
  - 자동화된 객체 매핑 : 개발자가 직접 SQL을 작성하지 않아도 객체와 테이블 간의 매핑을 자동으로 처리해주기 때문에 생산성이 향상됩니다.
  - 표준 인터페이스 : 자바 표준 인터페이스로서 여러 ORM프레임워크에서 구현되고 있습니다.
이는 벤더 독립성을 제공하며, 애플리케이션 코드를 특정 데이터베이스에 종속되지 않도록 합니다.
  - 캐시 기능 : 영속성 컨텍스트를 통해 캐시를 제공하여 반복적인 조회에서 성능 향상을 도모합니다.
  - 검색 기능 : JPQL(Java Persistence Qeury Language)을 제공하여 객체 지향적인 방식으로 데이터를 검색할 수 있습니다.
* 벤더 독립성 : 어떤 소프트웨어나 기술이 특정 벤더(공급업체)에 종속되지 않도록 하는 것을 의미

- 단점
  - 학습 곡선 : ORM의 개념을 다루기 때문에 초기 학습 곡선이 높을 수 있습니다.
복잡한 매핑이나 성능 튜닝을 위해서는 깊은 이해가 필요합니다.
  - 커스터마이징의 어려움 : 특정 데이터베이스에서 제공하는 고급 기능을 모두 활용하려면 JPA에서 추상화된 기능을 우회하거나 직접 SQL을 작성해야 할 수 있습니다.
  - 성능 고민 : 어떤 경우에는 SQL을 작성하는 것이 성능상 이점이 있을 수 있으며, 이는 JPA의 추상화를 통한 성능 손실을 감수하게 됩니다.
  - 비용 : 일부 경우에는 ORM을 사용하면서 발생하는 오버헤드가 있을 수 있습니다. 특히 대용량 트래픽이나 복잡한 쿼리를 다르는 경우 성능 고민이 필요할 수 있습니다.
  - 복잡한 쿼리 작성 : 복잡한 쿼리를 작성할 때는 JPQL이나 Criteria API를 사용해야 하는데, 이는 SQL에 익숙한 개발자에게는 어려울 수 있습니다.

---
- 둘 다 데이터베이스와의 상호 작용을 지원하는 기술이지만, MyBatis는 SQL 쿼리와 객체 매핑에 중점을 두며 개발자가 더 직접적으로 제어
- 반면에 JPA는 객체 지향 프로그래밍 패러다임을 지키며 데이터베이스 조작을 처리하는데 중점을 두는 ORM 기술로, 객체와 데이터베이스
간의 매핑을 자동화하고 편리한 객체 관리 기능을 제공
