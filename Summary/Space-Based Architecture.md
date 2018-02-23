# Space-Based Architecture

[Space-Based Architecture](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0501.png)
- WebServer, Application Server, Database layer로 이루어진
Web-Based Business appliction 에서 발생하는 scalability, concurrency를
처리하는 것에 특화된 Architecture.
- [Web-Based Buiness Example](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)

## Pattern Description
- Cloud Architecture Pattern 이라고도 불리움
- Database에 data가 집중되는 현상을 제거하고, data를 data-grid의 메모리 상에
저장 및 복제하여 동시성을 해결함.
- 사용자 load의 증가, 감소에 따라 Processing unit을 증가 감소 시켜 scalability 문제를
해결함.
- 이 패턴에 적합한 Application은 표준적인 websites 임 (Auction, Yahoo, 등)
### Space-Based Architecture의 주요 Components
[Typical Processing Unit](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0502.png)
- Processing Unit
    - Web-Based component 및 Backend business 로직을 담고 있는 Unit
    - Application type 및 규모에 따라 Processing Unit의 구조 및 크기는 다양하다.
    - Processing Unit은 In Memory Data grid 및 failover를 위한 Persistent store,
    Replication engine 등으로 구성되어 짐.

- Virtualized middleware
    - Data 동기화, Data 복제 및 분산 Request 처리 및 Process-Unit 적용을 위한
    Component
    - Messaging Grid, Data grid, processing grid, deployment mananger 등으로
    구성됨.
    - [Messaging Grid](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0503.png)
        - Request 및 Session 정보를 관리
        - Request에 대해 어떤 Processing Unit으로 전달할 지 결정을 하고 해당 Request의
        Session을 관리
    - [Data Grid](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0504.png)
        - 가장 중요한 component
        - Data에 변경사항이 발생할 경우 Process Unit 상에 있는 Data Replication engine과
        연동을 하여 Data 복제를 진행.
        - Messageing Grid가 Request를 현재 동작 중인 Process Unit 상으로 랜덤하게 보낼 수
        있으므로 Data 복제 및 동기화는 필수적인 요소.
    - [Processing Grid](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0505.png)
        - 필수적으로 필요한 Component는 아님
        - 다수의 Processing Unit이 있을 경우 분산된 요청 처리를 관리하기 위해 존재
        - 요청이 두 Processing Unit 상에서 교환되고 처리 될 때 Processing Grid
        가 이를 조율한다.
    - Deployment Manager
        - Processing Unit의 동적인 적용 및 중단을 책임지는 Component
        - Useer Load 를 지속적으로 검사하여 Processing Unit의 증가 및 감소를 결정.
## Consideration
- 매우 복잡하고 고비용의 pattern
- 작은 규모의 웹기반의 application에 적합한 pattern(Social media sites, Auction등)
- 큰 규모의 관계형 데이터베이스 application에는 적합하지 않음
- 변동이 없는 data와 통신상에 사용되는 데이터는 서로 격리를 시켜야 메모리 사용을 줄일 수
있음.
## Pattern Analysis
- Overall Agility : High
- Ease of deployment : High
- Testability : Low
- Performance : High
- Scalability : High
- Ease of development : Low






