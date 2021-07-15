# 노드 순서 바꾸거나 삭제

## 노드 리스트

querySelectorAll() 함수로 여러 개의 노드를 한꺼번에 가져오면 한꺼번에 저장되는데, 이것을 '노드 리스트' 라고 한다.

## hasChildNodes()

```js
document.querySelectorAll("p")[0].hasChildNodes();
```

자식 노드가 있는지 확인한다.

## childNodes

```js
document.getElementById("nameList").childNodes;
```

현재 노드의 자식 노드에 접근할 수 있다.<br>
요소 노드뿐만 아니라 텍스트 노드나 주석 노드까지 모두 접근할 수 있다.

## children

```js
document.getElementById("nameList").children;
```

요소 노드에만 접근하는 속성.

## parentNode

```js
document.getElementById("nameList").parentNode;
```

현재 노드의 부모 요소 노드를 반환한다.

## insertBefore()

```js
nameList.insertBefore(nameList.children[2], nameList.children[0]);
```

(추가할 노드, 기준 노드) 기준 노드 앞으로 추가할 노드를 추가한다.

## removeChild()

```js
let firstDel = document.querySelectorAll(".del")[0];
let firstP = document.querySelectorAll("p")[0];
firstP.removeChild(firstDel);
```

특정 노드를 삭제 할 수 있다.