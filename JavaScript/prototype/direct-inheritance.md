# 직접 상속

## Object.create에 의한 직접 상속

Object.create 메서드는 명시적으로 프로토타입을 지정하여 새로운 객체를 생성한다.

```js
/**
 * 지정된 프로토타입 및 프로퍼티를 갖는 새로운 객체를 생성하여 반환한다.
 * @param {Object} prototype - 생성할 객체의 프로토타입으로 지정할 객체
 * @param {Object} [propertiesObject] - 생성할 객체의 프로퍼티를 갖는 객체
 * @return {Object} 지정된 프로토타입 및 프로퍼티를 갖는 새로운 객체
 */
Object.create(prototype[, propertiesObject])
```

Object.create 메섣는 첫 번째 매개변수에 전달한 객체의 프로토타입 체인에 속한느 객체를 생성한다.

### 장점

- new 연산자 없이 객체 생성 가능
- 프로토타입을 지정하면서 객체 생성 가능
- 객체 리터럴에 의해 생성된 객체도 상속 가능

### 직접 호출 비권장

Object.create 메서드로 프로토타입 체인의 종점에 위치하는 객체를 생성할 수 있기 때문에 직접 호출이 비권장된다.

프로토타입 체인의 종점에 위치하는 객체는 Object.prototype의 빌트인 메서드를 사용할 수 없다.

```js
// 프로토타입이 null인 객체, 즉 프로토타입 체인의 종점에 위치하는 객체를 생성한다
const obj = Object.create(null);
obj.a = 1;

console.log(obj.hasOwnProperty("a"));
// TypeError: obj.hasOwnProperty is not a function

// Object.prototype의 빌트인 메서드는 객체로 직접 호출하지 않는다
console.log(Object.prototype.hasOwnProperty.call(obj, "a")); // true
```

## 객체 리터럴 내부에서 `__proto__`에 의한 직접 상속

ES6에서는 객체 리터럴 내부에서 `__proto__` 접근자 프로퍼티를 이용하여 직접 상속을 구현할 수 있다.

```js
const myProto = { x: 10 };

// 객체 리터럴에 의해 객체를 생성하면서 프로토타입을 지정하여 직접 상속받을 수 있다.
const obj = {
  y: 20,
  // 객체를 직접 상속받는다.
  // obj -> myphoto -> Object.prototype -> null
  __proto__: myProto,
};

// 위 코드는 아래와 동일하다

// const obj = Object.create(myProto, {
//   y: { value: 20, writable: true, enumerable: true, configurable: true },
// });
```
