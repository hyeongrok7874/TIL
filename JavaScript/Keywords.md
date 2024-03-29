# var, let, const

## var

ES5까지 변수를 선언할 수 있는 유일한 방법은 var 키워드였다

### 변수 중복 선언 허용

중복 선언시 초기화문이 있는 변수 선언문은 var 키워드가 없는 듯이 동작하고, 초기화문이 없는 변수 선언문은 무시된다

```js
var x = 1;
var y = 1;

var x = 100; // var 키워드가 없는 듯이 동작
var y; // 무시

console.log(x); // 100
console.log(y); // 1
```

### 함수 레벨 스코프

함수의 코드 블록만을 지역 스코프로 인정한다

함수 외부에서 var 키워드로 선언한 변수는 코드 블록 내에서 선언해도 전부 전역 변수가 된다

### 변수 호이스팅

var로 선언된 변수는 변수 선언문 이전에 참조할 수 있다.

호이스팅이 될 때 undefined로 초기화되기 때문이다

```js
// 호이스팅에 의해 변수 variable이 선언되면서 undefined로 초기화 된다
console.log(variable); // undefined

variable = 100; // 할당

console.log(variable); // 100

var variable;
```

변수 선언문 이전에 변수를 참조하는 것은 변수 호이스팅에 의해 에러를 발생시키지는 않지만 프로그램의 흐름상 맞지 않고 가독성을 떨어뜨리며 오류를 발생할 수 있다

### 전역 객체와 var

var 키워드로 선언한 전역 변수와 전역 함수, 그리고 선언하지 않은 변수에 값을 할당한 암묵적 전역은 전역 객체 window의 프로퍼티가 된다

## let

ES6에서 도입되었다

### 변수 중복 선언 금지

let 키워드로 이름이 동일한 변수를 중복 선언하면 문법 에러가 발생한다

```js
let a = 5;
let a = 2; // SyntaxError: Identifier 'a' has already been declared
```

### 블록 레벨 스코프

let으로 선언한 변수는 모든 코드 블록(함수, if 문, for 문, while 문, try/catch 문 등)을 지역 스코프로 인정하는 블록 레벨 스코프를 따른다

```js
let a = 5; // 전역 변수

{
  let a = 3; // 전역 변수
  let b = 1; // 지역 변수
}

console.log(a); // 5
console.log(b); // ReferenceError: b is not defined
```

### 변수 호이스팅

let 키워드로 선언한 변수는 "선언 단계"와 "초기화 단계"가 분리되어 진행된다.

런타임 이전에 JS 엔진에 의해 암묵적으로 선언 단계가 먼저 실행되지만 초기화는 변수 선언문에 도달했을 때 실행된다.

```js
console.log(a); // ReferenceError: foo is not defined

let a; // 초기화 단계가 실행된다
console.log(a); // undefined

a = 1; // 할당
console.log(a); // 1
```

호이스팅이 발생하지 않는 것처럼 동작한다

#### 일시적 사각지대

스코프의 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없는 구간

### 전역 객체와 let

let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다 (window.variable와 같이 접근 불가능)

let 전역 변수는 보이지 않는 개념적인 블록(전역 렉시컬 환경의 선언적 환경 레코드) 내에 존재한다

## const

상수를 선언하기 위해 사용한다

### 선언과 초기화

const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다

```js
const variable = 1;
```

그렇지 않으면 문법 에러가 발생한다

### 재할당 금지

const로 선언한 변수는 재할당이 금지된다

```js
const foo = 1;
foo = 2; // TypeError: Assignment to constant variable.
```

### 상수

재할당이 금지된 변수

const 키워드로 선언된 변수에 원시 값을 할당한 경우 원시 값은 변경할 수 없는 값이고 const 키워드에 의해 재할당이 금지되므로 할당된 값을 변경할 수 있는 방법은 없다

상수를 적극적으로 사용하면 유지보수성과 가독성이 향상된다

일반적으로 상수는 대문자로 선언해 상수임을 명확히 나타낸다 (여러단어 일 시에는 스네이크 케이스)

### const와 객체

const로 선언된 변수에 객체를 할당한 경우 값을 변경할 수 있다

변경 불가능한 값인 원시 값은 재할당 없이 변경 불가능하지만 객체는 재할당 없이도 직접 변경이 가능하다

```js
const person = {
  name: 'Lee'
};

person.name = 'Kim'; // 객체는 변경 가능한 값이다.

console.log(person) // {name: "Kim"}
```

const 키워드는 재할당을 금지할 뿐 "불변"을 의미하진 않는다.

프로퍼티 동적 생성, 삭제, 프로퍼티 값의 변경을 통해 객체를 변경하는 것은 가능하다

이때 객체가 변경되더라도 변수에 할당된 참조 값은 변경되지 않는다

## var vs. let vs. const

변수 선언은 기본적으로 const를 사용하고 let은 재할당이 필요한 경우에 한정하여 사용하는 것이 좋다

- ES6를 사용한다면 var 키워드는 사용하지 않는다
- 재할당이 필요한 경우에 한정해 let 키워드를 사용한다. 이때 변수의 스코프는 최대한 좁게 만든다
- 변경이 발생하지 않고 읽기 전용으로 사용하는(재할당이 필요 없는 상수) 원시 값과 객체에는 const 키워드를 사용한다. 재할당을 금지하므로 다른 키워드보다 안전하다

변수를 선언할 때는 일단 const를 사용하고 반드시 재할당이 필요하다면 그때 const를 let으로 변경해도 결코 늦지 않다