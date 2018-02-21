# Microservices Architecture Pattern

[Basic Microservice Architecture](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/ch04.html)
## Pattern Description
- SOA(Service Oriented Architectures) 및 Monolithic 구조에 대한 대안으로
떠오르고 있는 구조 (Microservices pattern이 Monolithic 한 개발론(Layered Pattern)
 및 Distributed pattern(SOA)을 보완하기 위해 나타남.)
    - [Monolithic](https://blog.knoldus.com/2018/01/03/monolithic-v-s-microservices/) :
     각 Component가 하나로 묶여있는 형태로 되어 구현하는 설계론이며 변경, 테스트, 적용
     등이 어렵다는 단점이 있다.
    - [SOA](https://ko.wikipedia.org/wiki/%EC%84%9C%EB%B9%84%EC%8A%A4_%EC%A7%80%ED%96%A5_%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98) : 가장 강력하고, 평행하지 않은 수준의 추상화 및 다양한 연결성을 제공하나
    복잡성, 고비용, 개발하기 어려운 환경을 만드는 설계론.
- 각 Service Component 단위로 기능상으로 분리, 적용되어 개발의 효율성, 확장을
쉽게 함.(Layered Pattern, Monolithic Pattern의 단점을 개선)
    - Service componet : 다른 Component들에 영향을 주지않는 기능 별로 나뉘어
    개발이 진행되어 독립적으로 적용 및 동작 가능한, module들의 집합을 의미.
- 각 Service Component 간의 기능들은 서로 RMI, REST등의 원격 접속 프로토콜을
이용하여 서로 통신하게 되도록 개발이 되며 이를 통해 분산처리 환경을 구성한다.

## Pattern Topologies
- Microservice Architecture 에는 12가지 정도의 topology가 존재를 하는데 그 중
두드러지게 유용성을 보이는 것들은 아래와 같다.
- [The API REST-based topology](https://www.slideshare.net/RiccardoCardin/software-architecture-patterns-59866690):
    - API(Application Programming Interface)를 거쳐 각 요청들이 해당
    Service Component 의 기능들과 rest 형식으로 통신을 하게 된다.
    - 각 Service Component 가 다루게 되는 서비스의 범위는 매우 세부적으로 나뉘어진다.
- [Application REST-based topology](https://pt.slideshare.net/AssafGannon/software-architecture-patterns):
    - User Interface Layer라는 web-base 또는 fat-client를 통해 각 Reqeust들이
    아래의 Service Component 들과 연동을 한다.
    - API REST-based topology와는 다르게 Service Compnent 들이 큰 규모로
    개발이 되며, 좀더 큰 느슨한 경계로 기능이 나뉘어진다.
- [The Centralized messaging topology](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/ch04.html):
    - 이 Pattern의 경우는 REST-Based topology와 비슷한 점이 많으나, User Interface
    Layer 와 Service Component 사이에 Lightweight Message Broker(ActiveMQ, HornetQ, etc..)
    가 존재를 하며, 이를 통해 메시지 queuing(비동기적 메시지 처리), 에러 처리, 메시지 처리 로드
    분산등을 구현하게 된다.

## Avoid Dependencies and Orchestration
- 각 Service Component 를 나누는 기준을 정하는 것이 매우 중요함.
    - 너무 크게 서비스를 나누게 된다면 Microservices Architecture Pattern 의 장점을
잘 활용할 수 없음(서비스 모듈간의 강결합의 발생, 확장 및 테스트하기가 어려워짐).
    - 너무 세부적으로 나뉘게 되면 SOA 의 단점인 Orchestration의 필요성, 복잡성, 혼잡성 등이 발생하게 됨.
- 각 Service Component 들의 독립성을 지키기 위해서 각 Service Component 개발시에는
반복적으로 필요로하는 function 들이 존재하게 된다. 이는 거의 필수적으로 발생하게 되는 문제이다.
- 만약 Service Component 를 적당한 기준으로 나누어 개발을 진행할 때 여전히 Service component orchestration
이 필요하다면 이 패턴이 개발중인 서비스에 적합하지 않다는 증거가 됨.
    - Orchestration 상에서는 각 Component간의 transcation이 발생을 하는데 이를 rollback 하는 등의 복잡성이 필수적으로 나타나게 되므로 이는 Application의
복잡도를 높이게 됨.

## Consideration
- SoA 와 Monolitic Pattern의 단점을 보완하기 위해 나온 Microsrvice Pattern은
각 Service component를 세부적으로 나뉘기 때문에 다른 Pattern에 비해 강건하고, 확장이
용이한 특성을 제공한다.
- 특히 운용중 새로운 기능의 적용 및 확장을 가능하게 하는 구조이다.
- Microservices Pattern의 경우 분산처리 패턴이므로 Event Driven 과 같은
복잡성, 인증문제 등의 문제점을 가지게 된다.

## Pattern Ananlysis
- Overall agility : High
- Easy Deployment : High
- Testability : High
- Performance : Low
- Scalability : High
- Ease of developement : High
