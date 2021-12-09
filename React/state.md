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
