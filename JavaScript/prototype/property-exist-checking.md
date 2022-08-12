# 프로퍼티 존재 확인

## in 연산자

객체 내에 특정 프로퍼티가 존재하는지 여부를 확인한다.

```js
/**
 * key: 프로퍼티 키를 나타내는 문자열
 * object: 객체로 평가되는 표현식
 */
key in object;
```

in 연산자는 확인 대상 객체의 프로퍼티뿐만 아니라 확인 대상 객체가 상속받은 모든 프로토타입의 프로퍼티를 확인한다

```js
const person = {
  name: "hyeongrok",
  address: "gwangju",
};

console.log("name" in person); // true

// tostring은 Object.prototype의 메서드다.
console.log("toString" in person); // true
```

ES6에서 도입된 Reflect.has 메서드로 대신할 수 있다.

in 연산자와 동일하게 동작한다.

```js
const person = { name: "hyeongrok" };

console.log(Reflect.has(person, "name")); // true
console.log("toString" in person); // true
```

## Object.prototype.hasOwnProperty 메서드

객체에 특정 프로퍼티가 존재하는지 확인할 수 있다.

인수로 전달받은 프로퍼티 키가 객체 고유의 프로퍼티 키인 경우에만 true를 반환하고 상속받은 프로토타입의 프로퍼티 키인 경우 false를 반환한다.

```js
const person = { name: "hyeongrok" };

console.log(person.hasOwnProperty("name")); // true
console.log(person.hasOwnProperty("toString")); // false
```
