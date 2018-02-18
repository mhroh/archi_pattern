# Microservices Architecture Pattern

[Basic Microservice Architecture](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/ch04.html)
## Pattern Description
- SOA(Service Oriented Architectures) 및 Monolithic 구조에 대한 대안으로
떠오르고 있는 구조 (Microservices pattern이 Monolithic 한 개발론(Layered Pattern)
 및 Distributed pattern(SOA)을 보완하기 위해 나타남.)
    - Monolithic :
    - SOA : 가장 강력하고, 평행하지 않은 수준의 추상화 및 다양한 연결성을 제공하나
    복잡성, 고비용, 개발하기 어려운 환경을 만드는 Architecture.
    (**SOA의 Orchestration 이란?**)
- 각 Service Component 들이 기능상으로 분리, 적용되어 개발의 효율성, 확장을
쉽게 함.
    - Service componet : 하나의 기능만을 제공하는 module을 가지고 있는 것 부터
    시작하여 하나의 application 수준에 해당하는 module들을 가지고 있는
- 각 Service Component 간의 기능들은 서로 결합되지 않는 형태로 존재하며, 이들은
RMI, REST등의 원격 접속 프로토콜을 이용하여 서로 통신하게 되어 분산처리 환경을
구성한다.

