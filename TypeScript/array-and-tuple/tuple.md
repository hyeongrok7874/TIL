# 튜플

수정이 불가능한 여러 객체를 담는 집합

JS에서는 튜플이 없으며 단순히 배열의 한 종류로 취급된다

```ts 
const tuple: [boolean, string] = [true, 'the result is ok']
```

## 튜플에 타입 별칭 사용

```ts
type ResultType = [boolean, string]

const doSomething = (): ResultType => {
  try {
    throw new Error('Some error occurs...')
  } catch(e) {
    return [false, e.message]
  }
}
```

## 튜플에 적용하는 비구조화 할당

```ts
const [result, errorMessage] = doSomething()
console.log(result, errorMessage) // false Some error occurs...
```