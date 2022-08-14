# 표준 빌트인 객체

js는 Object, String, Number, Boolean, Symbol, Date, Math ... 등 40여 개의 표준 빌트인 객체를 제공한다

Math, Reflect, JSON을 제외한 표준 빌트인 객체는 모두 인스턴스를 생성할 수 있는 생성자 함수 객체다.

생성자 함수 객체인 표준 빌트인 객체는 프로토타입 메서드와 정적 메서드를 제공하고, 생성자 함수 객체가 아닌 표준 빌트인 객체는 정적 메서드만 제공한다.

```js
// String 생성자 함수에 의한 String 객체 생성
const str = new String("hyeongrok");

// String 생성자 함수를 통해 생성한 str 객체의 프로토타입은 String.prototype 이다.
console.log(Object.getPrototypeOf(str) === String.prototype); // true
```

생성자 함수인 표준 빌트인 객체가 생성한 인스턴스의 프로토타입은 표준 빌트인 객체의 prototype 프로퍼티에 바인딩된 객체다.

표준 빌트인 객체의 prototype 프로퍼티에 바인딩된 객체는 다양한 기능의 빌트인 프로토타입 메서드를 제공한다.

표준 빌트인 객체는 인스턴스 없이도 호출 가능한 빌트인 정적 메서드를 제공한다.

```js
const num = new Number(1.5);

// Number.prototype의 프로토타입 메서드
console.log(num.toFixed()); // 2

// Number의 정적 메서드
console.log(Number.isInteger(0.5)); // false
```
