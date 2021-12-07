# jenkins

> 소프트웨어 개발 시 지속적으로 통합 서비스를 제공하는 툴

다수의 개발자들이 하나의 프로그램을 개발할 때 버전 충돌을 방지하기 위해 각자 작업한 내용을 공유영역에 있는 저장소에 번번히 업로드함으써 지속적 통합이 가능하도록 해준다.

## 이점

개발중인 프로젝트에서 커밋은 매우 번번히 일어나기 때문에 커밋 횟수만큼 빌드를 실행하는 것이 아니라 작업이 큐잉되어 자신이 실행될 차례를 기다리게 된다

- 프로젝트 표준 컴파일 환경에서의 컴파일 오류 검출
- 자동화 테스트 수행
- 정적 코드 분석에 의한 코딩 규약 준수여부 체크
- 프로파일링 툴을 이용한 소스 변경에 따른 성능 변화 감시
- 결합 테스트 환경에 대한 배포작업

이 외에도 젠킨스는 500여가지가 넘는 플러그인을 온라인으로 간단히 인소톨 할 수 있다

또한 스크립트를 이용해 손쉽게 자신에게 필요한 기능을 추가 할 수도 있다

## 각종 배치 작업의 간략화

DB구축, 어플리케이션 서버로의 Deploy(프로그램 등을 서버와 같은 기기에 설치하여 서비스 등을 제공), 라이브러리 릴리즈와 같이 이전에 CLI로 실행되던 작업들이 젠킨스 덕분에 웹 인터페이스로 손쉽게 가능해졌다

## Build 자동화의 확립

빌드 툴의 경우 Java는 maven과 gradle이 자리잡고 있다

젠킨스와 연동하여 빌드 자동화를 통해 프로젝트 진행의 효율성을 높일 수 있다.

## 자동화 테스트

젠킨스를 사용하는 가장 큰 이유다

자동화 테스트가 포함되지 않은 빌드는 CI(지속적 통합) 자체가 불가능하다고 봐도 무방하다. 

젠킨스는 버전관리시스템과 연동하여 코드 변경을 감지하고 자동화 테스트를 수행하기 때문에 만약 개인이 실행하지 못한 테스트가 있어도 안전망이 되어준다.

## 코드 표준 준수여부 검사

개인이 미처 실시하지 못한 코드 표준 준수 여부의 검사나 정적 분석을 통한 코드 품질 검사를 빌드 내부에서 수행하여 기술적 부채의 감소에도 크게 기여한다

## 빌드 파이프라인 구성

2개 이상의 모듈로 구성되는 레이어드 아키텍처가 적용된 프로젝트에는 그에 따른 빌드 파이프라인(연속적인 이벤트 혹은 Job의 그룹) 구성이 필요하다

(예 : 도메인 -> 서비스 -> UI와 같이 각 레이어의 참조 관계에 따라 순차적으로 빌드를 진행해야한다)

젠킨스에서는 이런 빌드 파이프라인의 구성을 간단히 할 수 있고 스크립트로 매우 복잡한 제어까지도 가능하다

### 레이어드 아키텍처

구성요소들이 수평적인 레이어로 조직화되어 있는 다층 구조

4개의 계층으로 이루어져 있다

#### 1. Presentaion Layer

- 최종 사용자들에게 UI를 제공하거나 클라이언트로 응답을 다시 보내는 역할을 담당하는 모든 클래스를 포함한다
- API의 엔드포인트(어떠한 소프트웨어나 제품에 최종목적지인 사용자)들을 정의하고 전송된 HTTP 요청들을 읽어 들이는 로직을 구현
  
#### 2. Business Layer

- 접근성, 보안, 인증과 같은 로직이 해당 계층에서 발생한다. ESB, 미들웨어, 유효성 검사 등을 수행한다
- 실제 시스템이 구현해야하는 로직들을 이 레이어에서 구현한다.

#### 3. Persistence Layer

- 이 계층은 DAO presentaion, ORM 등을 포함한다.
- 데이터베이스에서 데이터를 저장, 수정, 불러들이는 등 데이터베이스와 관련된 로직을 구현한다

#### 4. Database Layer

- 모든 DB가 저장되는 레이어다

레이어드 아키텍쳐의 특징은 하위 레이어에 의존한다는 것이다.