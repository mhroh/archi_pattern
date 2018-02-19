# Microservices Architecture Pattern

[Basic Microservice Architecture](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/ch04.html)
## Pattern Description
- SOA(Service Oriented Architectures) 및 Monolithic 구조에 대한 대안으로
떠오르고 있는 구조 (Microservices pattern이 Monolithic 한 개발론(Layered Pattern)
 및 Distributed pattern(SOA)을 보완하기 위해 나타남.)
    - [Monolithic](https://blog.knoldus.com/2018/01/03/monolithic-v-s-microservices/) :
     각 Component가 하나로 묶여있는 형태로 되어 구현하는 설계론이며 변경, 테스트, 적용
     등이 어렵다는 단점이 있다.
    - SOA : 가장 강력하고, 평행하지 않은 수준의 추상화 및 다양한 연결성을 제공하나
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
- [Application REST-based topology](https://pt.slideshare.net/AssafGannon/software-architecture-patterns):
    - User Interface Layer라는 web-base 또는 fat-client를 통해 각 Reqeust들이
    아래의 Service Component 들과 연동을 한다. 또한 API REST-based topology와는
    다르게 Service Compnent 들이 큰 규모로 개발이 되며, 좀더 큰 느슨한 경계로 기능이
    나뉘어져 개발이 된다.
- [The Centralized messaging topology](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/ch04.html):
    - 이 Pattern의 경우는 REST-Based topology와 비슷한 점이 많으나, User Interface
    Layer 와 Service Component 사이에 Lightweight Message Broker(ActiveMQ, HornetQ, etc..)
    가 존재를 하며, 이를 통해 메시지 queuing(비동기적 메시지 처리), 에러 처리, 메시지 처리 로드
    분산등을 구현하게 된다.

##
