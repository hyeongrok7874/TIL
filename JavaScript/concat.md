# concat

concat() 메서드는 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환한다

## 사용법

```array.concat([value1[, value2[, ...[, valueN]]]])```

### 한 배열에 한 배열을 이어 붙여 새 배열 생성

```js
const arr = ['a', 'b', 'c'];
const brr = ['d', 'e', 'f'];
const crr = arr.concat(brr); // crr = ['a', 'b', 'c', 'd', 'e', 'f']
```

### 한 배열에 한 배열 이어붙이기

```js
const arr = ['a', 'b', 'c'];
const brr = ['d', 'e', 'f'];
arr.concat(brr); // arr = ['a', 'b', 'c', 'd', 'e', 'f']
```

## 한 배열에 두 배열 이어 붙이기

```js
const arr = ['a', 'b', 'c'];
const brr = ['d', 'e', 'f'];
const crr = ['g', 'h', 'i'];
arr.concat(brr, crr); // arr = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i']
```

## 한 배열에 값 이어붙이기

```js
const arr = ['a', 'b', 'c'];

arr.concat(1, [2, 3]); // 결과: ['a', 'b', 'c', 1, 2, 3]
```