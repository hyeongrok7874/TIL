# 함수 구현 기법

## 매개변수 기본값 지정하기

함수 호출 시 인수를 전달하지 않더라도 매개변수에 어떤 값을 설정하고 싶을 때 사용한다

```ts
(매개변수: 타입 = 매개변수 기본값)
```

## 객체 생성 시 값 부분을 생략

매개변수의 이름과 똑같은 이름의 속성을 가진 객체를 만들 수 있다

```ts
const makePerson = (name: string, age: number) => {
  const person = {name, age} // {name: name, age: age}의 단축 표현
}
```

## 객체를 반환하는 화살표 함수

컴파일러가 {}를 객체로 해석하게 하려면 객체를 소괄호로 감싸주어야 한다

```ts
const makePerson = (name: string, age: number = 10): person => ({name, age})
```

## 매개변수 비구조화 할당문

매개변수도 변수의 일종으로 비구조화 할당이 가능하다

```ts
type Person = {name: string, age: number}

const printPerson = ({name, age}: Person): void => 
  console.log(`name: ${name}, age: ${age}`)

printPerson({name: 'Jack', age: 10}) // name: Jack, age: 10
```

## 색인 키와 값으로 객체 만드기

색인 가능 타입을 정의하기 위해서는 색인에 접근할 때 사용하는 대괄호로 객체의 색인 시그니쳐를 적어야한다

```ts
const makeObject = (key, value) => ({[key]: value})
```

TS에서는 {[key]: value} 형태의 타입을 '색인 가능 타입'이라고 하며 타입을 다음처럼 명시한다

```ts
type KeyType = {
  [key: string]: string
}

const makeObject = (key: string, value: string): keyType => ({[key]: value})

console.log(makeObject('name', 'Kim')) // {name: 'Kim'}
```