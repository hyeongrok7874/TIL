# 연산자

하나 이상의 표현식을 대상으로 산술, 할당, 비교, 논리, 타입, 지수 연산등을 수행하여 하나의 값을 만든다

## 피연산자

연산의 대상

## 산술 연산자

### 이항 산술 연산자

- 2개의 피연산자를 산술 연산하여 숫자 값을 만든다.
- 모든 이항 산술 연산자는 값을 변경하는 부수 효과가 없다.
- 피연산자의 값이 바뀌는 경우는 없고 언제나 새로운 값을 만든다.

#### 종류

- \+ 
- \- 
- \* 
- \/
- %

### 단항 산술 연산자

- 1개의 피연산자를 산술 연산하여 숫자값을 만든다.
- 증감연산자는 피연산자의 값을 변경하는 부수 효과가 있다.

#### 종류

- \++
- \--
- \+
- \-

#### 증감 연산자

- 전위 : 먼저 피연산자의 값을 증감 후, 다른 연산을 수행한다
- 후위 : 먼저 다른 연산을 수행한 후, 피연산자의 값을 증감한다.

### 문자열 연결 연산자

```js
'1' + 2; // '12'
1 + '2'; // '12'
```

#### 암묵적 타입 변환

```js
1 + true; // 2

1 + false; // 1

1 + null; // 1

+undefined; // NaN
1 + undefined;  // NaN
```

## 할당 연산자

우항에 있는 피연산자의 평가 결과를 좌항에 있는 변수에 할당한다.(부수 효과가 있다)<br>
표현식인 문 이다.

- =
- +=
- \-=
- *=
- /=
- %=

## 비교 연산자

좌항과 우항의 피연산자를 비교한 다음 그 결과를 불리언 값으로 반환한다.

### 동등/일치 비교 연산자

동등 비교 연산자는 느슨한 비교를 하지만 일치 비교 연산자는 엄격한 비교를 한다.

- == : 값이 같음
- === : 값과 타입이 같음 
- != : 값이 다름
- !== : 값과 타입이 다름

== 은 좌항과 우항의 피연산자를 비교할 때 먼저 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 확인한다.<br>

#### NaN

- NaN은 자신과 일치하지 않는 유일한 값이다.
- 숫자가 NaN인지 조사하려면 빌트인 함수 isNaN을 사용한다.

#### 0

- 양의 0과 음의 0이 따로 존재한다.

### 대소 관계 비교 연산자

피연산자의 크기를 비교하여 불리언 값을 반환한다.

- \> : 크다
- < : 작다
- => : 크거나 같다
- <= : 작거나 같다

### 삼항 조건 연산자

``` js
조건식 ? 조건식이 true일 때 반환할 값 : 조건식이 false일 때 반환할 값
```

삼항 조건 연산자의 표현식은 값으로 평가할 수 있는 표현식인 문이다.

## 논리 연산자

우항과 좌항의 피연산자(부정 논리 연산자의 경우 우항의 피연산자)를 논리 연산한다.

- ||
- &&
- !

## 쉼표 연산자

쉼표 연산자는 왼쪽 피연산자부터 차례대로 피연산자를 평가하고 마지막 피연산자의 평가가 끝나면 마지막 피연산자의 평가 결과를 반환한다.

## 그룹 연산자

- 소괄호 ()로 피연산자를 감싸는 그룹 연산자는 자신의 피연산자인 표현식을 가장 먼저 평가한다. 
- 그룹 연산자를 사용하면 연산자의 우선순위를 조절할 수 있다
- 연산자 우선순위가 가장 높다.

## typeof 연산자

typeof 연산자는 피연산자의 데이터 타입을 문자열로 반환한다.

### 반환 값

- string
- number
- boolean
- undefined
- symbol
- object
- function

### 주의점

- null 값 연산시 "null"이 아닌 "object"를 반환한다
- 선언되지 않은 식별자를 typeof 연산자로 연산해 보면 RefernenceError가 발생하지 않고 undefined를 반환한다.

## 지수 연산자

좌항의 피연산자를 밑으로, 우항의 피연산자를 지수로 거듭 제곱하여 숫자 값을 반환한다.

```js
2 ** 2; // 4
```

지수 연산자가 도입 되기전에는 Math.pow 메서드를 사용했다.

```js
Math.pow(2, 2); // 4
```

음수를 거듭제곱의 밑으로 사용해 계산하려면 괄호로 묶는다.

```js
(-5) ** 2; // 25
```

지수 연산자는 다른 산술 연산자와 마찬가지로 할당 연산자와 함께 사용할 수 있다

```js
let num = 5;
num **= 2; // 25
```

지수 연산자는 이항 연산자 중에서 우선순위가 가장 높다

## 그 외의 연산자

- ?. - 옵셔널 체이닝 연산자
- ?? - null 병합 연산자
- delete - 프로퍼티 삭제
- new - 생성자 함수를 호출할 때 사용하여 인스턴스를 생성
- instanceof - 좌변의 객체가 우변의 생성자 함수와 연결된 인스턴스인지 판별
- in - 프로퍼티 존재 확인

## 연산자의 부수 효과

부수 효과가 있는 연사자는 할당 연산자, 증감 연산자, delete 연산자이다.

## 연산자 우선 순위

1. ( )
2. new(매개변수 존재), . , [ ](프로퍼티 접근), ( )(함수 호출), ?.(옵셔널 체이닝 연산자)
3. new(매개변수 미존재)
4. x++, x--
5. !x, +x, -x, ++x, --x, typeof, delete
6. **
7. *, /, %
8. +, -
9. <, <=, >, >=, in, instanceof
10. ==, !=, ===, !==
11. ??(null 병합 연산자) 
12. &&
13. ||
14. ? ... : ...
15. 할당 연산자(=, +=, -=, ...)
16. ,


## 연산자 결합 순서

연산자 결합 순서란 연산자의 어느쪽(좌항 또는 우항)부터 평가를 수행할 것인지를 나타내는 순서를 말한다.

### 좌항 -> 우항

- \+
- \-
- /
- %
- <
- <=
- \>
- \>=
- &&
- ||
- .
- [ ]
- ( )
- ??
- ?.
- in
- instanceof

### 우항 -> 좌항

- ++
- \--
- 할당 연산자(=, +=, -=, ...)
- !ㅌ
- +x
- -x
- ++x
- --x
- typeof
- delete
- ? ... : ...