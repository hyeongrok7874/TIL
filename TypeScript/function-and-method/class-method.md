# 클래스 메서드

## function 함수와 this 키워드

function 키워드로 만든 함수는 Function이란 클래스의 인스턴스, 즉 함수는 객체다

TS에서는 function 키워드로 만든 함수에 this 키워드를 사용할 수 있다

반면에 화살표 함수에는 this 키워드를 사용할 수 없다

## 메서드

function으로 만든 함수 표현식을 담고 있는 속성

```ts
class A {
  value: number = 1
  method: () => void = function(): void {
    console.log(`value: ${this.value}`)
  }
}

let a: A = new A
a.method() // value: 1
```

## 클래스 메서드 구분

클래스 속성 중 함수 표현식을 담는 속성은 function 키워드를 생략할 수 있게 하는 단축 구문을 제공한다

```ts
class B {
  constructor(public value: number = 1){}
  method(): void {
    console.log(`value: ${this.value}`)
  }
}

let b: B = new B(2)
b.method() // value: 2
```

## 정적 메서드

메서드 또한 속성으로 이름 앞에 static 수정자를 붙여 정적 메서드를 만들 수 있다

'클래스 이름. 정적 메서드()' 형태로 호출한다

```ts
class C {
  static whoAreYou(): string {
    return `I'm class C`
  }
}

console.log(C.whoAreYou()) // I'm class C
```

## 메서드 체인

객체의 메서드를 이어서 계속 호출하는 방식

TS로 메서드 체인을 구현하려면 메서드가 항상 this를 반환하게 한다

```ts
class calculator {
  constructor (public value: number = 0) {}
  add(value: number) {
    this.value += value
    return this
  }
  multiply(value: number) {
    this.value *= value
    return this
  }
}

let calc = new Calculator
let result = calc.add(1).add(2).multiply(3).multiply(4).value
console.log(result) // (0 + 1 + 2) * 3 * 4 = 36
```