# useCallback

특정 함수를 새로 만들지 않고 재사용하고 싶을 때 사용한다

React 컴포넌트 함수 안에 함수가 선언이 되어 있다면 이 함수는 해당 컴포넌트가 랜더링될 때 마다 새로운 함수가 생성된다

useMemo를 기반으로 만들어졌다

## 동작방식

```jsx
const onToggle =  useCallback(
  id => {
    setUsers(
      users.map(user =>
        console.log("function")
      )
    );
  },
  [depsArray]
);
```

첫번째 인자로 넘어온 함수를 두번째 인자로 넘어온 배열 내의 값(deps)이 변경될 때까지 저장해놓고 재사용할 수 있게 해준다

함수 안에서 가장 최근의 값을 참조하기 위해 ```deps```

## 함수형 업데이트

함수형 업데이트를 사용하면 ```deps```를 넣지 않더라도 최신 값을 참조 할 수 있다