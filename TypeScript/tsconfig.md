# tsconfig.json

## compilerOptions

tsc 명령 형식에서 옵션을 나타낸다

### module

동작 대상 플랫폼이 웹 브라우저인지 Node.js인지 구분하여 그에 맞는 모듈 방식으로 컴파일한다

- 웹 브라우저 : amd
- Node.js : commonjs

### moduleResolution

module 키 값에 따라 달라진다

- amd : classic
- commonjs : node

### baseUrl과 outDir

트랜스파일된 ES5 JS 파일을 저장하는 디렉터리를 설정한다

tsc는 tsconfig.json 파일이 있는 디렉터리에서 실행됨으로 baseUrl의 키 값은 "."이 보통이다

Outdir은 baseUrl 설정값을 기준으로 했을 때 하위 디렉터리의 이름이고 빌드된 결과가 만들어진다

### paths 

소스 파일의 import 문에서 from 부분을 해석할 때 찾아야 하는 디렉터리를 설정

### esModuleInterop

오픈소스 JS 라이브러리 중 웹 브라우저에서 동작한다는 가정으로 만들진 것들이 CommonJS 방식으로 동작하는 TS 코드에 혼란을 줄 수 있다

AMD 방식의 라이브러리가 동작하려면 esModuleInterop 값이 true여야 한다

### sourceMap

true일 시, 트랜스파일 디렉터리에 .js 파일 이외에도 .js.map 파일이 만들어진다

이 소스맵 파일은 변환된 JS 코드가 TS 코드의 어디에 해당하는지 알려준다

소스맵 파일은 주로 디버깅할 때 사용된다

### downlevellteration

생성기 구문이 정상적으로 동작하려면 반드시 true여야한다

### noImpolicitAny

TS 컴파일러는 기본적으로 매개변수에 타입을 명시하지 않은 코드는 암시적으로 any 타입을 설정한 것으로 간주한다

이런 형태의 코드는 TS의 장점을 사용하는 것이 아니므로 문제가 있음을 알려준다

false로 설정 시 타입을 지정하지 않더라도 문제로 인식하지 않게 한다

## include 

대상 파일 목록을 나타낸다
