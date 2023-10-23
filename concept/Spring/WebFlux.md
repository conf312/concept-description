## WebFlux의 등장

WebFlux는 논블로킹으로 동작하는 웹 스택의 필요성 때문에 등장하게 되었다. 기존 SpringMVC의 Servlet API는 v3.1부터 논블로킹을 위한 API를 제공했었다. 하지만 이외의 동기적으로 처리하는 모듈(Filter, Servlet)과 블로킹 방식의 API(getParameter, getPart)들이 있기에 완벽한 논블로킹 환경의 개발을 할 수 없었으며, 비동기 논블로킹 환경의 서버로 Netty가 부상하고 있었으며 이 Netty와의 연동을 위해 Spring은 새로운 API가 필요했다.

## Spring WebFlux는 아래와 같은 사용에 추천
- 비동기, non-blocking reactive 개발
- 효율적으로 동작하는 고성능 웹어플리케이션 개발
- 서비스간 호출이 많은 마이크로서비스 아키텍처
- 일반적으로 blocking 코드 작성에는 익숙하기 때문에 생산성이 높을 것이나 non-blocking 코드에는 익숙하지 않고 확실히 이해하고 코딩하지 않으면 알 수 없는 오류도 발생하기 쉽고 디버깅도 어렵기 때문에 학습이 필요하다. 그리고 non-blocking과 blocking 코드를 같이 사용하게 되면 비동기 코드가 무의미해지고 성능적인 이점도 볼 수 없기 때문에 고려해야할 부분도 많다.

## Spring MVC vs WebFlux

### Spring MVC와 WebFlux의 공통점
@Controller, Reactive클라이언트이다. 둘 모두 Tomcat, Jetty, Undertow와 같은 서버에서 실행할 수 있다. (Spring PSA)    

### Spring MVC, 명령형 논리, JBDC, JPA
Spring MVC는 하나의 요청에 대해 하나의 스레드가 사용된다(thread-per-request). 그래서 다량의 요청을 대비해 미리 스레드 풀을 생성해놓으며, 각 요청마다 스레드를 할당하여 처리한다.

### Spring WebFlux
에서는 기능적 엔트 포인트, 이벤트 루프, 동시성 모델을 가질 수 있다.


### 장점:
- 비동기적인 방식으로 동작하여 높은 확장성과 처리량을 제공합니다.
- Reactor 라이브러리를 사용하여 함수형 프로그래밍을 지원하므로 코드의 가독성이 높아집니다.
- Non-blocking I/O 모델을 사용하여 더 많은 클라이언트를 동시에 처리할 수 있습니다.
- WebSockets와 같은 양방향 통신을 지원합니다.
- 서버와 클라이언트 간의 지속적인 연결에 대한 처리를 쉽게 할 수 있습니다.

### 단점:
- 기존의 Servlet API와 다르기 때문에 학습 곡선이 높을 수 있습니다.
- 리액티브한 프로그래밍 방식을 사용하므로 기존의 스프링 MVC와 같은 방식으로 개발하기 어렵습니다.
- 서버 사이드 렌더링을 지원하지 않습니다.
- RxJava와 같은 비슷한 라이브러리가 이미 있기 때문에 선택하는 것이 어려울 수 있습니다.
- 멀티 쓰레드 환경에서의 동작에 대한 이해가 필요합니다.