# 객체

## 객체란?
> 객체는 관련된 데이터와 함수의 집합

## 종류
> 내장 객체 : 미리 정의되어 있는 객체 <br>
> ex) Number, Boolean, Array, Math<br>
> 문서 객체 모델(DOM) : 객체를 사용해 웹 문서를 관리하는 방식 <br>
> ex) Document 객체, Image 객체<br>
> 브라우저 객체 모델 : 웹 브라우저의 주소 표시줄이나 창 크기 등 웹 브라우저 정보를 다루는 객체<br>
> ex) Navigator 객체, History 객체, Location 객체, Screen 객체<br>
> 사용자 정의 객체 : 사용자가 정의한 객체

## 속성
> 객체에서 값을 담고 있는 정보

## 메서드
> 객체가 어떻게 동작할지를 선언해 놓은 함수

## 프로토타입
> 다른 객체의 원형이 되는 객체

## 인스턴스
> 프로토타입을 사용하여 만든 객체
```js
let now = new Date()
```

## 사용자 정의 객체 만들기
> 리터럴 표기법
```js
let book = {
    title: "자바스크립트",
    author: "형록",
    pages: 300,
    price: 12000,
    //함수
    info: function(){
        alert(this.tile + "책의 분량은 " + this.pages + "쪽입니다.");
    }
};
```

## 생성자 함수로 객체 만들기
```js
function Book(author, pages, price, title){
    this.author = author;
    this.pages = pages;
    this.price = price;
    this.title = title;
}

let jsBook = new Book("김형록", 500, 15000, "자바스크립트");
```