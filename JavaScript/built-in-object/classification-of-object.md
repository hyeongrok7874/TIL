# 자바스크립트 객체의 분류

## 표준 빌트인 객체

ECMAScript 사양에 정의된 객체

ECMAScript 사양에 정의된 객체이므로 js 실행 환경과 관계없이 언제나 사용할 수 있다.

표준 빌트인 객체는 전역 객체의 프로퍼티로서 제공되므로 별도의 선언 없이 전역 변수처럼 언제나 참조할 수 있다.

## 호스트 객체

ECMAScript 사양에 정의되어 있지 않지만 js 실행 환경 (브라우저 환경 또는 Node.js 환경)에서 추가로 제공하는 객체

### 브라우저 환경

- DOM, BOM, Canvas, XMLHttpRequest, fetch, requestAnimationFrame, SVG, Web Storage, Web Component, Web Worker 와 같은 클라이언트 사이드 Web API를 호스트 객체로 제공한다.

### Node.js 환경

- Node.js 고유의 API를 호스트 객체로 제공한다.

## 사용자 정의 객체

사용자가 직접 정의한 객체
