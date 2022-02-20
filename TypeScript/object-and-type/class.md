# 클래스

## 선언문

```ts
class 클래스 이름{
  [private | protected | public] 속성 이름[?]: 속성 타입[...]
}
```

## 접근 제한자

생략 시 public으로 간주

- public
- private
- protect

## 생성자

클래스는 constructor(생성자)라는 특별한 메서드를 포함한다

생성자의 매개변수에 접근 제한자를 붙이면 해당 매개변수의 이름을 가진 속성이 클래스에 선언된 것처럼 동작한다

```ts
class Person {
  constructor(public name: string, public age?: number) {}
}

// 같다
class Person2 {
  name: string
  age?: number
}
```

## 인터페이스 구현

```ts
class 클래스 이름 implements 인터페이스 이름 {
  ...
}
```

인터페이스는 규약에 불과할 뿐 물리적으로 해당 속성을 만들지 않는다

클래스 몸통에는 반드시 인터페이스가 정의하고 있는 속성을 멤버 속성으로 포함해야 한다

```ts
interface IPerson {
  name: string
  age?: number
}

class Person implements IPerson {
  name: string
  age: number
}
```

## 추상 클래스

abstract 키워드를 class 키워드 앞에 붙여서 만든다

자신의 속성이나 메서드 앞에 abstract를 붙여 나를 상속하는 다른 클래스에서 이 속성이나 메서드를 구현하게 한다

```ts
abstract class 클래스 이름 {
  abstract 속성 이름: 속성 타입
  abstract 메서드 이름() {}
}
```

## 상속

extends 키워드를 사용해 상속 클래스를 만든다

부모 클래스의 생성자를 super 키워드로 호출할 수 있다

```ts
class 상속 클래스 extends 부모 클래스 { ... }
```

## static 

```ts
class 클래스 이름 {
  static 정적 속성 이름: 속성 타입
}
```

```클래스 이름.정적 속성 이름``` 형태의 점 표기법으로 값을 얻거나 설정한다