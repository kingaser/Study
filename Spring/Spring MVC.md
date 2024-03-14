## Spring MVC
- Spring에서 제공하는 웹 모듈로, Model, View, Controller 세 가지 구성요소를 사용해 사용자의 다양한 HTTP Request를 처리하고
단순한 텍스트 형식의 응답부터 REST 형식의 응답은 물론 View를 표시하는 html을 return하는 응답까지 다양한 응답을 할 수 있도록 하는 프레임워크입니다.

- Spring MVC는 다양한 요청을 처리하고 응답하기 위해 주요 구성 요소들을 만들어 놓고 구성요소들을 확장할 수 있게 만들어 놓는데,
이들을 제대로 사용하기 위해서는 MVC가 어떻게 구성되어 있는지를 알아야 합니다.

### 구조
- Spring MVC의 주요 구성요소는 Model, View, Controller지만, 이들이 유기적으로 동작하도록 하기 위해 다양한 구성요소가 함껳합니다.

- DispatcherServlet(Front Controller)
- Handler(Controller)
- ModelAndView
- ViewResolver

MVC 프레임워크 구조
![image](https://github.com/kingaser/Study/assets/104209781/a740ba85-b87b-43ae-a208-eb46f0089a2c)

Spring MVC 구조
![image](https://github.com/kingaser/Study/assets/104209781/b3fd115e-bae3-4d68-b7cf-33ebaf313100)

명칭은 다르지만 구조는 같습니다.

- FrontController -> DispatcherServlet
- handlermappingMap -> Handlermapping
- MyHandlerAdapter -> HandlerAdapter
- ModelView -> ModelAndView
- viewResolver -> ViewResolver
- MyView -> View

### 동작 순서
1. 클라이언트로 부터 HTTP 요청이 들어오면 DispatcherServlet이 요청을 받습니다.
2. DispatcherServlet은 받은 요청을 핸들러 매핑을 통해 URL에 매핑된 핸들러(Controller)를 조회합니다.
3. 핸들러(Controller)를 실행할 수 있는 핸들러 어댑터를 핸들러 어댑터 목록에서 조회합니다.
4. 조회된 핸들러 어댑터를 DispatcherServlet이 핸들러 어댑터에 보내 실행합니다.
5. 핸들러 어댑터는 핸들러(Controller)를 통해 실행합니다.(실제 실행)
6. 핸들러 어댑터는 핸들러가 반환하는 정보를 DispatcherServlet으로 보내고 이 과정에서 ModelAndView가 생성되어 반환됩니다.
7. ModelAndView를 받은 DispatcherServlet은 viewResolver를 호출합니다. JSP의 경우 InternalResourceViewResolver가 자동 등록되어 사용됩니다.
8. viewResolver는 View를 찾아 반환합니다. JSP의 경우 InternalResourceView(JstlView)를 반환하는데, 내부에는 forward()가 있습니다.
9. DispatcherServlet은 반환받은 View를 View를 통해 렌더링하고 응답합니다.

### DispatcherServlet 구조
DispatcherServlet도 부모 클래스에서 HttpServlet을 상속받아 사용하며 서블릿으로 동작합니다.
- DispatcherServlet -> FrameworkServlet -> HttpServletBean -> HttpServlet

- 스프링 부트 구동 시 DispatcherServlet을 서블릿으로 자동등록하며 모든 경로에 대해 매핑합니다.
- Spring MVC역시 프론트 컨트롤러 패턴으로 구현되어 있고 DispatcherServlet이 프론트 컨트롤러의 역할을 한다고 생각하면 됩니다.

### DispatcherServlet
- 제일 앞단에서 HTTP Requset를 처리하는 Controller 입니다.
- Spring MVC에서는 HTTP Request가 왔을 때 DispatcherServlet이라 불리는 서블릿이 HTTP Requset를 처리할 Controller를 지정합니다.
- DispatcherServlet은 일종의 HTTP Request를 처리할 Controller를 지정하는 Controller로 Super Controller 역할을 합니다.

### Controller(Handler)
- HTTP Request를 처리해 Model을 만들고 View를 지정합니다.
- DispatcherServlet에 의해 배정된 Controller는 HTTP Reqeust를 처리하고, HTTP Request의 메시지를 처리해 필요한 데이터를 뽑아 Model에 저장합니다.
- 또한 HTTP Request에 따라서 HTTP가 보여줄 View Name을 지정합니다.
- 이곳에서 View Name 뿐만 아니라 직접 View를 반환할 수도 있습니다.
- 하지만 이곳에서 View에 Model의 데이터를 세팅하지는 않습니다.

ModelAndView : Controller에 의해 반환된 Model과 View가 Wrapping된 객체. 내부에는 View 혹은 View Name이 있는데, View가 지정되더라도 데이터가 세팅된 View가 지정되지는 않습니다.
Model : Map<String, Value> 형태의 데이터 저장소
Model은 Map자료 구조로, HTTP Request 속의 데이터를 파싱해 Key-Value 쌍으로 만들어 저장합니다. 이 Model은 이후에 View를 그리기 위해 사용됩니다.

### ViewResolver
- ModelAndView를 처리하여 View를 그립니다.
- ViewResolver 에서는 ModelAndView 객체를 처리해 View를 그립니다.
- 여기서는 모델에 저장된 데이터를 사용해 View를 그려줍니다.
- View는 사용자에게 보여줄 완성된 View이며, 여기서 그려지는 View는 그대로 유저에게 반환됩니다.
- 우리가 특정한 url로 들어갔을 때 우리에게 보여지는 View가 바로 이곳에서 만들어지는 View입니다.

---
Spring MVC는 HTTP Request를 처리하는 부분인 Controller, 데이터를 처리해 정제된 데이터를 넣는 Model, 정제된 데이터를 활용해 사용자에게 보여지는 View에 대한 역할 분리를 잘 해놓았습니다.
Spring MVC를 사용하면 Model, View, Controller 모두를 인터페이스를 사용해 규격화해놓아 유연하고 확장성 있게 웹 애플리케이션을 설계할 수 있습니다.
