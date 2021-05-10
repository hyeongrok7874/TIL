# DOM에 노드를 추가하기

## createElement()

```js
let newP = document.createElement("HTML 태그");
```

> (괄호) 안의 태그에 해당하는 요소 노드를 만들 수 있다.

## createTextNode()

```js
let newText = document.createTextNode("텍스트 노드");
```

> (괄호) 안의 내용을 담고 있는 텍스트 노드를 만들어 저장한다.

## appendChild()

```js
newP.appendChild(newText);
```

> 텍스트 노드를 요소 노드의 자식 노드로 연결하였다.

```js
document.body.appendChild(newP);
```

> newP 노드를 body 노드의 자식 노드로 추가하였다.