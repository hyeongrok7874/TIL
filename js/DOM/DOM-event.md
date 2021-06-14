# 이벤트 처리

## HTML 태그 안에서 이벤트 처리기 연결

```html
<img id= "pic" src="" alt="" onclick="function()">
```

## DOM 요소에 이벤트 처리기 연결하기

```html
<img id= "pic" src="" alt="">
<script>
    let pic = document.getElementById("id");
    pic.onclick = function;
```

## addEventListener()

```js
let pic = document.getElementById("id");
pic.addEventListener("이벤트 유형", 함수, 캡처 여부);
```

> 한 요소에 여러 이벤트가 발생했을 때 이를 동시에 처리하는 함수