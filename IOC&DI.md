# 🌈 Spring IOC, Container, DI, Bean?

## IOC (Inversion of Control)
제어의 역전이라 부른다. 아래에서 컨테이너와 함께 설명한다.

## Container
컨테이너는 보통 객체의 생명주기, 생성된 인스턴스들에게 추가적인 기능을 제공한다. 스프링 컨테이너는 의존성도 관리한다.

## Spring IOC Container - 스프링 IOC 컨테이너
스프링은 스프링 IOC 컨테이너에서 제어 권한을 가져 객체 생성, 관계, 의존성, 생명주기 관리 하는데 이때 생성된 객체를 스프링 Bean이라고 한다.

이 Bean들은 싱글톤으로 관리된다.

즉, 개발자는 이런 과정을 스킵 함으로써 비즈니스 로직에 집중할 수 있게 된다.

그렇다면 우리가 만든 클래스를 스프링 IOC 컨테이너가 관리할 수 있게 하려면 어떻게 할까? 바로 Bean으로 등록해 주면 된다. Bean으로 등록하는 방법은 여러 가지 방법이 있는데 예전에 사용하던 XML을 통해 등록하는 방법을 제외하고 어노테이션을 통해 등록하는 2가지 방법을 확인해 보자.
 
## 1. Bean으로 등록하는 방법
### 1-1. Component Scan
Bean으로 등록될 준비가 된 클래스들을 스캔하여 Bean으로 등록해 주는 과정이다.

준비가 된 클래스들이란 @Component 어노테이션을 클래스에 추가한 것을 말한다. 많이 사용하는 @Controller, @Service, @Repository도 따라가 보면 @Componet이 있는 걸 확인할 수 있다.

그렇다면 이제 하나 더 궁금증이 생긴다. 나는 컴포넌트 스캔을 한 적이 없는데 왜 위의 어노테이션만 붙였을 뿐인데 Bean으로 등록된 걸까?

스프링부트 프로젝트를 생성하면 기본적으로 ~Application 클래스가 생성되는데 이 클래스에는 @SpringBootApplication 어노테이션이 있는데 그 안을 살펴보면 @ComponentScan 어노테이션을 통해서 해당 클래스를 기준으로 하위 패키지를 스캔하는 걸 알 수 있다.
 
### 1-2. Java config - @Configuration, @Bean
@Configuration 클래스에서 @Bean 어노테이션을 사용해 수동으로 스프링 컨테이너에 빈을 등록하는 방법이다.

```java
@Configuration
public class TestConfig {
    @Bean
    public OpenApi openApi() {
        return new OpenApi();
    }
} 
```

위와 같이 수동으로 Bean을 등록하는 경우에는 주로 다음과 같을 때 사용한다.
1. 개발자가 직접 제어가 불가능한 라이브러리를 빈으로 등록하여 사용할 때
2. 전범위적으로 사용되는 클래스를 등록할 때
3. 다형성을 활용하여 여러 구현체를 등록해주어야 할 때

## 2. DI(Dependency Injection) - 의존성 주입
Bean으로 등록하고 스프링 IOC 컨테이너에 의해 생성도 되었다면, 이제 의존성 주입을 통해 사용할 수 있는데 의존성 주입에는 여러 가지 방법이 있다. 차례대로 확인해 보자.
### 2-1. 필드 주입
```java
@Controller
public class TestController {
    @Autowired
    private TestService testService;
}
```
### 2-2. 수정자(Setter) 주입
```java
@Controller
public class TestController {

    private TestService testService;

    @Autowired
    public void setTestService(TestService testService) {
        this.testService = testService;
    }
}
```
### 2-3. 생성자 주입
```java
@Controller
public class TestController {

    private final TestService testService;

    public TestController(TestService testService) {
        this.testService = testService;
    }
}
```

다만, 필드나 Setter 메서드에서 주입을 사용하는 것보다 생성자 주입 방법이 권장된다. 그 이유는 아래와 같다.
1. 순환 참조 방지 A가 B를 참조하고, B가 다시 A를 참조하는 문제
2. 불변성(Immutability)
생성자로 의존성을 주입할 때 final로 선언할 수 있고, 런타임에서 의존성을 주입받는 객체가 변할 일이 없어지게 된다. 또, 필드 주입 방식은 null이 만들어질 가능성이 있는데 final로 선언한 생성자 주입 방식은 null이 불가능하다.

### Reference
- https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-introduction
