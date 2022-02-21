# 일등 함수

일등 함수 기능을 제공하는 언어에서 함수는 '함수 표현식'이라는 일종의 값이다 (변수에 담을 수 있다)

## 콜백 함수

함수 표현식을 매개변수로 받을 수 있다

매개변수 형태로 동작하는 함수를 콜백 함수라고 한다

```ts
const f = (callback: () => void): void => callback()
```

예

```ts
const init = (callback: () => void): void => {
  callback() // hello
}

init(() => console.log("hello"))
```

## 중첩 함수

함수형 언어에서 함수는 변수에 담긴 함수 표현식이므로 함수 안에 또 다른 함수를 중첩해서 구현할 수 있다

예

```ts
const calc = (value: number, cb: (number) => void): void => {
  let add = (a, b) => a + b
  
  add(1, 2)
}
```

## 고차 함수와 클로저

고차 함수는 또 다른 함수를 반환하는 함수이다

함수형 언어에서 함수는 단순히 함수 표현식이라는 값으로 다른 함수를 반환할 수 있다

```ts
const add1 = (a: number, b: number): number => a + b // 보통 함수
const add2 = (a: number): (number) => number => (b: number): number => a + b // 고차 함수
```

예

```ts
const add = (a: number): (number) => number => (b: number): number => a + b
const result = add(1)(2)
```

같은 기능

```ts
type NumberToNumberFunc = (number) => number
const add = (a: number): NumberToNumberFunc => {
  const _add: NumberToNumberFunc = (b: number): number => {
    return a + b // 클로저
  }
  return _add
}

let fn: NumberToNumberFunc = add(1)

let result = fn(2)

console.log(result) // 3
console.log(add(1)(2)) // 3
```

_add 함수의 관점에서 a는 외부에 선언된 변수이다

고차 함수는 클로저 기능이 반드시 필요하다

함수의 차수에 맞도록 호출 연산자를 사용해야 함수가 값을 얻을 수 있다