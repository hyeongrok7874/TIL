# jsx

JavaScript를 확장한 문법

JSX는 React “엘리먼트(element)” 를 생성합니다

컴포넌트 파일에서 XML 형태로 코드를 작성하면 babel이 JSX를 JS로 변환한다

## 규칙

### 태그는 꼭 닫혀야 한다

태그와 태그 사이에 내용이 들어가지 않을 때에는, Self Closing 태그로 닫아준다

```jsx
<Hello />
```

### 태그는 감싸져야한다

두개 이상의 태그는 무조건 하난의 태그로 감싸져있어야 한다.

```jsx
const App = () => {
  return (
    <div>
      <Hello />
      <div>안녕히계세요</div>
    </div>

    // 아래와 같이 감싸는 태그가 없을 시 오류가 발생한다
    // <Hello />
    // <div>안녕히계세요</div>
  );
}
```

좋지 않은 상황에 대비하여 Fragment가 존재한다

```jsx
const App = () => {
  return (
    <>
      <Hello />
      <div>안녕히계세요</div>
    </>
  );
}
```

위는 Fragment이다. 

Fragment는 브라우저 상에서 따로 별도의 엘리먼트로 나타나지 않는다

### JSX 안에 JS 표현식 사용하기

JSX 내부에 JS 표현식을 사용해야 할 때에는 { }로 감싸서 보여준다

```jsx
const App = () => {
  const name = 'react'; 
  return (
    <>
      <Hello />
      <div>{name}</div>
    </>
  )
}
```

### style

인라인 스타일은 객체 형태로 작성을 해야한다

"-"로 구분되어 있는 이름들은 camelCase 형태로 네이밍 해주어야 한다.

```backgroung-color -> backgroundColor```

**jsx에서 style 적용**

```jsx
const App = () => {
  const style = {
    backgroundColor: 'black',
    color: 'aqua',
    fontSize: 24, // 기본 단위 px
    padding: '1rem' // 다른 단위 사용 시 문자열로 설정
  } 

  return (
    <div style={style}></div>
  )
}
```

### className

CSS class를 설정 할 때 ```class=```이 아닌 ```className=``` 으로 해주어야 한다

**css파일로 적용**

```jsx
import '~~~.css';

const App = () => {
  return (
    <div className="style"></div>
  )
}
```

```css
.style{
  /* style */
}
```

### 주석

```jsx
{/* 이런 형태로 */}
```

중괄호로 감싸야 주석처리가 된다

열리는 태그 내부에서는 

```Jsx
<Hello 
  //이런 형태도 가능하다 
/>
```

### jsx 속성 정의

```jsx
const element = <div tabIndex="0"></div>;
```

속성에 따옴표를 이용해 문자열 리터럴을 정의할 수 있습니다.

```jsx
const element = <img src={user.avatarUrl}></img>;
```

중괄호를 사용하여 어트리뷰트에 JavaScript 표현식을 삽입할 수도 있습니다.

따옴표(문자열 값에 사용) 또는 중괄호(표현식에 사용) 중 하나만 사용

### 주입 공격 방지

```jsx
const title = response.potentiallyMaliciousInput;
// 이것은 안전합니다.
const element = <h1>{title}</h1>;
```

기본적으로 React DOM은 JSX에 삽입된 모든 값을 렌더링하기 전에 이스케이프 한다

모든 항목은 렌더링 되기 전에 문자열로 변환된다. 

XSS (cross-site-scripting) 공격을 방지할 수 있다.

#### XSS

사이트 간 스크립팅

웹사이트 관리자가 아닌 이가 웹 페이지에 악성 스크립트를 삽입할 수 있는 취약점

---------------------------------------------------------------------

## Babel

Babel은 ECMAScript 2015+ 코드를 이전 JavaScript 엔진에서 실행할 수 있는 이전 버전과 호환되는 JavaScript 버전으로 변환하는 데 주로 사용되는 무료 오픈 소스 JavaScript 트랜스컴파일러입니다. 

자바스크립트의 문법을 확장해주는 도구입니다. 

아직 지원되지 않는 최신 문법이나, 편의상 사용하거나 실험적인 자바스크립트 문법들을 정식 자바스크립트 형태로 변환해줌으로서 구형 브라우저같은 환경에서도 제대로 실행 할 수 있게 해주는 역할을 합니다.

### 객체 표현

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