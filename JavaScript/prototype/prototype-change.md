# 프로토타입의 교체

프로토타입은 임의의 다른 객체로 변경할 수 있다

부모 객체인 프로토타입을 동적으로 변경할 수 있다는 것을 의미한다.

객체간의 상속 관계를 동적으로 변경할 수 있다

프로토타입은 직접 교체하지 않는 것이 좋다

## 방법

- 생성자 함수
- 인스턴스
- 직접 상속
- 클래스

## 생성자 함수에 의한 프로토타입의 교체

```js
const Person = (function() {
  function Person(name){
    this.name = name;
  }

  // 생성자 함수의 prototype 프로퍼티를 통해 프로토타입을 교체
  Person.prototype = {
    constructor: Person, // constructor 프로퍼티와 생성자 함수 간의 연결을 설정
    sayHello(){
      console.log(`Hi! My name is ${this.name}`);
    }
  };

  return Person;
}());

const me = new Person('Lee');
```

Person.prototype = ... 은 Person 생성자 함수가 생성할 객체의 프로토타입을 객체 리터럴로 교체한 것 이다.

프로토타입으로 교체한 객체 리터럴에는 constructor 프로퍼티가 없다

constructor 프로퍼티는 js 엔진이 프로토타입을 생성할 때 암묵적으로 추가한 프로퍼티다.

따라서 me 객체의 생성자 함수를 검색하면 Person이 아닌 Object가 나온다

프로토타입을 교체하면 constructor 프로퍼티와 생성자 함수 간의 연결이 파괴된다

프로토타입으로 교체한 객체 리터럴에 constructor 프로퍼티를 추가하여 프로토타입의 constructor 프로퍼티를 되살린다.

## 인스턴스에 의한 프로토타입의 교체

프로토타입은 인스턴스의 ```__proto__``` 접근자 프로퍼티(또는 Object.getPrototypeOf 메서드)를 통해 접근할 수 있다

따라서 인스턴스의  ```__proto__``` 접근자 프로퍼티(또는 Object.getPrototypeOf 메서드)를 통해 프로토타입을 교체할 수 있다

```__proto__``` 접근자 프로퍼티를 통해 프로토타입을 교체하는 것은 이미 생성된 객체의 프로토타입을 교체하는 것이다

```js
function Person(name) {
  this.name = name;
}

const me = new Person('Lee')

const parent = {
  constructor: Person,
  sayHello(){
    console.log(`Hi! My name is ${this.name}`);
  }
};

Person.prototype = parent; 
// 생성자 함수의 prototype 프로퍼티와 프로토타입 간의 연결을 설정

Object.setPrototypeOf(me, parent);
// me.__proto__ = parent; 와 같다

me.sayHello(); // Hi! My name is Lee
```

프로토타입으로 교체한 객체 리터럴에 constructor 프로퍼티를 추가하고 생성자 함수의 prototype 프로퍼티를 재설정하여 파괴된 생성자 함수와 프로토타입 간의 연결을 되살린다

## 둘의 차이

생성자 함수에 의한 프로토타입 교체는 생성자 함수의 prototype 프로퍼티가 교체된 프로토타입을 가리킨다

인스턴스에 의한 프로토타입 교체는 생성자 함수의 prototype 프로퍼티가 교체된 프로토타입을 가리키지 않는다
