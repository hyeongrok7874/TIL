# 배열

JS의 배열은 Array 클래스의 인스턴스이다

```ts
let 배열 이름 = new Array(배열 길이)
```

배열의 담긴 각각의 값을 아이템 또는 원소라고 한다

## [ ] 단축 구문

```ts
let numbers = [1, 2, 3]

console.log(numbers) // [ 1, 2, 3 ]
```

## 배열은 객체다

JS에서 배열은 다른 언어와 다르게 객체다

배열은 Array 클래스의 인스턴스인데, 클래스의 인스턴스는 객체이기 때문이다

Array 클래스는 배열을 사용하는 데 필요한 여러 메서드를 제공한다

## 배열의 타입

TS에서 배열의 타입은 '아이템 타입[]' 이다

```ts
let numArray: number[] = [1, 2, 3]

type IPerson = {name: string, age?: number}
let personArray: IPerson[] = [{name: 'Jack'}, {name: 'Jane', age: 32}]
```

## 문자열과 배열 간 변환

TS에서는 문자 타입이 없고 문자열의 내용 또한 변경할 수 없다

문자열을 가공하려면 먼저 문자열을 배열로 전환해야 한다

```ts
const split = (str: string, delim: string = ''): string[] => str.split(delim)

console.log(
  split('hello'), // ['h', 'e', 'l', 'l', 'o']
  split('h_e_l_l_o', '_') // ['h', 'e', 'l', 'l', 'o']
)

const join = (strArray: string[], delim: string=''): string => strArray.join(delim)

console.log(
  join(['h', 'e', 'l', 'l', 'o']), // hello
  join(['h', 'e', 'l', 'l', 'o'], '_') // h_e_l_l_o
) 
```

## 인덱스 연산자

배열의 특정 위치에 있는 아이템을 얻는다

```ts
arr[0] // arr 배열의 0 인덱스
```

## 비구조화 할당

배열의 비구조화 할당문에는 객체와 달리 [ ] 기호를 사용한다

```ts
let array: number[] = [1, 2, 3, 4, 5]
let [first, second, third, ...rest] = array
console.log(first, second, third, rest) // 1 2 3 [4, 5]
```

## for ... in 문

for ... in 문은 객체를 대상으로 사용하지만, 배열도 객체이므로 배열에 사용할 수도 있다

```ts
for(변수 in 객체) {
  ...
}
```

for ... in 문은 배열의 인덱스값을 순회한다

for ... in 문에 객체를 사용할 때는 객체가 가진 속성을 대상으로 순회한다

## for ... of 문

```ts
for(let 변수 of 객체) {
  ...
}
```

배열의 아이템값을 대상으로 순회한다

아이템값만 필요할 때는 for ... in 보다 간결하게 구현할 수 있다

```ts
for(let name of ['Jack', 'Jane', 'Steve'])
  console.log(name) // Jack Jane Steve
```

## 제네릭 방식 타입

배열을 다루는 함수를 작성할 때는 number[ ]와 같이 타입이 고정된 함수를 만들기 보다는 T[ ] 형태로 배열의 아이템 타입을 한꺼번에 표현하는 것이 편리하다

타입을 T와 같은 일종의 변수로 취급하는 것을 제네릭 타입이라고 한다


```ts
const arrayLength = <T>(array: T[]): number => array.length
const isEmpty = <T>(array: T[]): boolean => arrayLength<T>(array) == 0

let numArray: number[] = [1, 2, 3]
let strArray: string[] = ['Hello', 'World']

type IPerson = {name: string, age?: number}
let personArray: IPerson[] = [{name: 'Jack'}, {name: 'Jane', age: 32}]

console.log(
  arrayLength(numArray), // 3
  arrayLength(strArray), // 2
  arrayLength(personArray), // 2
  isEmpty([]), // true
  isEmpty([1]) // false
)
```

## 제네릭 함수의 타입 추론

제네릭 형태로 구현된 함수는 원칙적으로는 타입 변수를 명시해 주어야 한다

```ts
함수 이름<타입 변수>(매개변수)
```

타입 변수 부분을 생략 시 타입 추론을 통해 생략된 타입을 찾아낸다

## 제네릭 함수의 함수 시그니처

함수 시그니처의 매개변수 부분에 변수 이름을 기입하고 요구시에는 해석하지 못하는 부분에 변수를 삽입하고 이 변수에 타입을 명시한다

```ts
const error = (cb: (number, number?) => number): void => {}
const fixed = (cb: (a:number, number?) => number): void => {}
```

제네릭 타입의 함수에서의 해결

```ts
const f = <T>(cb: (arg: T, i?: number) => number): void => {}
```

## 전개 연산자

배열을 전개한다

```ts
let array1: number[] = [1]
let array2: number[] = [2, 3]
let mergedArray: number[] = [...array1, ...array2, 4]
console.log(mergedArray) // [1, 2, 3, 4]
```

## range 함수 구현

배열에 전개 연산자를 적용하면 ramda가 제공하는 R.range 같은 함수를 쉽게 만들 수 있다

from에서 to까지 수로 구성된 배열을 생성해준다

```ts
const range = (from: number, to: number): number[] => 
  from < to ? [from, ...range(from + 1, to)] : []

let numbers: number[] = range (1, 9+1)
console.log(numbers) // [1, 2, 3, 4, 5, 6, 7, 8, 9]
```