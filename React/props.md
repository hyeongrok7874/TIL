# props

어떠한 값을 컴포넌트한테 전달해줘야 할 때, 사용한다.

## 기본 사용법

컴포넌트를 사용 할 때 props를 사용하고 싶다면 

```jsx
const App = () => {
  return(
    <Hello name="react" />
  );
}
```

로 props를 넘겨준다

컴포넌트에게 전달된 props는 파라미터로 조회할 수 있다

```jsx
const Hello = () => {
  return(
    <div>안녕하세요 {props.name}</div>
  );
}
```

props 는 객체 형태로 전달되며, 만약 name 값을 조회하고 싶다면 props.name 을 조회하면 됩니다.

## 여러개의 props, 비구조화 할당

props가 여러 개일 경우 함수의 파라미터에서 비구조화 할당을 사용하면 조금 더 간결하게 작성할 수 있다

```jsx
const App = () => {
  return(
    <Hello name="react" color="red" />
  );
}
```

```jsx
const Hello = ({color, name}) => {
  return (
    <div style={{color}}>안녕하세요 {name}</div>
  )
}
```

## defaultProps로 기본값 설정

컴포넌트에 props를 지정하지 않았을 때 기본적으로 사용 할 값을 설정하고 싶다면 컴포넌트에 ```defaultProps``` 라는 값을 설정하면 됩니다

```jsx
const Hello = ({color, name}) => {
  return (
    <div style={{color}}>안녕하세요 {name}</div>
  )
}

Hello.defaultProps = {
  name:'이름없음'
}
```

## props.chidren

태그 사이의 컴포넌트들을 보이게 하기 위해서는 태그에서 props.children을 렌더링 해야한다

```jsx
const Wrapper = ({children}) => {
  render(
    <div>
      {children}
    </div>  
  )
}
```