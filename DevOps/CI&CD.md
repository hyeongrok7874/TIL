# CI/CD

## CI

Continuous Integration 

지속적인 통합

새로운 코드 변경 사항이 정기적으로 빌드 및 테스트 되어 공유 레포지토리에 통합히는 것

### 필요 환경

- 다수의 개발자가 형상관리 툴을 공유하여 사용하는 환경 : 자동화된 빌드&테스트는 원천 소스코드의 충돌 등을 방어한다
- MSA(Micro Service Archietecture) 환경 : 기능 충돌 방지

### 핵심 목표

- 버그를 신속하게 찾아 해결
- 소프트웨어의 품질을 개선
- 새로운 업데이트의 검증 및 릴리즈의 시간을 단축시키는 것

## CD 

Continuous Delivery 혹은 Continuous Depolyment

지속적인 서비스 제공 혹은 지속적인 배포

개발자의 변경 사항이 레포지토리를 넘어, 고객의 프로덕션(Production) 환경까지 릴리즈 되는 것

### Continuous Delivery

공유 repository까지 자동으로 release 하는 것

### Continuous Depolyment

Production 레벨까지 자동으로 deploy

서비스의 사용자는 최대한 빠른 시간 내에 최신 버전의 Production을 제공받을 필요가 있다

CD는 언제나 신뢰가능한 버전을 유지할 수 있도록 해준다