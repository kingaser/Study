## Library VS Framework
### 제어 흐름
- 라이브러리
  - 라이브러리는 개발자가 필요한 기능을 호출하여 사용할 수 있는 코드의 모음
  - 개발자는 필요할 때 마다 라이브러리 함수를 호출하여 원하는 작업을 수행
  - 라이브러리는 개발자가 제어 흐름을 가지며, 개발자가 라이브러리의 함수를 호출하고 그 결과를 처리
- 프레임워크
  - 프레임워크는 개발자가 구체적인 작업 흐름과 구조를 따르도록 정의된 애플리케이션의 기본 구조
  - 프레임워크는 제어 흐름을 이미 정의한 상태로 제공하며, 개발자는 프레임워크 안에서 자신의 코드를 작성하여 프레임워크가 정한 규칙에 따라 동작

### 코드 소유권
- 라이브러리
  - 라이브러리를 사용하는 개발자는 필요한 기능을 호출하여 사용할 수 있지만, 코드의 소유권은 개발자에게 있음
  - 개발자는 라이브러리의 함수를 활용하며 필요에 따라 수정하거나 대체 가능
- 프레임워크
  - 프레임워크는 이미 정의된 구조와 규칙을 갖고 있기 때문에, 개발자는 프레임워크가 정한 방식대로 코드를 작성
  - 코드의 흐름과 구조를 프레임워크에 따라 작성해야 하므로, 코드의 일부분만 개발자가 작성

### 제어 흐름의 역전 (Inversion of Control)
- 라이브러리
  - 라이브러리는 개발자가 호출하여 사용하는 형태이므로, 제어 흐름은 개발자가 가짐
- 프레임워크
  - 프레임워크는 개발자가 정해진 규칙과 구조에 따라 코드를 작성하므로, 제어 흐름이 프레임워크에게 넘어감
  - 이러한 역전된 제어 흐름을 제어 흐름의 역전 이라 함

### 확장성
- 라이브러리
  - 라이브러리는 개발자가 필요한 기능만 선택적으로 사용할 수 있으므로, 더 큰 유연성과 확장성을 제공
- 프레임워크
  - 프레임워크는 이미 정의된 구조에 따라 작성해야 하므로, 프레임워크의 확장성에 따라 개발을 진행

### 요약
- 라이브러리는 개발자가 필요한 기능을 호출하여 사용할 수 있는 도구 모음이며, 프레임워크는 개발자가 정해진 규칙과 구조에 따라 코드를
작성해야 하는 애플리케이션의 기본 구조