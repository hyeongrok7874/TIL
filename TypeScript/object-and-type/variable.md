# 변수

## 기본 제공 타입

### JS

- 수: Number
- 불리언: Boolean
- 문자열: String
- 객체: Object

### TS

- 수: number
- 불리언: boolean
- 문자열: string
- 객체: object

## let과 const

```ts
let 변수 이름 [= 초깃값]

const 변수 이름 = 초깃값 // 반드시 초기값을 명시해야함
```

## 타입 주석

타입을 명시해 준다

```ts
let 변수 이름: 타입 [= 초깃값]
const 변수 이름: 타입 = 초깃값
```

let으로 선언한 변숫값은 타입 주석으로 명시한 타입에 해당하는 값으로만 바꿀 수 있다

```ts
let n: number = 1

n = 'a' // 타입 불일치 오류 발생
```

## 타입 추론

타입 주석 부분을 생략할 수 있다

대입 연산자 오른쪽 값에 따라 변수의 타입을 지정한다

이후에 각 변수에는 해당 타입의 값만 저장할 수 있다

```ts
let n = 1 // number 타입
```

## any 타입

값의 타입과 무관하게 어떤 종류의 값도 저장할 수 있다

## undefined 타입

TS의 undefined는 타입이기도 하고 값이기도 한다

undefined 타입으로 선언된 변수는 오직 undefined 값만 가질 수 있다

## 타입 계층

1. any
2. number, boolean, string, object(interface, class)
3. undefined

## 탬플릿 문자열

변수에 담긴 값을 조합해 문자열을 만들 수 있다

백틱으로 문자열을 감싸고, 변수를 ${}로 감싼다

```ts
`${변수 이름}`