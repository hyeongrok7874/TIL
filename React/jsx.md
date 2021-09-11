# jsx

JavaScript를 확장한 문법

## jsx에 표현식 포함하기

JSX의 중괄호 안에는 유효한 모든 JavaScript 표현식을 넣을 수 있습니다

## jsx도 표현식이다

컴파일이 끝나면, JSX 표현식이 정규 JavaScript 함수 호출이 되고 JavaScript 객체로 인식됩니다

## jsx 속성 정의

```jsx
const element = <div tabIndex="0"></div>;
```

속성에 따옴표를 이용해 문자열 리터럴을 정의할 수 있습니다.

```jsx
const element = <img src={user.avatarUrl}></img>;
```

중괄호를 사용하여 어트리뷰트에 JavaScript 표현식을 삽입할 수도 있습니다.

따옴표(문자열 값에 사용) 또는 중괄호(표현식에 사용) 중 하나만 사용

## JSX로 자식 정의

```jsx
const element = <img src={user.avatarUrl} />;
```

태그가 비어있다면 /> 를 이용해 바로 닫아주어야 한다.

```jsx
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

JSX 태그는 자식을 포함할 수 있습니다.

## 주입 공격 방지

```jsx
const title = response.potentiallyMaliciousInput;
// 이것은 안전합니다.
const element = <h1>{title}</h1>;
```

기본적으로 React DOM은 JSX에 삽입된 모든 값을 렌더링하기 전에 이스케이프 한다

모든 항목은 렌더링 되기 전에 문자열로 변환된다. 

XSS (cross-site-scripting) 공격을 방지할 수 있다.

### XSS

사이트 간 스크립팅

웹사이트 관리자가 아닌 이가 웹 페이지에 악성 스크립트를 삽입할 수 있는 취약점

## 객체 표현

Babel은 JSX를 React.createElement() 호출로 컴파일합니다.

```jsx
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```jsx
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```

위 두 예시는 동일하다

React.createElement()는 버그가 없는 코드를 작성하는 데 도움이 되도록 몇 가지 검사를 수행하며, 기본적으로 다음과 같은 객체를 생성합니다.

```jsx
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```

이러한 객체를 “React 엘리먼트”라고 한다.

### Babel

Babel은 ECMAScript 2015+ 코드를 이전 JavaScript 엔진에서 실행할 수 있는 이전 버전과 호환되는 JavaScript 버전으로 변환하는 데 주로 사용되는 무료 오픈 소스 JavaScript 트랜스컴파일러입니다. 