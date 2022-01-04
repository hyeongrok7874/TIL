# Context API

프로젝트 안에서 전역적으로 사용할 수 있는 값을 관리 할 수 있다

이 값은 꼭 상태가 아니어도 된다

함수 일 수도 있고, 어떤 외부 라이브러리 인스턴스, DOM일 수도 있다

## 사용법

React.createContext() 함수로 만든다

```jsx
const UserDispatch = React.createContext(null);
```

Context를 만들면, Context 안에 Provider 라는 컴포넌트가 있다

이 컴포넌트로 Context의 값을 정할 수 있다

이 컴포넌트를 사용할 때, ```value```라는 값을 설정해주면 된다.

```jsx
<UserDispatch.Provider value={dispatch}>...</UserDispatch.Provider>
```

Provider에 의해 감싸진 컴포넌트 중 어디에서나 Context의 값을 조회해서 사용할 수 있다

## 내보내기

```jsx
export const UserDispatch = React.createContext(null);
```

위같이 내보내면

```jsx
import {UserDispatch} from "./App"
```

위같이 불러올 수 있다

## useContext

만든 Context를 조회할 수 있다

```jsx
const dispatch = useContext(UserDispatch);
```