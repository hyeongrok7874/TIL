# 타입 변환

특정 타입의 변숫값을 다른 타입의 값으로 변환하는 기능

## 타입 단언

JS의 타입 변환 구문과 구분하기 위해 TS에서는 타입 단언이라는 용어를 사용한다

```ts
(<타입>객체)
(객체 as 타입)
```

예

```ts
interface INameable {
  eame: string
};

let obj: object = {name: 'Kim'}

let name1 = (<INameable>obj).name
let name2 = (obj as INameable).name
console.log(name1, name2) // Kim Kim
```

## 타입 변환 용어

### type conversion

type casting과 type coercion을 포함하는 의미

### type casting

명시적 타입 변환

### type coercion

암묵적 타입 변환