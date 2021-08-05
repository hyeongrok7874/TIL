# DOM Access Functions

## getElementById()

```js
document.getElementById("Id 이름");
```

DOM 요소를 id 선택자로 접근하는 함수

## getElementsByClassName()

```js
document.getElementsByClassName("클래스 이름");
```

DOM 요소를 class 값으로 찾아내는 함수

## getElementsByTagName()

```js
document.getElementsByTagName("태그 이름");
```

DOM 요소를 태그 이름으로 찾아내는 함수

## querySelector()

```js
document.querySelector("이름");
```

DOM 요소를 다양한 방법으로 찾아주는 함수<br>
class 선택자나 태그 이름 사용 시 여러 요소 중 첫 번째 요소에만 접근 가능

## querySelectorAll()

```js
document.querySelectorAll("이름");
```

DOM 요소를 다양한 방법으로 찾아주는 함수<br>
같은 이름의 모든 요소들에 접근 가능


## getElementById() vs querySelector()

이름에 Element(s)가 들어간 함수는 요소 노드까지만 접근할 수 있다<br>
반면에 query가 들어간 함수는 요소 노드 뿐만 아니라 텍스트 노드와 속성 노드까지 접근 가능하다