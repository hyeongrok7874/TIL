# state

컴포넌트의 동적인 값

컴포넌트에서 state는 컴포넌트가 살아있는 동안 변화가 가능한 객체

props는 탑다운 방식으로 내려온 읽기 전용의 데이터의 느낌이라면, state는 컴포넌트가 소유하고 있는 고유의 값

state는 항상 초기 값이 있어야 한다

setState를 통하여 state를 렌더링할 수 있다

## useState

```jsx
const [number, setNumber] = useState(0);
```

상태의 기본값을 useState의 파라미터로 넣어서 호출해준다

함수를 호출하면 배열이 반환된다

여기서 첫번째 원소는 현재 상태, 두번째 원소는 Setter 함수이다. 

```jsx
const up = () => {
  setNumber(number + 1);
}
const down = () => {
  setNumber(number - 1);
}
```

## 이벤트 객체 

이벤트에 등록되는 함수에서는 이벤트 객체 ```e``` 를 파라미터로 받아와서 사용할 수 있다

```jsx
const onChange = (e) => {
  setText(e.target.value);
};
```

이 객체의 e.target은 이벤트가 발생한 DOM인 input DOM을 가르키게된다

이 DOM의 value 값, 즉 ```e.target.value```를 조회하면 현재 input에 입력한 값이 무엇인지 알 수 있다

input의 상태를 관리할 때에는 input 태그의 value 값도 설정 해주어야 상태가 바뀔때 input의 내용도 업데이트 됩니다

useState 에서는 문자열이 아니라 객체 형태의 상태를 관리해주어야 한다

리액트 상태에서 객체를 수정해야 할때에는

```jsx
input[name] = value'
```

이런식으로 직접 수정하면 안된다

새로운 객체를 만들어서 새로운 객체에 변화를 주고, 이를 상태로 사용해야한다

```jsx
setInputs({
  ...inputs,
  [name]: value
})
```

이러한 작업을 불변성을 지킨다고 한다

불변성을 지켜주어야만 리액트 컴포넌트에서 상태가 업데이트가 됐음을 감지 할 수 있고 이에 따라 필요한 리렌더링이 진행된다

기존 상태를 직접 수정하게 되면, 값을 바꿔도 리렌더링이 되지 않는다

리액트에서는 불변성을 지켜주어야만 컴포넌트 업데이트 성능 최적화를 제대로 할 수 있다

**리액트에서 객체를 업데이트하게 될 때에는 기존 객체를 직접 수정하면 안되고, 새로운 객체를 만들어서, 새 객체에 변화를 주어야 된다**