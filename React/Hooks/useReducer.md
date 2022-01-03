# useReducer

컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리할 수 있다

상태 업데이트 로직을 컴포넌트 바깥에 작성할 수도 있고 다른 파일에 작성하여 불러와 사용 할 수도 있다

## Reducer

현재 상태와 액션 객체를 파라미터로 받아와서 새로운 상태를 반환해주는 함수이다

```jsx
const reducer = (state, action) => {
  // const nextState = ...
  return nextState;
}
```

reducer 에서 반환하는 상태는 곧 컴포넌트가 지닐 새로운 상태가 된다.

action은 업데이트를 위한 정보를 가지고 있다 (주로 type 값을 지닌 객체 형태로 사용한다)

## useReducer 사용법

```jsx
const [state, dispatch] = useReducer(reduver, initialState);
```

## useState VS useReducer

컴포넌트의 값이 딱 하나이고, 그 값이 단순한 숫자, 문자열 또는 boolean 값이라면 ```useState```가 편하다

컴포넌트에서 관리하는 값이 여러개가 되어 상태의 구조가 복잡해진다면 ```useReducer```가 편할 수 있다