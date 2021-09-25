# SCSS

## SCSS 란?

CSS를 편리하게 이용할 수 있도록 도와주며 추가 기능도 있는 확장판

## 동작 원리

Sass자체로 브라우저에 적용하는 것이 아니라 CSS를 확장해서 쉽고 편리하게 쓰기 위해 쓰는 스크립팅 언어이다

따라서 Sass로 작성한 코드는 컴파일을 해서 일반 CSS의 문법으로 바꾼 뒤 적용한다

## 사용 이유

- 변수의 사용
- 조건문과 반복문
- Import
- Nesting
- Mixin
- Extend/Inheritance

## SASS와의 차이

SASS보다 SCSS가 뒤에 나왔고 여러가지 문법의 차이가 있지만 SCSS가 더 넓은 범용성과 CSS의 호환성 등의 장점으로 SCSS를 사용하기를 권장한다.

## 문법 예시

```HTML
<ul class='list'>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</div>
```

위 같은 코드가 있을 때

CSS
```CSS
.list {
  width: 100px;
  float: left;
  }
li {
  color: red;
  background: url("./image.jpg");
  }
li:last-child {
  margin-right: -10px;
  }
```

SCSS
```SCSS
.list {
  width: 100px;
  float: left;
  li {
    color: red;
    background: url("./image.jpg");
    &:last-child {
      margin-right: -10px;
    }
  }
}
```