# 순수 함수와 배열

함수형 프로그래밍에서 함수는 순수 함수라는 조건을 만족해야 한다

## 순수 함수

부수 효과가 없는 함수 (<-> 불순 함수)

부수 효과 : 함수가 가진 고유한 목적 이외에 다른 효과가 나타나는 것

함수형 프로그래밍에서 발생하는 부수 효과는 함수를 순수 함수 형태로 작성해야만 제거할 수 있다

### 조건

- 함수 몸통에 입출력 관련 코드가 없어야한다
- 함수 몸통에서 매개변숫값을 변경시키지 않는다(즉, 매개변수는 const나 readonly 형태로만 사용한다)
- 함수는 몸통에서 만들어진 결과를 즉시 반환한다
- 함수 내부에 전역 변수나 정적 변수를 사용하지 않는다
- 함수가 예외를 발생기키지 않는다
- 함수가 콜백 함수로 구현되었거나 함수 몸통에 콜백 함수를 사용하는 코드가 없다
- 함수 몸통에 Promise와 같은 비동기 방식으로 동작하는 코드가 없다

## 타입 수정자 readonly

readonly 타입으로 선언된 매개변숫값을 변경하는 시도가 있으면 문제가 있음을 알려준다

인터페이스, 클래스, 함수의 매개변수 등 const 키워드 없이 사용하므로 readonly 타입 수정자가 필요하다

```ts
function forcePure(array: readonly number[]) {
  array.push(1) // 불가능
}
```

## 불변과 가변

- 불변 변수 - 변수가 const나 readonly를 명시하고 있으면 변숫값은 초깃값을 항상 유지한다
- 가변 변수 - const나 readonly를 명시하지 않은 변수

## 깊은 복사와 얕은 복사

복사 : 어떤 변숫값을 다른 변숫값으로 설정하는 것

순수 함수를 구현할 때는 매개변수가 불변성을 유지해야 하므로 깊은 복사를 실행해야한다

- 깊은 복사 : 대상 변숫값이 바뀔 때 원본 변숫값은 그대로인 형태로 동작
- 얕은 복사 : 대상 변숫값이 바뀔 때 원본 변숫값도 바뀌는 형태로 동작 (객체와 배열은 얕은 복사 방식으로 동작한다)

## 전개 연산자와 깊은 복사

전개 연산자를 사용해 배열을 복사하면 깊은 복사를 할 수 있다

```ts
const oArray = [1, 2, 3, 4]
const deepCopiedArray = [...oArray]
deepCopiedArray[0] = 0
console.log(oArray, deepCopiedArray) // [1, 2, 3, 4] [0, 2, 3, 4]
```

## 배열의 sort 메서드를 순수 함수로 구현

배열의 아이템을 오름차순 혹은 내림차순으로 정렬하는 Array 클래스의 sort 메서드는 원본 배열의 내용을 변경한다

```ts
const pureSort = <T>(array: readonly T[]): T[] => {
  let deepCopied = [...array]
  return deepCopied.sort()
}

let beforeSort = [6, 2, 9, 0]
const afterSort = pureSort(beforeSort)
console.log(beforeSort, afterSort) // [6, 2, 9, 0] [0, 2, 6, 9]
```

위 함수는 원본 배열을 변경하지 않으면서 내용이 정렬된 새로운 배열을 얻을 수 있다

## 배열의 filter 메서드와 순수한 삭제

splice 메서드는 원본 배열의 내용을 변경하므로 순수 함수에서는 사용할 수 없다

```ts
const pureDelete = <T>(array: readonly T[], cb: (val: T, index?: number) => boolean): T[] => 
  array.filter((val, index) => cb(val, index) == false)

const mixedArray: object[] = [
  [], {name: 'Jack'}, {name: 'Jane', age: 32}, ['description']
]

const objecsOnly: object[] = pureDelete(mixedArray, (val) => Array.isArray(val))
console.log(mixedArray, objectsOnly)
// [[], {name: 'Jack'}, {name: 'Jane', age: 32}, ['description']]
// [{name: 'Jack'}, {name: 'Jane', age: 32}]
```

위 함수는 원본 배열을 훼손하지 않으면서 삭제가 가능하다

## 가변 인수 함수와 순수 함수

함수를 호출할 때 전달하는 인수의 개수를 제한하지 않는 것을 가변 인수라 한다

```ts
const mergedArray: string[] = mergeArray(
  ['Hello'], ['World']
)

console.log(mergedArray) // ['Hello', 'World']
```

위 같이 작동하는 함수를 '가변 인수 함수'라 한다

mergeArray 함수를 구현해보자

매개변수 arrays 앞의 ...은 가변 인수를 표현하는 구문이다

```ts
const mergeArray = (...arrays) => {}
```

제네릭 타입으로 타입에 상관 없이 동작하게 한다

```ts
const mergeArray = <T>(...arrays) => {}
```

함수를 호출할 때 전달하는 값은 모두 배열이다

```ts
const mergeArray = <T>(...arrays: T[][]) => {}
```

출력은 T[] 형태의 배열을 반환해야 한다

```ts
const mergeArray = <T>(...arrays: T[][]): T[] => {}
```

순수 함수로 구현하기 위해 매개변수 타입 앞에 readonly 키워드를 추가한다

```ts
const mergeArray = <T>(...arrays: readonly T[][]): T[] => {}
```

mergeArray 함수 구현

```ts
const mergeArray = <T>(...arrays: readonly T[][]): T[] => {
  let result: T[] = []
  for(let index=0; index < arrays.length; index++){
    const array: T[] = arrays[index]
    result = [...result, ...array]
  }
  return result
}

const mergedArray: string[] = mergeArray(
  ['Hello'], ['World']
)

console.log(mergedArray) // ['Hello', 'World']
```