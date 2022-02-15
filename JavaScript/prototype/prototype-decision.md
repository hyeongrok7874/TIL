# 객체 생성 방식과 프로토타입의 결정

## 객체 생성 방식

- 객체 리터럴
- Object 생성자 함수
- 생성자 함수
- Object.create 메서드
- 클래스(ES6)

추상 연산 OrdinaryObjectCreate에 의해 생성된다

프로토타입은 추상 연산 OrdinaryObjectCreate에 전달되는 인수에 의해 결정된다

이 인수는 객체가 생성되는 시점에 객체 생성 방식에 의해 결정된다

## 객체 리터럴에 의해 생성된 객체의 프로토타입

JS 엔진은 객체 리터럴을 평가하여 객체를 생성할 때 OrdinaryObjectCreate을 프로토타입 Object.prototype이 전달되어 호출한다

**객체 리터럴에 의해 생성되는 객체의 프로토타입은 Object.prototype이다**

Object.prototype 객체를 상속받음으로 Object.prototype의 프로퍼티와 메서드를 자유롭게 사용할 수 있다

## Object 생성자 함수에 의해 생성된 객체의 프로토타입

**Object 생성자 함수에 의해 생성되는 객체의 프로토타입은 Object.prototype이다.**

추상 연산 OrdinaryObjectCreate에 프로토타입 Object.prototype이 전달되어 호출된다

객체 리터럴에 의해 생성된 객체와 동일한 구조를 갖는다

Object.prototype을 프로토타입으로 갖게 되며, Object.prototype을 상속받는다.

### 객체 리터럴과 차이

- 객체 리터럴 : 객체 리터럴 내부에 프로퍼티를 추가한다
- Object 생성자 함수 : 일단 빈 객체를 생성한 후 프로퍼티를 추가해야 한다

## 생성자 함수에 의해 생성된 객체의 프로토타입

**생성자 함수에 의해 생성되는 객체의 프로토타입은 생성자 함수의 prototype 프로퍼티에 바인딩되어 있는 객체다**

추상연산 OrdinaryObjectCreate에 생성자 함수의 prototype 프로퍼티에 바인딩되어 있는 객체가 전달되어 호출된다

프로토타입은 객체로 프로토타입에도 프로퍼티를 추가/삭제할 수 있다.

추가/삭제된 프로퍼티는 프로토타입 체인에 즉각 반영된다.