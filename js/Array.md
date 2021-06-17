# 배열

## Array 객체로 배열 만들기

```js
let myArray = new Array();
```

 > 초기 값이 없는 배열 선언

 ```js
 let numbers = ["one", "two", "three", "four"];
 let numbers = new Array("one", "two", "three", "four");
 ```

 > 초기 값이 있는 배열 선언 

## Array 객체의 함수

> concat : 기존 배열에 새로운 배열을 추가해 새로운 배열을 만듭니다.<br>
> every : 배열의 모든 요소가 주어진 함수에 대해 true라면 true를 반환하고 그렇지 않으면 false를 반환합니다<br>
> filter : 배열의 요소 중 주어진 필터링 함수에 대해 true인 요소만 골라 새로운 배열을 만듭니다.<br>
> forEach : 배열의 모든 요소에 대해 주어진 함수를 실행합니다.<br>
> indexOf : 주어진 값과 일치하는 값이 있는 배열 요소의 첫 인덱스를 찾습니다.<br>
> join : 배열 요소를 문자열로 합칩니다. 이때 요소 사이를 구분할 구분자를 지정할 수 있습니다.<br>
> pop : 배열의 마지막 요소를 꺼내 그 값을 반환합니다.<br>
> push : 배열의 맨 끝에 새로운 요소를 추가한 후 새로운 length를 반환합니다.<br>
> reverse : 배열의 배치 순서를 역순으로 바꿉니다.<br>
> shift : 배열에서 첫 번째 요소를 꺼내 그 값을 반환합니다.<br>
> slice : 배열에서 특정한 부분만 추출합니다. 기존 배열은 바뀌지 않습니다.<br>
> sort : 배열 요소를 지정한 조건에 따라 정렬합니다.<br>
> splice : 배열에 요소를 추가하거나 특정 부분을 추출합니다.<br>
> toString : 배열에서 지정한 부분을 문자열로 반환합니다. 이때 각 요소는 쉼표로 구분합니다.<br>
> unshift : 배열의 시작 부분에 새로운 요소를 추가합니다