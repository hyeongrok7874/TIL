# map

map함수는 callbackFunction을 실행한 결과를 가지고 새로운 배열을 만들 때 사용한다.

## 사용방법

```js
array.map(callbackFunction(currenValue, index, array), thisArg)
```

- currentValue : 배열 내 현재 값
- index : 배열 내 현재 값의 인덱스
- array : 현재 배열
- thisArg : callbackFunction 내에서 this로 사용될 값