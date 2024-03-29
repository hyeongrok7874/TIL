# 타입 변환

개발자가 의도적으로 값의 타입을 변환하는 것을 **명시적 타입 변환(explicit coercion)** 또는 **타입 캐스팅(type casting)** 이라고 한다.

자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되는 것을 **암묵적 타입 변환(implicit coercion)** 또는 **타입 강제 변환(type coercion)** 이라 한다.

타입 변환이 기존 원시 값을 직접 변경하는 것은 아니다.

원시 값은 변경 불가능한 값이므로 변경할 수 없다.

타입 변환이란 기존 원시 값을 사용해 다른 타입의 새로운 원시 값을 생성하는 것이다.

암묵적 타입 변환은 기존 변수 값을 재할당하여 변경하는 것이 아닌, 표현식을 에러 없이 평가하기 위해 피연산자의 값을 암묵적 타입 변환해 새로운 타입의 값을 만들어 단 한 번 사용하고 버린다.

명시적 타입 변환은 타입을 변경하겠다는 개발자의 의지가 코드에 명백히 드러난다.

암묵적 타입 변환은 타입을 변경하겠다는 개발자의 의지가 명백히 나타나지 않는다.

## 암묵적 타입 변환

### 문자열 타입으로 변환

- 문자열 연결 연산자 표현식을 평가하기 위해 문자열 연결 연산자의 피연산자 중에서 문자열 타입이 아닌 피연산자를 문자열 타입으로 암묵적 타입 변환한다.

### 숫자 타입으로 변환

- 산술, 비교 연산자 표현식을 평가하기 위해 연산자의 피연산자 중에서 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다.
- 피연산자를 숫자 타입으로 변환할 수 없는 경우는 연산을 수행할 수 없으므로 표현식의 평가 결과는 NaN이 된다.
- 빈 문자열(' '), 빈 배열([ ]), null, false는 0
- true는 1로 변환된다
- 객체와 빈 배열이 아닌 배열, undefined는 변환되지 않아 NaN이 된다.

### 불리언 타입으로 변환

- if 문이나 for 문과 같은 제어문 또는 삼항 조건 연산자의 조건식의 평과 결과를 불리언 타입으로 암묵적 타입 변환한다.

#### Falsy 값
거짓으로 평가되는 값

- false
- undefined
- null
- 0, -0
- NaN
- ''(빈 문자열)

#### Truthy 값

참으로 평가되는 값

Falsy 값 외의 모든 값

## 명시적 타입 변환

### 문자열 타입으로 변환

- String 생성자 함수를 new 연산자 없이 호출하는 방법
- Object.prototype.toString 메서드를 사용하는 방법
- 문자열 연결 연산자를 이용하는 방법

```js
String(1); //"1"

(1).toString(); //"1"

1 + ''; //"1"
```

### 숫자 타입으로 변환

- Number 생성자 함수를 new 연산자 없이 호출
- parseInt, parseFloat 함수를 사용하는 방법(문자열만 숫자 타입으로 변환 가능)
- \+ 단항 산술 연산자를 이용하는 방법
- \* 산술 연산자를 이용하는 방법

```js
Number('0');

parseInt('0');

+'0';

'0' * 1;
```

### 불리언 타입으로 변환

- Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
- ! 부정 논리 연산자를 두 번 사용하는 방법

```js
Boolean('x');
Boolean('0');
Boolean(null);
Boolean(undefined);

!!'x';
!!0;
!!null;
!!undefined;
```

## 단축 평가

표현식을 평가하는 도중에 평가 결과가 확정된 경우 나머지 평과 과정을 생략하는 것

### 논리 연산자를 사용한 단축 평가

- 논리합 또는 논리곱 연산자 표현식은 불리언 값이 아닐 수도 있다.
- 논리합 또는 논리곱 연산자 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.
- 논리곱 연산자는 두 개의 피연산자가 모두 true로 평가될 때 true를 반환한다.

|단축 평가 표현식|평가 결과|
|:---:|:---:|
|true \| \| anything|true|
|false \| \| anything|anything|
|true && anything|anything|
|false && anything|false|

### 사용 예

#### 객체를 가리키기를 기대하는 변수가 null 또는 undefined가 아닌지 확인하고 프로퍼티를 참조할 때

```js
let elem = null;
let value = elem.value; // TypeError
```

만약 객체를 가리키기를 기대하는 변수의 값이 객체가 아니라 null 또는 undefined인 경우 객체의 프로퍼티를 참조하면 타입 에러가 발생한다

```js
let elem = null;
let value = elem && elem.value; // null
```
 에러가 나지 않는다.

 #### 함수 매개 변수에 기본값을 설정할 때

 함수를 호출할 때 인수를 전달하지 않으면 매개변수에는 undefined가 할당된다. 이때 단축 평가를 사용해 매개변수의 기본값을 설정하면 undefined로 인해 발생할 수 있는 에러를 방지할 수 있다.

 ```js
 // 단축 평가를 사용한 매개변수의 기본값 설정
 function getStringLength(str){
     str = str || '';
     return str.length;
 }

 getStringLength();
 getStringLength('hi');

// ES6의 매개변수의 기본값 설정
 function getStringLength(str = ''){
     return str.length;
 }

 getStringLength();
 getStringLength('hi');
 ```

 ### 옵셔널 체이닝 연산자

 ?.는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.

 ```js
 let elem = null;

 let value = elem?.value;
 console.log(value); // undefined
 ```

옵셔널 체인닝 연산자는 좌항 피연산자가 Falsy 값이라도 null 또는 undefined가 아니면 우항의 프로퍼티 참조를 이어간다.

### null 병합 연산자

null 병합 연산자 ??는 좌항의 피연산자가 null 또는 undefined인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다.

```js
let foo = null ?? 'defult string';
console.log(foo); // "default string"
```

변수에 기본값을 설정할 때 유용하다.

좌항의 피연산자가 Falsy 값이라도 null 또는 undefined가 아니면 좌항의 피연산자를 그대로 반환한다.