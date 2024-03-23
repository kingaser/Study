## TDD(Test-Driven Development)
- 테스트 주도 개발
- 소프트웨어 개발 방법론 중의 하나
- 선 개발 후 테스트 방식이 아닌 선 테스트 후 개발 방식의 프로그래밍 방법
- 작은 단위의 테스트 케이스를 작성하고 이를 통과하는 코드를 추가하는 단계를 반복하여 구현
- 짧은 개발 주기의 반복에 의존하는 개발 프로세스
- 애자일 방법론 중 하나인 eXtream Programming(XP)의 Test-First 개념에 기반을 둔 단순한 설계를 중요시 함

### TDD 개발 주기
![image](https://github.com/kingaser/Study/assets/104209781/b537925c-2bc6-4259-b53b-f98872660d0e)
- Red 단계에서 실패하는 테스트 코드를 먼저 작성
- Green 단계에서 테스트 코드를 성공시키기 위한 실제 코드 작성
- Blue 단계에서 중복 코드 제거, 일반화 등의 리팩토링 수행

- 중요한 것은 실패하는 테스트 코드를 작성할 때까지 실제 코드를 작성하지 않는 것과, 실패하는 테스트를 통과할 정도의 최소 실제 코드를 작성해야 하는 것
- 이를 통해 실제 코드에 대해 기대되는 바를 보다 명확하게 정의함으로써 불필요한 설계를 피할 수 있고, 정확한 요구 사항에 집중 가능

### TDD를 이용한 개발 방법
1. 테스트 케이스 작성
  - 만들고 싶은 기능을 점검할 테스트 코드 작성
  - 이때, 아직 기능 코드를 구현하지 않았으므로 테스트 결과는 실패로 반환
  - 실패하는 테스트를 가장 빠르게 구현하는 방법은 아무 값이나 반환하도록 하는 것

2. 테스트 케이스를 통과하는 코드 작성
  - 테스트 코드를 만족시킬 수 있는 기능을 구현
  - 테스트 통과를 최우선으로 생각하며 작업
  - 단위 테스트를 통과할 수 있을 정도의 최소한의 코드만 작성

3. 작성한 코드 리팩토링
  - 기능의 성능이 향상되며, 재사용성이 좋고, 가독성이 좋은 코드로 기능 코드를 개선
  - 테스트 코드를 통해 다시 기능 코드를 점검
  - 기능 테스트가 완전해질 때까지 2, 3의 과정을 반복

- 요약
  - 테스트 케이스와 테스트 코드 작성
  - 테스트 코드가 개발을 주도하기 위해서 반드시 실패를 포함하는 테스트 코드의 작성이 앞서야 함
  - 테스트 케이스를 통과하는 코드 작성
  - 작성된 코드는 개선될 수 있는 많은 여지를 포함한 코드
  - 리팩토링 단계에서 이를 개선
---
TDD는 기본적으로 위 3단계를 반복으로 진행하며 점진적으로 개발이 진행됩니다. 필요한 기능에 대한 테스트 코드를
먼저 작성한 후 테스트를 통과하도록 코드를 작성하는 것입니다.

### 장점
1. 객체 지향적인 코드 개발
  - TDD는 코드의 재사용 보장을 명시하므로 TDD를 통한 소프트웨어 개발 시 기능별로 모듈화가 이루어짐
  - 의존성과 종속성이 낮은 모듈로 조합된 소프트웨어 개발을 가능하게 함
  - 필요에 따라 모듈을 추가하거나 제거해도 소프트웨어 전체 구조에 영향을 미치지 않게 됨

2. 디버깅 시간을 단축 할 수 있음
  - 단위(Unit) 테스팅을 하는 이점이기도 함
  - 예를 들면 사용자의 데이터가 잘못 나온다면 DB의 문제인지, 비즈니스 레이어의 문제인지 UI의 문제인지 실제 모든 레이어들을 전부 디버깅해야 함
  - TDD의 경우 자동화된 유닛 테스트를 전재하므로 특정 버그를 손쉽게 찾아낼 수 있음

3. 코드가 내 손을 벗어나기 전에 가장 빠르게 피드백 받을 수 있음
  - 개발 프로세스에서는 보통 인수 테스트를 함
  - 이미 배치된 시스템을 대상으로 클라이언트가 의뢰한 소프트웨어가 사용자 관점에서 사용할 수 있는 수준인지 체크하는 과정임
  - 이미 90% 이상 완성된 코드를 가지고 테스트하기 때문에, 문제를 발견해도, 정확하게 원인이 무엇인지 진단하기 힘듦
  - TDD를 사용하면 기능 단위로 테스트를 진행하기 때문에 코드가 모두 완성되어 개발자의 손을 떠나기 전에 피드백을 받는 것이 가능

4. 작성한 코드가 가지는 불안정성을 개선하여 생산성을 높일 수 있음
  - TDD는 불안함을 지루함으로 바꾸는 마법의 돌(켄트 백)
  - TDD를 사용하면, 코드가 내 손을 떠나 사용자에게 도달하기 전에 문제가 없는지 먼저 진단 받을 수 있음
  - 그러므로 코드가 지닌 불안정성과 불확실성을 지속적으로 해소해줌

5. 설계 수정시간의 단축
  - 테스트 코드를 먼저 작성하기 때문에 최초 설계안을 만족하게 함
  - 입출력 구조와 기능의 정의를 명확하게 하게 되므로 설계의 구조적 문제를 바로 찾아낼 수 있음
    
6. 유지보수(리팩토링)의 용이성
  - 기본적으로 단위 테스트 기반의 테스트 코드를 작성하기 때문에 추후 문제가 발생하였을 때 각각의 모듈별로 테스트를 진행해보면 문제의 지점을 쉽게 찾을 수 있음
    
7. 테스트 문서의 대체 가능
  - 대부분의 개발 프로젝트에서 테스트를 진행하는 경우 단순 통합 테스트에 지나지 않음
  - TDD를 하게 될 때 테스팅을 자동화시킴과 동시에 더욱 정확한 테스트 근거를 산출해 정의서를 작성할 수 있음

### 단점
1. 생산성 저하
  - 프로젝트를 진행할 때 경험 때문에 어떤 예외상황이 발생할지 눈에 뻔히 보이는 경우가 종종 있음
  - 이러한 단발성 개발은 개발 기간이 타이트하게 잡히는 경우가 많음
  - 이러한 경우 TDD를 이용해 테스트 코드를 작성하고 그에 통과하기 위한 코드를 작성한다면 비효율적일 것임
    
2. 사전준비 기간
  - TDD를 프로젝트에 도입하려면 사전에 필요한 지식을 습득하고 개발 환경을 구축해야 함
  - TDD를 효과적으로 사용할 수 있는 수준으로 개발자를 교육하는 데 보통 1~6개월의 시간이 필요함

3. 구조에 얽매임
  - TDD로 프로젝트를 진행하면서 어려운 예외가 생길 수 있는데 그것 때문에 고민의 순간이 찾아오게 됨
  - 원칙을 깰 수는 없고 꼼수가 있기는 한데 그 꼼수를 위해서 구조를 바꾸자니 이건 아무래도 아닌 것 같고
  - 테스트는 말 그대로 테스트일 뿐 실제 코드가 더 중요한 상황인데도 불구하고 테스트 원칙 때문에 쉽게 넘어가지 못하는 그런 경우

### 좋은 TDD의 특징(FIRST 규칙)
- Fast : 테스트는 빠르게 동작하여 자주 돌릴 수 있어야 한다.
- Independent : 각각의 테스트는 독립적이며 서로 의존해서는 안된다.
- Repeatable : 어느 환경에서도 반복할 수 있어야 한다.
- Self-Validating : 테스트는 성공 또는 실패로 bool 값으로 결과를 내어 자체적으로 검증되어야 한다.
- Timely : 테스트는 적시에 즉, 테스트하려는 실제 코드를 구현하기 직전에 구현해야 한다.