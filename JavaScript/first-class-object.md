# 함수와 일급 객체

## 일급 객체

- 무명의 리터럴로 생성할 수 있다. 즉, 런타임에 생성이 가능하다.
- 변수나 자료구조(객체, 배열 등)에 저장할 수 있다.
- 함수의 매개변수에 전달할 수 있다.
- 함수의 반환값으로 사용할 수 있다.

함수는 일급 객체이므로 객체와 동일하게 사용할 수 있다

객체는 값으로 함수는 값과 동일하게 취급할 수 있다

따라서 함수는 값을 사용할 수 있는 곳 (변수 할당문, 객체의 프로퍼티 값, 배열의 요소, 함수 호출의 인수, 함수 반환문)이라면 어디서든지 리터럴로 정의할 수 있고 런타임에 함수 객체로 평가된다

일급 객체로서 함수의 가장 큰 특징은 일반 객체와 같이 함수의 매개변수에 전달 할 수 있고 함수의 반환값으로 사용할 수도 있다는 것이다

이는 함수형 프로그래밍을 가능케 한다

## 함수 객체의 프로퍼티

함수는 객체로 프로퍼티를 가질 수 있다

### arguments 프로퍼티

arguments의 프로퍼티 값은 arguments 객체다

- arguments 객체 : 함수 호출 시 전달된 인수들의 정보를 담고 있는 순회 가능한 유사 배열 객체이며, 함수 내부에서 지역 변수처럼 사용된다 (함수 외부에서는 참조할 수 없다)

- arguments 프로퍼티는 현재 일부 브라우저에서 지원하며 ES3부터 표준에서 폐지되어 Function.arguments와 같은 사용법은 권장되지 않고 함수 내부에서 지역 변수처럼 사용할 수 있는 arguments 객체를 참조하도록 한다

- arguments의 length 프로퍼티는 인수의 개수를 나타낸다

- arguments 객체는 매개변수 개수를 확정할 수 없는 **가변 인자 함수**를 구현할 때 유용하다

- arguments 객체는 배열 형태로 인자 정보를 담고 있지만 실제 배열이 아니 유사 배열 객체다

#### 매개변수와 인수

- JS는 함수의 매개변수와 인수의 개수가 일치하는지 확인하지 않는다 (함수 호출 시 매개변수 개수만큼 인수를 전달하지 않아도 에러 발생 X)

- 함수를 정의할 때 선언한 매개변수는 함수 몸체 내부에서 변수와 동일하게 취급된다. (함수 호출 -> 암묵적 매개변수 선언 -> 초기화 -> 할당)

- 매개변수 개수보다 인수를 적게 전달 시 인수가 전달되지 않은 매개변수는 undefined로 초기화된 상태를 유지한다

- 매개변수 개수보다 인수를 초과하여 전달 시 초과된 인수는 무시된다

- 모든 인수(초과된 인수 포함)는 그냥 버려지지 않고 arguments 객체의 프로퍼티로 보관된다

#### arguments 객체의 Symbol(Symbol.iterator) 프로퍼티

arguments 객체를 순회 가능한 자료구조인 이터러블로 만들기 위한 프로퍼티

Symbol.iterator를 프로퍼티 키로 사용한 메서드를 구현하는 것에 의해 이터러블이 된다

```js
function multiply(x, y) {
  // 이터레이터
  const iterator = arguments[Symbol.iterator]();

  // 이터레이터의 next 메서드를 호출하여 이터러블 객체 arguments를 순회
  console.log(iterator.next()); // {value: 1, done: false}
  console.log(iterator.next()); // {value: 2, done: false}
  console.log(iterator.next()); // {value: 3, done: false}
  console.log(iterator.next()); // {value: undefined, done: true}

  return x * y;
}

multiply(1, 2, 3);
```

#### 유사 배열 객체

length 프로퍼티를 가진 객체로 for 문으로 순회할 수 있는 객체

배열 메서드를 사용할 경우 에러가 발생하므로 배열 매서드를 사용하기 위해선 간접 호출해야 한다

ES6에서 도입된 Rest 파라미터로 위의 번거로운을 해결할 수 있다

#### 유사 배열 객체와 이터러블

ES6에서 도입된 이터레이션 프로토콜을 준수하면 순회 가능한 자료구조이 ㄴ이터러블이 된다

이터러블의 개념이 없었던 ES5에서 arguments 개게는 유사 배열 객체로 구분되었다.

이터러블이 도입된 ES6부터 arguments 객체는 유사 배열 객체이면서 동시에 이터러블이다

### caller 프로퍼티

ECMAScript 사양에 포함되지 않은 비표준 프로퍼티

이후 표준화될 예정도 없는 프로퍼티로 사용하지 말고 참고로만 알아두자

함수 객체의 caller 프로퍼티는 함수 자신을 호출한 함수를 가리킨다

함수를 호출한 함수가 없을 경우 null을 가리킨디 (브라우저 한정)

```js
function foo(func) {
  return func();
}

function bar() {
  return 'caller : ' + bar.caller;
}

console.log(foo(bar)); // caller : function foo(func) {...}
```

### length 프로퍼티

함수 객체의 length 프로퍼티는 함수를 정의할 때 선언한 매개변수의 개수를 가리킨다

arguments 객체의 length 프로퍼티와 함수 객체의 length 프로퍼티의 값은 다를 수 있으므로 주의해야 한다

arguments의 length 프로퍼티는 인자의 개수를 가리키고, 함수 객체의 length 프로퍼티는 매개변수의 개수를 가리킨다

```js
function foo(x, y){}

console.log(foo.length); // 2
```

### name 프로퍼티

함수 객체의 name 프로퍼티는 함수 이름을 나타낸다

ES6 이전까지는 비표준이었다가 ES6에서 정식 표준이 되었다

ES5와 ES6에서 동작을 달리한다

익명 함수 표현식의 경우 ES5에서는 빈 문자열을 값으로 갖고, ES6에서는 함수 객체를 가리키는 식별자를 값으로 갖는다.

```js 
// 식별자가 아닌 함수 이름을 나타낸다
let hello = function foo() {};
console.log(hello.name); // foo

let anonymous = function(){};
// ES5: 빈 문자열, ES6: 함수 객체를 가리키는 변수 이름
console.log(anonymous.name) // anonymous

function bar() []
console.log(bar.name); // bar
```

### \__proto__ 접근자 프로퍼티

[[Prototype]] 내부 슬롯이 가리키는 프로토타입 객체에 간접적으로 접근하기 위해 사용하는 접근자 프로퍼티

내부 슬롯에는 직접 접근할 수 없고 간접적인 접근 방법을 제공하는 경우에 한하여 접근할 수 있다 ([[Prototype]]도 마찬가지)

모든 객체는 [[Prototype]]이라는 내부 슬롯을 갖는다.

[[Prototype]] 내부 슬롯은 객체지향 프로그래밍의 상속을 구현하는 프로토타입 객체를 가리킨다

```js
const obj = {a: 1};

// 객체 리터럴 방식으로 생성한 객체의 프로토타입 객체는 Object.prototype이다.
console.log(obj.__proto__ === Object.prototype); // true

// 객체 리터럴 방식으로 생성한 객체는 프로토타입 객체인 Object.prototype의 프로퍼티를 상속받는다.
console.log(obj.hasOwnProperty('a')); // true
console.log(obj.hasOwnProperty('__proto__')); // false
```

#### hasOwnProperty 메서드

인수로 전달받은 프로퍼티 키가 객체 고유의 프로퍼티 키인 경우에만 true를 반환하고 상속받은 프로토타입의 프로퍼티 키인 경우 false를 반환한다.

### prototype 프로퍼티

생성자 함수로 호출할 수 있는 함수 즉, constructor만이 소유하는 프로퍼티

일반 객체와 생성자 함수로 호출할 수 없는 non-constructor에는 prototype 프로퍼티가 없다

prototype 프로퍼티는 함수가 생성자 함수로 호출될 때 생성자 함수가 생성할 인스턴스의 프로토타입 객체를 가리킨다

```js
// 함수 객체는 prototype 프로퍼티를 소유한다
(function () {}).hasOwnProperty('prototype'); // true

// 일반 객체는 prototype 프로퍼티를 소유하지 않는다
({}).hasOwnProperty('prototype'); // false
```