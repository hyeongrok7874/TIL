# strict mode (엄격 모드)

ES5부터 추가된 모드로, JS 언어의 문법을 좀 더 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 JS 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해 명시적인 에러를 발생시킨다

## 린트 도구

ESLint 같은 린트 도구를 사용해도 strict mode와 유사한 효과를 얻을 수 있다.

린트 도구는 정적 분석 기능을 통해 소스코드를 실행하기 전에 소스코드를 스캔하여 문법적 오류만이 아닌 잠재적 오류까지 찾아내고 원인을 리포팅해준다

strict mode가 제한하는 오류는 물론 코딩 컨벤션을 설정 파일 형태로 정의하고 강제할 수 있다

## strict mode 적용

strict mode를 적용하려면 전역의 선두 또는 함수 몸체의 선두에 ```'use strict';```를 추가한다

전역의 선두에 추가하면 스크립트 전체에 strict mode가 적용된다

```js
'use strict';

function foo() {
  x = 10; // ReferenceError: x is not defined
}

foo();
```

함수 몸체의 선두에 추가하면 해당 함수와 중첩 함수에 strict mode가 적용된다.

```js
function foo() {
  'use strict';

  x = 10; // ReferenceError: x is not defined
}

foo();
```

코드의 선두에 위치 시키지 않으면 제대로 동작하지 않는다

```js
function foo() {
  x = 10; // 에러를 발생시키지 않는다
  'use strict';
}

foo();
```

## 전역에 strict mode 적용은 피하자

전역에 적용한 strict mode는 스크립트 단위로 적용된다.

strict mode 스크립트와 non-strict mode 스크립트를 혼용하는 것은 오류를 발생시킬 수 있다.

외부 서드파티 라이브러리를 사용하는 경우 라이브러리가 non-strict mode인 경우도 있기 때문에 전역에 적용은 바람직하지 않다

이러한 경우 즉시 실행 함수로 스크립트 전체를 감싸서 스코프를 구분하고 즉시 실행 함수의 선수에 strict mode를 적용한다.

## 함수 단위로 strict mode 적용은 피하자

어떤 함수는 적용하고 어떤 함수는 적용하지 않는 것은 바람직하지 않고 모든 함수에 일일이 strict mode를 적용하는 것은 번거로운 일이다.

strict mode가 적용된 함수가 참조할 함수 외부의 컨텍스트에 strict mode를 적용하지 않는다면 이 또한 문제가 발생할 수 있다.

strict mode는 즉시 실행 함수로 감싼 스크립트 단위로 적용하는 것이 바람직하다

## strict mode가 발생시키는 에러들

### 암묵적 전역

선언하지 않은 변수를 참조하면 ReferenceError가 발생한다

### 변수, 함수, 매개변수의 삭제

delete 연산자로 변수, 함수, 매개변수를 삭제하면 SyntaxError가 발생한다

### 매개변수 이름의 중복

중복된 매개변수 이름을 사용하면 SyntaxError가 발생한다

### with 문의 사용

with 문을 사용하면 SyntaxError가 발생한다.

#### with 문

전달된 객체를 스코프 체인에 추가한다

동일한 객체의 프로퍼티를 반복해서 사용할 때 객체 이름을 생략할 수 있어서 코드가 간단해지는 효과가 있다

하지만 성능과 가독성이 나빠지므로 사용을 지양하자

## strict mode 적용에 의한 변화

### 일반 함수의 this

strict mode에서 함수를 일반 함수로서 호출하면 this에 undefined가 바인딩된다.

생성자 함수가 아닌 일반 함수 내부에서는 this를 사용할 필요가 없기 때문이다.

이때 에러는 발생하지 않는다.

### arguments 객체

strict mode에서는 매개변수에 전달된 인수를 재할당하여 변경해도 arguments 객체에 반영되지 않는다.

```js
(function (a) {
  'use strict';

  a = 2;

  // 변경된 인수가 arguments 객체에 반영되지 않는다.
  console.log(arguments); // {0: 1, lenth: 1}
})
```