## Spring AOP
### AOP(관점 지향 프로그래밍)
- AOP는 프로그램 구조에 대해 또 다른 사고 방식을 제공하여 객체 지향 프로그래밍(OOP)를 보완합니다.
- OOP의 모듈화 핵심 단위는 클래스인 반면, AOP의 모듈화 단위는 관점입니다.
- Aspect를 사용하면 여러 유형과 개체에 걸쳐 문제를 모듈화 할 수 있습니다.
ex) 트랜잭션 관리
- AOP에서는 "Cross Cuttig Concerns" 횡단 관심사라고 합니다.

### AOP 프레임워크
- Spring의 주요 구성 요소 중 하나는 AOP 프레임워크 입니다.
- Spring IoC컨테이너는 AOP에 의존하지 않지만(원하지 않는 경우 AOP를 사용할 필요가 없음을 의미) AOP는 Spring IoC를 보완하여 매우 유능한 미들웨어 솔루션을 제공합니다.

### AspectJ 포인트 컷을 사용한 Spring AOP
- Spring은 스키마 기반 접근 방식이나 @AspectJ 어노테이션을 사용하여 사용자 정의 측면을 작성하는 간단하고 강력한 방법을 제공합니다.
- 이 두 가지 스타일 모두 위빙을 위해 Spring AOP를 계속 사용하면서 완전한 유형의 조언과 AspectJ 포인트 컷 언어 사용을 제공합니다.

### Spring AOP 유형
- Before Advice(Advice 전) : 조인 포인트 이전에 실행되지만 실행 흐름이 조인 포인트로 진행되는 것을 방지할 수 있는 기능이 없는 Advice입니다.(예외가 발생하지 않는 한)
- After Returning Advice(Advice 반환 후) : 조인 포인트가 정상적으로 완료된 후 실행하라는 Advice입니다. ex) 예외를 던지지 않고 메서드가 반환된 경우
- After Throwing Advice(Advice를 던진 후) : 예외를 던져 메서드가 종료되면 실행하라는 Advice입니다.
- After (Finally) Advice((최종) Advice 후) : 조인 포인트가 종료되는 수단(정상 또는 예외적 반화)에 관계없이 실행되도록 Advice합니다.
- Around Advice(어라운드 Advice) : 메서드 호출과 같은 조인 포인트를 둘러싸는 Advice입니다.
  - 가장 강력한 종류의 Advice입니다.
  - 메서드 호출 전후에 사용자 지정 행동을 수행할 수 있습니다.
  - 또한 조인 포인트로 진행할지 아니면 자체 반환 값을 반환하거나 예외를 던져 Advice된 메서드 실행을 단축하지 선택하는 역할도 수행합니다.
---
- Around Advice는 가장 일반적인 종류의 Advice입니다.
- AspectJ와 같은 Spring AOP는 전체 범위의 조언 유형을 제공하므로 필요한 동작을 구현할 수 있는 가장 덜 강력한 Advice유형을 사용하는 것이 좋습니다.
- 메서드의 반환 값으로 캐시를 업데이트하기만 하면 되는 경우 Around Advice가 동일한 작업을 수행할 수 있지만 Around Advice보다 반환 후 Advice를 구현하는 것이 더 좋습니다.
- 가장 구체적인 Advice유형을 사용하면 오류 가능성이 적은 간단한 프로그래밍 모델이 제공됩니다.
- 모든 Advice 매개변수는 정적으로 입력되므로 개체 배열이 아닌 적절한 유형의 조언 매개변수(ex : 메서드 실행에서 반환되는 값 유형)로 작업할 수 있습니다.
- 포인트 컷과 일치하는 조인 포인트 개념은 AOP의 핵심이며, 이는 가로채기만 제공하는 이전 기술과 구별됩니다.
- 포인트 컷을 사용하면 객체 지향 계층 구조와 독립적으로 조언을 타겟팅할 수 있습니다.
- 선언적 트랜잭션 관리를 제공하는 Around Advice를 여러 개체(ex : 서비스 계층의 모든 비즈니스 작업)에 걸쳐 있는 메서드 집합에 적용할 수 있습니다.

### Spring AOP 기능 및 목표
- Spring AOP는 순수 Java로 구현되어있어, 특별한 컴파일 과정이 필요하지 않습니다.
- 클래스 로더 계층 구조를 제어할 필요가 없으므로 서블릿 컨테이너 또는 애플리케이션 서버에서 사용하기에 적합합니다.
- 현재 메서드 실행 조인포인트(Spring Bean에서 메서드 실행을 조언)만 지원합니다.
- 핵심 Spring AOP API를 손상시키지 않고 필드 가로채기에 대한 지원을 추가할 수 있지만 필드 가로채기는 구현되지 않습니다.
- 필드 액세스를 Advice하고 조인 포인트를 업데이트해야 하는 경우 AspectJ와 같은 언어를 고려해서 사용합니다.
- AOP에 대한 Spring AOP의 목표는 가장 완전한 AOP구현을 제공하는 것이 아닙니다. 하지만 가능은 합니다.
- 오히려 AOP구현과 Spring IoC간의 긴밀한 통합을 제공하여 엔터프라이즈 애플리케이션의 일반적인 문제를 해결하는 것이 목표입니다.