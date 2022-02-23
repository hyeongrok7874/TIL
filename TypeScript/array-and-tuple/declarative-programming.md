# 선언형 프로그래밍과 배열

## 명령형 프로그래밍

- 입력 데이터 얻기
- 입력 데이터 가공해 출력 데이터 생성
- 출력 데이터 출력

여러 개의 데이터를 대상으로 할 때 for 문을 사용해서 구현한다

시스템 자원의 효율을 최우선으로 생각한다

## 선언형 프로그래밍

- 문제를 푸는 데 필요한 모든 데이터 배열에 저장
- 입력 데이터 배열을 가공해 출력 데이터 배열 생성
- 출력 데이터 배열에 담긴 아이템 출력

범용으로 구현된(혹은 언어가 제공하는) 함수를 재사용하면서 문제를 해결한다

## 1부터 100까지 더하기

### 명령형

```ts
let sum = 0
for(let val = 1; val <= 100;)
  sum += val++
console.log(sum) //5050
```

### 선언형 - fold: 배열 데이터 접기

배열 데이터를 가공해 하나의 값을 생성할 때 사용한다

배열의 아이템 타입이 T라고 할 때 배열은 T[]로 표현할 수 있는데, 폴드 함수는 T[] 타입 배열을 가공해 T 타입 결과를 만들어 준다

```ts
const range = (from: number, to: number): number[] => 
  from < to ? [from, ...range(from + 1, to)] : []

const fold = <T>(array: T[], callback: (result: T, val: T) => T, initValue: T) => {
  let result: T = initValue
  for(let i = 0; i < array.length; ++i){
    const value = array[i]
    result = callback(result, value)
  }
  return result
}

let numbers: number[] = range(1, 100+1) // 입력 데이터 생성

let result = fold(numbers, (result, value) => result + value, 0) // 입력 데이터 가공
console.log(result) // 5050
```

## 1에서 100까지 홀수 합 구하기

### 명령형

```ts
let oddSum = 0
for(let val = 1; val <= 100; val += 2)
  oddSum += val
console.log(oddSum) // 2500
```

### 선언형 - filter: 조건에 맞는 아이템만 추려내기

입력 배열을 가공해 조건에 맞는 값만 추려낸다

```ts
const filter = <T>(array: T[], callback: (value: T, index?: number) => boolean): T[] => {
  let result: T[] = []
  for(let index: number = 0; index < array.length; ++index) {
    const value = array[index]
    if(callback(value, index))
      result = [...result, value]
  }
  return result
}

let numbers: number[] = range(1, 100+1)
const isOdd = (n: number): boolean => n % 2 != 0
let result = fold(
  filter(numbers, isOdd),
  (result, value) => result + value, 0)
console.log(result) // 2500
```

## 1에서 100까지 짝수의 합 구하기

### 명령형

```ts
let evenSum = 0
for(let val = 0; val <= 100; val += 2)
  evenSum += val
console.log(evenSum) // 2550
```

### 선언형 - filter: 조건에 맞는 아이템만 추려내기

```ts
let numbers: number[] = range(1, 100+1)
const isEven = (n: number): boolean => n % 2 == 0
let result = fold(
  filter(numbers, isEven),
  (result, value) => result + value, 0)
console.log(result) // 2550
```

## 제곱의 합 구하기

### 명령형

```ts
let spareSum = 0
for(let val = 1; val <= 100; ++val)
  squareSum += val * val
console.log(squareSum) // 338350
```

### 선언형 - map: 배열 데이터 가공하기

데이터를 가공한다

입력 타입과 출력 타입이 다를 수 있음을 고려해야 한다

```ts
const map = <T, Q>(array: T[], callback: (value: T, index?: number) => Q): Q[] => {
  let result: Q[] = []
  for(let index = 0; index < array.length; ++index) {
    const value = array[index]
    result = [...result, callback(value, index)]
  }
  return result
}

let numbers: number[] = range(1, 100+1)
let result = fold(
  map(numbers, value => value * value),
  (result, value) => result + value, 0)
console.log(result) // 338350
```