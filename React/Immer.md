# Immer

상태를 업데이트 할 때, 불변성을 신경쓰지 않으면서 업데이트를 해주면 Immer가 불변성 관리를 대신 해준다

## 사용법

produce 함수를 가져와 사용한다

```jsx
import produce from "immer";
```

produce의 첫 번째 파라미터에는 수정하고 싶은 상태, 두 번째 파라미터에는 업데이트 정의 함수를 넣는다

```jsx
const state={
  number: 1,
  dontChangeMe: 2
};

const nextState = produce(state, draft => {
  draft.number += 1;
});

console.log(nextstate) // {number: 2, dontChangeMe: 2}
```

두번째 파라미터에 넣는 함수에서는 불변성에 신경쓰지 않아도 알아서 처리해준다

produce 함수에 두 개의 파라미터를 넣게 된다면 첫번째 파라미터의 상태의 불변성을 유지하며 새로운 상태를 만들어 주지만

첫번째 파라미터를 생략 후 바로 업데이트 함수를 넣어주게 된다면 반환 값이 새로운 상태가 아닌 상태를 업데이트 해주는 함수가 된다

## 주의 

Immer는 편하지만 성능적으로는 사용하지 않은 코드가 조금 더 빠르다