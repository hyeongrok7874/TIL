# 조건부 렌더링

특정 조건에 따라 다른 결과물을 렌더링하는 것

## 삼항 연산자

```jsx
const Hello = ({color, name, isSpecial}){
  return(
    <div style={{color}}>
      {isSpecial ? '*' : null}
      안녕하세요 {name}
    </div>
  )
}
```

isSpecial props를 받아와 true 값일때, *을 출력한다

props 이름만 작성하고 값 설정을 생략한다면 true로 설정한 것으로 간주한다

```jsx
<Hello name="react" color="red" isSpecial /> 
// isSpecial은 true이다 
```

## && 이용

```jsx
const Hello = ({color, name, isSpecial}){
  return(
    <div style={{color}}>
      {isSpecial && '*'}
      안녕하세요 {name}
    </div>
  )
}
```

단순히 특정 조건이 true이면 보여주고 아닐 때 에는 숨기는 상황은 ```&&```으로 처리하면 된다

## if 이용

```jsx
const Hello = ({color, name, isSpecial}){
  return(
    <div style={{color}}>
      {isSpecial && '*'}
      안녕하세요 {name}
    </div>
  )
}
```

