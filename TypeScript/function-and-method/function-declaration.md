# 함수 선언문

```ts
function 함수 이름(매개변수1: 타입1, 매개변수2: 타입2[, ..]) : 반환값 타입 {
  함수 몸통
}
```

## 매개변수와 반환값의 타입 주석 생략

타입이 생략되어 있으면 함수의 구현 의도를 알기 어렵고 잘못 사용하기 쉬움으로 지양하자

## void 타입

값을 반환하지 않는 함수는 반환 타입이 void이다

void는 함수 반환 타입으로만 사용할 수 있다

## 함수 시그니처

함수의 타입을 함수 시그니처라고 한다

```ts
(매개변수1 타입, 매개변수2 타입[, ...]) => 반환값 타입
```

예

```ts
let printMe: (string, number) => void = function (name: string, age: number): void {}
```

매개변수가 없으면 단순히 ()로 표현한다

## 타입 별칭

type 키워드로 기존에 존재하는 타입을 단순히 이름만 바꿔서 사용할 수 있는 기능

```ts
type 새로운 타입 = 기존타입
```

예

```ts
type stringNumberFunc = (string, number) => void
let f: stringNumberFunc = function(a: string, b: number): void {}
let g: stringNumberFunc = function(c: string, b: number); void {}
```

함수 시그니처를 명시하면 매개변수의 개수나 타입, 반환 타입이 다른 함수를 선언하는 잘못을 미연에 방지할 수 있다

## undefined

undefined는 최하위 타입으로 인터페이스를 상속하는 자식 타입으로 간주한다

오류를 방지하기 위해 매개변수 값이 undefined인지 판별하는 코드를 작성해야 한다

## 선택적 매개변수

함수의 매개변수 뒤에도 물음표를 붙일 수 있고, 이를 선택적 매개변수라고 한다

선택적 매개변수가 있는 함수의 시그니처는 타입 뒤에 물음표를 붙인다