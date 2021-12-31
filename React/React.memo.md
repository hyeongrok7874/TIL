# React.memo

컴포넌트의 props가 바뀌지 않았다면, 리렌더링을 방지하여 리렌더링 성능 최적화를 해준다

컴포넌트에서 리렌더링이 필요한 상황에서만 리렌더링을 하도록 설정한다

## 사용법

```jsx
export default React.memo(Component); // 컴포넌트를 export 하며 사용
```

```jsx
const Component = React.memo(() => {
  // 컴포넌트 React.memo를 사용하여 만듬
})
```

## 주의 

렌더링 최적화 하지 않을 컴포넌트에 React.memo를 사용하는 것은, 불필요한 props 비교만 하는 것으로로 실제로 렌더링을 방지할 수 있는 상황이 있는 경우에만 사용해야한다