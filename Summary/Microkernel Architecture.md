# Microkernel Architecture
---------------------------

- 플러그인 아키텍쳐 패턴이라고도 불린다.
- 일반적으로 패키징되어서 다운로드가능한 프로그램. 서드파티 제품이라고도 한다.


## Pattern Description
- 2가지의 구성요소 : core system, plug-in module
- 코어 시스템은 시스템이 운영되는데 필요한 최소한의 기능들을 담당
- 플러그-인 모듈은 기본 코어 시스템을 이용해서 각자의 필요한 로직을 실행
- 플러그-인 모듈은 각각이 완전히 독립된 하나의 기능을 구성
- 플러그-인 모듈은 다른 플러그-인 모듈에 대해 의존성을 가질 수 있음
  + 각 모듈에서는 필요 모듈에 대한 의존성에 대한 정보를 가지고 있어야 한다
- 플러그-인 모듈은 여러 방법을 통해 코어 시스템과 연동될 수 있다
  + messaging, web services, direct point-to-point binding ...
-

## Pattern Examples
- Eclipse IDE 
- Web Browser..
- 일반적인 다운로드가능한 제품들
- 

## Considerations
- 다른 아키텍쳐 패턴의 일부로 포함 가능
- 코어 시스템을 변경하지 않고도 기능추가가 가능
- 일반적인 다운로드 가능한 제품은 마이크로커널 아키텍쳐 패턴이 시작 아키텍쳐로서 우선 고려해야하는 대상
  + 차후 추가기능을 개발하기 편함
  + 사용자가 필요한 기능을 제어가능
  + 해당 아키텍쳐가 모든 요구사항을 충족하지 못할때 리팩토링 용이함 

## Pattern Analysis
- Overall Agility : High
  + 
- Case of deployment : High
  + 
- Testablility : High
  + 
- Performance : High
  + 
- Scalability : Low
  + 
- Case of development : Low
  + 
