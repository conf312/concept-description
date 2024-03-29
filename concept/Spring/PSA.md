## PSA(Portable Service Abstraction)란?
서비스의 기능에 접근하는 방식을 일관되게 유지하면서 기술 자체를 유연하게 사용할 수 있도록 하는 것을 PSA(일관된 서비스 추상화)라고 한다.
즉, PSA가 적용된 코드는 나의 코드가 바뀌지 않고, 다른 기술로 바꿀 수 있도록 확장성이 좋고, 어떤 기술에 특화되어 있지 않는 코드를 의미한다.

### 대표적인 예로 Spring의 MVC, Transactional, Cacheable가 있다.

## Transactional
@Transactional을 예로 들면, 어떤 데이터베이스를 선택하더라도 트랜잭션 기능을 사용할 수 있는것처럼, 이러한 기능을 가능하게 해주는 개념이 PSA(일관된 서비스 추상화)라고 한다.

이게 가능한 이유는 PlatformTransactionManager이라는 최상위 Manager를 사용하고, 각각 사용자의 선언에 따라서 JPATransactionManger, DatasourceTransactionManager, HibernateTransactionManger 등을 상황에 맞게 의존성 주입을 받아 사용하게 만들어졌기 때문이다.

## Spring MVC
기본적으로 Servlet 기반의 Application을 활용하지만, 개발자는 Spring framework를 사용하면 Servlet을 직접적으로 코딩할 일이 거의 없다. 

@Controller, @GET(url) 등의 어노테이션만 활용하게 되면 보이지 않는 곳에서 Spring이 처리해 준다. 

즉, 개발자는 HttpServlet을 구현하여 모든 Mapping에 대해 직접적으로 구현할 일이 없게 Service Abstraction을 통해 편리하게 사용할 수 있는것이다.

---

## GPT 부가 설명
Spring PSA(Portable Service Abstraction)는 스프링 프레임워크의 핵심 개념 중 하나로, 스프링이 제공하는 여러 서비스에 대한 추상화를 의미합니다. PSA는 스프링을 사용하는 애플리케이션 개발자들이 특정 기술이나 환경에 의존하지 않고 일관된 방식으로 프로그래밍할 수 있도록 도와줍니다. 이는 코드의 유지보수성을 높이고, 테스트 용이성을 개선하며, 다양한 환경에서의 이식성을 제공하는 데 기여합니다.

Spring PSA는 주로 다음과 같은 세 가지 추상화 레벨로 구성됩니다.

1. **인프라스트럭처 추상화 (Infrastructure Abstraction)**:
   - **데이터 액세스**: 스프링은 JDBC, JPA, MyBatis 등 다양한 데이터 액세스 기술에 대한 추상화를 제공합니다. 개발자는 특정 데이터베이스 기술에 종속되지 않고 일관된 방식으로 데이터베이스와 상호 작용할 수 있습니다.
   - **트랜잭션 관리**: 스프링은 여러 트랜잭션 매니저를 지원하며, 트랜잭션 관리에 대한 추상화를 제공하여 애플리케이션 코드가 특정 트랜잭션 매니저에 종속되지 않도록 합니다.

2. **메시징 추상화 (Messaging Abstraction)**:
   - **JMS(Java Message Service)**: 스프링은 JMS를 사용하는 메시지 큐 시스템에 대한 추상화를 제공합니다. 이를 통해 애플리케이션은 특정 JMS 구현에 종속되지 않고도 메시지 기반 통신을 구현할 수 있습니다.

3. **리소스 추상화 (Resource Abstraction)**:
   - **파일 시스템, 클래스패스 등**: 스프링은 파일 시스템이나 클래스패스 상의 리소스에 접근하는 방법에 대한 추상화를 제공합니다. 이를 통해 애플리케이션은 특정 환경에 종속되지 않고 리소스를 로드하고 조작할 수 있습니다.

이러한 PSA의 주요 이점은 다음과 같습니다.

- **유연성과 이식성**: PSA를 통해 개발자는 구체적인 기술에 대한 의존성을 낮출 수 있으며, 이는 애플리케이션의 유연성과 이식성을 향상시킵니다.
  
- **테스트 용이성**: PSA를 사용하면 모킹 및 테스트를 용이하게 할 수 있습니다. 각 PSA는 인터페이스를 통해 제공되므로, 해당 인터페이스를 구현하는 모의 객체를 만들어 테스트할 수 있습니다.

- **애플리케이션의 응집성 강화**: PSA는 다양한 기술에 대한 접근 방식을 일관된 방식으로 제공하므로, 애플리케이션의 응집성을 강화하고 유지보수를 쉽게 만듭니다.

Spring PSA는 스프링 프레임워크가 다양한 환경에서의 적응성을 향상시키고 개발자에게 일관된 프로그래밍 모델을 제공하는 데 중요한 역할을 합니다.
