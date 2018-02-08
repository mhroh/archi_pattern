# Layered Pattern.
[Layered Pattern](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0101.png)
- 가장 흔하게 사용되는 패턴.
- 각 기능별(Domain)로 나뉘어진 Layer를 층층이 쌓아 놓는 것 처럼 보여
**n-tier pattern** 이라고도 불림.
- 보통 3~5개의 Layer로 구성되며, 각 layer가 가져야 되는 컴포넌트의 갯
수에는 제한이 없음.
    - 3개의 Layer로 설계 될 경우 **client-server** 모델이라고
    불리우기도 함.
    - 4개의 Layer로 구성되는 것이 일반적이며 각 layer의 명칭은
    Presentation, Bussiness, Persistence, Database 이다.
- 각 Layer는 서로의 위 또는 아래에 수평하게 위치하게 된다.
## Key Concept
### Separation of concerns:
- 각 Layer에 속한 컴포넌트들은 자신이 속한 layer의 로직과 역활에만 집중
하게 된다.
    - Presentation Layer는 사용자에게 정보를 보여주거나, 요청을 받아
    Business Layer로 전달 및 응답받는 역활만을 수행하는 등 각 layer마다
    정해진 로직 구현 및 수행하는 것에만 집중을 한다.
    - 이러한 특징은 Application 개발, 테스트, 유지/보수에 큰 이점으로 작용
    한다.
### Layer Isolation:
[Layer Isolation](https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0102.png)
- 최상위 Layer(Presentation)를 통해 들어온 요청은 경우 각 layer를
순서대로 거쳐야 처리가 되며, 중간 Layer를 건너 뛰어 처리 될 수 없음을
나타내는 특징
- 각 Layer에서 발생한 변화에 대한 영향은 변화가 발생한 layer 내의
컴포넌트에만 제한되어야 한다.
- Layer architecture에서 Layer isolation특성을 지키지 않을 경우 
각 Layer의 컴포넌트들은 서로 결합도가 높아지게 되며 로직 변경이 발생시
큰 비용이 들게 됨.
    - 예를 들어 Presentation Layer의 역활을 하는 Web에서 Database에
    직접 접근하여 Request에 따라 Data Select, Insert 등을 진행하게 되면
    Presentation Layer에는 이 처리를 위한 많은 컴포먼트들이 존재하게 되며
    각 컴포넌트들은 서로 의존관계를 가지게 되며 변경이 발생시에 큰 비용을
    지불하게 된다.
- Separation of concerns과 함께 이 부분은 역활 및 책임 범위를 제한함으로써
개발, 테스트, 유지/보수를 용이하게 하는 특징이 되나, 특정 요청처리를 위해
불필요한 Layer를 거쳐야 한다는 단점도 만드는 개념이다.
### Layer Open, Close:
[Layer Open, Close] (https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0103.png)
-  각 Layer들은 자신의 요청을 아래의 layer로 전달하는 방식으로 Logic을
처리하고 있기에, 여러 Layer에서 공유되는 Layer가 추가 된다면  불필요하게
모든 하위 Layer를 거쳐야 된다는 문제점을 해결하기 위해 추가된 개념
    - 그림에서 처럼 Services Layer가 Business Layer 아래에 추가 되면서
    Business layer의 Logic 중 Persistence Layer와의 통신이 필요한 레이어는
    Layer Isolation 개념에 의해 Service Layer와의 통신을 통해 요청을 전달하고
    전달 받아야 된다. 이런 부분은 불필요한 Logic을 추가하게 되므로 Layer에
    Closed, Open 개념을 넣어 Service Layer의 경우 이를 무시하고 다른 하위 Layer
    로 요청을 보내는 것을 허용하는 것.
## Layered Pattern Example:
[Layered Pattern Example] (https://www.safaribooksonline.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0104.png)
- 링크의 그림에서 보는 것과 같이 Presentation Layer에서 시작된 요청(검은색 화살)
은 하위 layer는 Component 를 거쳐 DataBase Layer에 도착하고 이 요청에 대한
응답(붉은색 화살)을 Database Layer는 자신의 바로 위 Layer인 Persistent Layer로
전달하게 된다.
## 고찰
- Sinkhole anti-pattern: 이미 **Layer Open, Close, Layer Isolation** 에서 보았듯이
최상위 layer의 요청이 하위의 layer를 거처 전달될 때 불필요한 처리가 일어
남을 보았다. 특히나 요청에 대해 중간 layer가 처리를 해야 할 logic이 없을 경우
이를 보안하기 위해 Open Layer특성을 부여하는 등으로 넘길 수 있으나 이러한
부분이 커지게 되면 Layered Pattern의 규칙에 위배되는 상황이 만들어지며 이를
**Sinkhole anti-pattern** 이라고 부른다.
- 80-20 rule: **Sinkhole anti-pattern** 을 피하기 위한 rule로써, 하위
layer를 거치지 않는 logic 20%, 거치는 logic은 80%로 유지한다는 것이다.
- Toward Monolithic: 아무리 Layer를 나누어 처리를 한다고 하더라도 큰
틀에서 본다면 Layer Pattern은 Monolithic 한 개발론을 추구하게 된다는 것.
## Layered Patttern 평가
- Agility(**LOW**) : Layer Isolation으로 인해 각 레이어의 변경에 대해서는 빠른
변경을 이룰 수 있으나, 전체 Architecture 라는 면에서 보자면 각 Layer 내의
Component 간의 의존성 및 monolithic 한 구현 등에 의해 큰 시간을 들여야 한다.
- Easy deployment(**LOW**) : 규모가 커질 수록 Layer의 갯수가 늘어나며, Layer
간에는 서로 의존관계가 있으므로 새로이 변경된 사항을 적용하기 위해서는
새로 모든 부분을 다시 적용해야 한다는 문제점이 있다.
- Performance(**LOW**) : 모든 request들은 각 Layer를 거쳐야 하므로 Performance
는 낮다고 볼 수 있다.
- Testability(**HIGH**) : Layer Isolation의 영향으로 각 Test는 각 Layer에
포함된 Component를 중심으로 진행이 되므로 Test를 진행하기 쉽다.
- Scalability(**LOW**) : Layer Isolation은 구현 중에 Monolithic 한 패턴을
보이며, 또한 각 Layer간의 강한 결합도는 확장을 하기 어렵게 만든다.
- Ease of Development(**HIGH**) : 각 Layer들은 서로 기능적으로 분리되어 있고
여러 개발자, 디자이너들에게 잘 알려진 패턴이므로 개발하기가 상대적으로
쉬운편이다.


