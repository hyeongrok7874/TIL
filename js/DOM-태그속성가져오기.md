# 태그 속성 가져와서 수정

## getAttribute(), setAttribute()

```js
document.querySelector("노드").getAttribute("속성 노드");
document.querySelector("노드").setAttribute("속성 노드", 속성 값);
```

> getAttribute() : 속성에 접근한다 <br>
> setAttribute() : 속성 값을 바꾼다 

## 함수 대신 속성 사용하기

```js
노드.소스 = 속성 값;
```