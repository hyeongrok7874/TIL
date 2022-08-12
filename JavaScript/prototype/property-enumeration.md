# 프로퍼티 열거

## for ... in

```js
for (변수선언문 in 객체) { ... }
```

`for ... in` 문은 객체의 프로퍼티 개수만큼 순회하며 `for ... in` 문의 변수 선언문에서 선언한 변수에 프로퍼티 키를 할당한다

`for ... in` 문은 in 연산자처럼 순회 대상 객체의 프로퍼티뿐만 아니라 상속받은 프로토타입의 프로퍼티까지 열거한다.

`for ... in` 문은 객체의 프로토타입 체인 상에 존재하는 모든 프로토타입의 프로퍼티 중에서 프로퍼티 어트리뷰트 [[Enumerable]]의 값이 true인 프로퍼티를 순회하며 열거한다.

```js
const sym = Symbol();
const obj = {
  a: 1,
  [sym]: 10,
};

for (const key in obj) {
  console.log(key + ": " + obj[key]);
}
// a: 1
```

`for ... in` 문은 프로퍼티 키가 심벌인 프로퍼티는 열거하지 않는다.

상속받은 프로퍼티는 제외하고 객체 자신의 프로퍼티만 열거하려면 Object.prototype.hasOwnProperty 메서드를 사용하여 객체 자신의 프로퍼티인지 확인해야 한다.

```js
const person = {
  name: "hyeongrok",
  address: "gwangju",
  __proto__: { age: 18 },
};

for (const key in person) {
  if (!person.hasOwnProperty(key)) continue;
  console.log(key + ": " + person[key]);
}
// name: hyeongrok
// address: gwangju
```

`for ... in` 문은 프로퍼티를 열거할 때 순서를 보장하지 않으므로 주의해야 한다.

하지만 대부분의 모던 브라우저는 순서를 보장하고 숫자(사실은 문자열)인 프로퍼티 키에 대해서는 정렬을 실시한다.

배열에는 `for ... in` 문을 사용하지 말고 인반적인 `for` 문이나 `for ... of` 문 또는 `Array.prototype.forEach` 메서드를 사용하기를 권장한다.

배열도 객체이므로 프로퍼티와 상속받은 프로퍼티가 포함될 수 있다.

```js
const arr = [1, 2, 3];
arr.x = 10;

for (const i in arr) {
  // 프로퍼티인 x도 출력된다.
  console.log(arr[i]); // 1 2 3 10
}

for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]); // 1 2 3
}

// forEach 메서드는 요소가 아닌 프로퍼티는 제외한다.
arr.forEach((v) => console.log(v)); // 1 2 3

// for ... of는 변수 선언문에서 선언한 변수에 키가 아닌 값을 할당한다.
for (const value of arr) {
  console.log(value); // 1 2 3
}
```

## Object.keys/values/entries

객체 자신의 고유 프로퍼티만 열거하기 위해서는 `for ... in` 문을 사용하는 것보다 `Object.keys/values/entries` 메서드를 사용하는 것을 권장한다.

- Object.keys() : 객체 자신의 열거 가능한 프로퍼티 키를 배열로 반환한다.
- Object.values() : 객체 자신의 열거 가능한 프로퍼티 값을 배열로 반환한다. (ES8 도입)
- Object.entries() : 객체 자신의 열거 가능한 프로퍼티 키와 값의 쌍의 배열을 배열로 반환한다. (ES8 도입)

```js
const person = {
  name: "hyeongrok",
  address: "gwangju",
  __proto__: { age: 18 },
};

console.log(Object.keys(person)); // ["name", "address"]
console.log(Object.values(person)); // ["hyeongrok", "gwangju"]
console.log(Object.entries(person)); // [["name", "hyeongrok"], ["address", "gwangju"]]
```
