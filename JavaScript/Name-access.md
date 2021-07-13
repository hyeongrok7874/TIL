# 폼 요소에 접근하기

## id, class 사용

> getElement---() 또는 querySelector---() 사용

## name 값 사용

```js
document.name.name;
document.forms["name"].elements["name"];
```

> 폼 태그의 name 속성과 폼 태그에 포함된 폼 요소에도 name 속성이 있어야 한다.

## 폼 배열 사용

```js
document.forms;
//폼 요소에 접근
document.forms[0].elements;
//폼 태그 안의 요소들에 접근
document.forms[0].elements[0].value;
//폼 태그 안의 요소의 값을 가져옴
```

