# 배열의 메서드

배열 또한 메서드 체인 방식으로 동작하도록 설계되었다

## filter 메서드

배열의 타입이 T[]일 때 배열의 filter 메서드는 다음과 같은 형태로 설계되어있다

```ts
filter(callback: (value: T, index?: number): boolean): T[]
```

조건에 맞는 아이템을 추려낸다

## map 메서드

배열의 타입이 T[]일 때 배열의 map 메서드는 다음과 같은 형태로 설계되어있다

```ts
map(callback: (value:T, index?: number): Q): Q[]
```

입력 타입과 다른 타입의 배열을 만들 수 있다

## reduce 메서드

배열의 타입이 T[]일 때 배열의 reduce 메서드는 다음과 같은 형태로 설계되어있다

```ts
reduce(callback: (result: T, value: T), initialValue: T): T
```

