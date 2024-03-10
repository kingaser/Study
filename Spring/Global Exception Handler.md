## Spring Exception Handling / Global Exception Handler
- @Exception 어노테이션
- @ControllerAdvice, @RestControllerAdvice 어노테이션
- Global Exception Handling(전역 에ㅚ 처리) 전략
- Enum을 이용하여 에러 코드 및 메시지 관리하기

### Spring Exception Handling
- 스프링은 일관성 있는 코드 스타일을 유지하면서 Exception을 처리할 수 있도록 막강한 어노테이션을 제공하고 있습니다.
- @ControllerAdvice, @RestControllerAdvice, @ExceptionHandler

### @ExceptionHandler 어노테이션
- @ExceptionHandler는 Controller 계층에서 발생하는 에러를 잡아서 메서드로 처리해주는 기능입니다.
- Controller 클래스안에 메서드로 정의하거나, @ControllerAdvice, @RestControllerAdvice가 명시된 클래스의 메서드로 정의할 수 있습니다.
- @ExceptionHandler의 설정 값에 어떤 Exception을 처리할 것인지 정의할 수 있습니다. 값을 설정하지 않는 경우 모든 Exception을 잡게 됩니다.
- Service나 Repository에서 발생하는 에러는 처리하지 않습니다.

### @ControllerAdvice, @RestControllerAdvice 어노테이션
- 해당 어노테이션은 컨트롤러를 보조하는 클래스로 @Controller, @RestController가 명시된 클래스에서 Exception이 발생되면 이를 감지하고 해당 클래스에서 예외 처리를 할 수 있습니다.
- 프로젝트 전역에서 발생하는 Exception을 잡기위한 클래스입니다.
- Global 예외 처리 및 특정 package/Controller 예외 처리를 합니다.
- advice 클래스를 따로 만들어 정의합니다.
- basePackage : 패키지경로 설정으로 해당 패키지 하위에 있는 클래스의 예외만 처리할 수 있습니다.
- annotation : RestController.class 설정으로 @RestController 어노테이션을 명시한 클래스의 예외만 처리할 수 있습니다.

### Global Exception Handling(전역 예외 처리)전략
- Controller 진입시 Spring Validation 기능을 사용하여 데이터 유효성 검사를 할 수 있습니다.
- 이때 유효성 검사에 실패한 경우 MethodArgumentNotValidException이 발생하게 됩니다.
- Controller에서 BindingResult 객체를 파라미터로 받게되면 예외가 발생하지 않고, Controller에서 Validation에 대한 결과를 처리할 수 있지만, 모든 요청마다 코드를 넣어주는 것은 가독성이 떨어지며 Validation 처리에 대한 수정이 일어날 경우 모든 코드에 수정을 해야합니다.
- 때문에 Controller에서 처리하지 않고, 예외를 발생시키고 @ControllerAdvice 어노테이션을 이용하여 예외에 대한 처리를 한다면 데이터 유효성 검사 실패에 대한 처리를 한 곳에서 할 수 있습니다.
- @ExceptionHandler 어노테이션으로 Controller 계층에서 발생하는 에러들을 메서드로 관리하여 처리할 수 있습니다.
- @ControllerAdvice나 @RestControllerAdvice로 특정 패키지 하위 Controller에서 발생하는 모든 예외를 다른 클래스에서 하나로 전역 예외 처리를 할 수 있습니다.
---
- Validation용 DTO 객체 ex) SampleDto.class
- 예외 발생시 공통된 형식으로 반환하기 위한 DTO 객체 ex)ErrorResponse.class
- 전역으로 예외를 잡기위한 핸들러 클래스 ex)GlobalExceptionHandler.class
- @ControllerAdvice : 특정 패키지 하위 Controller에서 발생하는 예외를 감지하여 해당 클래스에서 예외를 처리할 수 있습니다.
- @ExceptionHandler : 특정 Exception을 지정하여 해당 예외가 발생시 메서드로 처리할 수 있습니다.
- Enum을 사용하여 에러의 종류를 지정하고, 상태코드와 에러 메시지를 관리합니다.

### CustomException 클래스
- RuntimeException을 상속받아서 Unchecked Exception으로 활용합니다.
- 비즈니스 로직에서 실패 처리할 때 CustomException 예외를 발생시켜 응답을 GlobalExceptionHandler에서 공통으로 처리합니다.
- throw new CuntomException(ErrorCode.INVALID_INPUT_VALUE); 처럼 throw 키워드로 예외를 던져서 GlobalExceptionHandler에서 처리하도록 사용합니다.

### ErrorResponse 클래스
- 예외 발생시 공통된 형식으로 에러를 반환하기 위한 DTO 클래스 입니다.(클래스 이름이 꼭 ErrorResponse가 아니어도 됩니다.)

### GlobalExceptionHandler 클래스
- @ControllerAdvice : 프로젝트 전역에서 발생하는 모든 예외를 처리하는 클래스입니다.
- @ExceptionHandler : 특정 예외를 지정하여 하나의 메서드에서 공통으로 처리할 수 있게 합니다.
