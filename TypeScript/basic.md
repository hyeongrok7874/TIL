# 주요문법

## ESNext 주요문법

### 비구조화 할당

```ts
let person = {name: "Jane", age: 22};
let {name, age} = person; //name = "Jane", age = 22
```

### 화살표 함수

```ts
function add(a, b) {return a + b}
const add2 = (a,b) => a + b;
```

위와 아래의 코드는 같은 역할을 하는데 화살표 함수로 코드를 간결하게 만들 수 있다.

### 클래스

```ts
abstract class Animal {
  constructor(public name?: string, public age?: number){}
  abstract say(): string
}

class Cat extends Animal{
  say() {return '야옹'}
}

class Dog extends Animal{
  say() {return '멍멍'}
}

let animals: Animal[] = [new Cat('야옹이', 2), new Dog('멍멍이', 3)]
let sounds = animals.map(a => a.say()) // ["야옹", "멍멍"]
```

객체지향 프로그래밍을 지원한다

### 모듈

```ts
import * as fs from 'fs'

export function writeFile(filepath: string, content:any){
  fs.writeFile(filepath, content, (err)) => {
    err && console.log('error', err)
  }
}
```

모듈을 사용하면 코드를 여러 개 파일로 분할해서 작성할 수 있습니다. 

변수나 함수, 클래스 등에 export 키워드를 사용해 모듈로 만들면 다른 파일에서도 사용할 수 있습니다.

파일을 분할해서 구현할 수 있게 해주는 모듈 기능을 제공한다.

### 생성기

**yield**라는 특별한 키워드를 제공한다

**yield**문은 '반복자'를 의미하는 반복기를 생성할 때 사용한다.

반복기는 독립적으로 존재하지 않고 반복기 제공자를 통해 얻는다.

**yield**문을 이용해 반복기를 만들어 내는 반복기 제공자를 생성기라 한다

생성기는 function*과 yield 키워드를 이용해 만든다.

yield는 반드시 function* 안에서 사용이 가능하다

```ts
function* gen(){
  yield* [1, 2]
}
for(let value of gen()) {console.log(value)} // 1, 2
```

위 코드에서 1행의 function을 생성기라고 한다

yield가 호출되면 2행에서 점프하여 4행을 실행한다. 

그리고 4행의 실행을 마치면 2행을 실행하고, 이 과정을 2행의 배열 [1, 2]의 요소를 모두 순회할 때까지 반복한다.

### Promise와 async/await 구문

Promise는 웹 브라우저와 노드제이에스(Node.js)에서 모두 제공하는 기본 타입으로 비동기 콜백 함수를 상대적으로 쉽게 구현할 목적으로 만들어졌다.

```ts
async function get(){
  let value = []
  values.push(await Promise.resolve(1))
  values.push(await Promise.resolve(2))
  values.push(await Promise.resolve(3))
  return values
}
get().then(values => console.log(values)) // [1, 2, 3]
```

1행의 함수는 async 함수 수정자를 사용한다. 

async를 사용한 함수는 본문에서 await 키워드를 사용할 수 있다.

await는 Promise 객체를 해소해 준다. 

따라서 아래 get함수는 [1, 2, 3] 값을 Promise 형태로 반환한다.

get이 반환한 Promise 객체는 then 메서드를 호출해 실제 값을 얻을 수 있다.

## TS 고유 문법

### 타입 주석과 타입 추론

```ts
let n: number = 1 // 타입 주석
let m = 2 // 타입 추론
```

1행의 변수 n 뒤에 :(콜론)과 타입 이름이 있다

이것을 타입 주석이라 한다

타입스크립트는 2행처럼 타입 부분을 생략할 수도 있다

타입 부분이 생략되면 대입 연산자의 오른쪽 값을 분석해 왼쪽 변수의 타입을 결정한다

이것을 타입 추론이라 한다

타입 추론 기능은 자바스크립트 소스코드와 호환성을 보장하는 데 큰 역할을 한다

타입 추론 덕분에 .js 파일을 확장자만 .ts로 바꾸면 타입그크립트 환경에서도 바로 동작한다

### 인터페이스

```ts
interface Person{
  name: string
  age?: number
}

let person: Person = {name: "Jane
}
```

### 튜플

튜플은 물리적으로는 배열과 같다

하지만, 배열에 저장되는 아이템의 데이터 타입이 모두 같으면 배열, 다르면 튜플이다

```ts
let numberArray: number[] = [1, 2, 3] // 배열
let tuple: [boolean, number, string] = {true, 1, 'ok'} // 튜플
```

### 제네릭 타입

다양한 타입을 한꺼번에 취급할 수 있게 해준다

```ts
class Container<T>{
  constructor(public value: T){}
}

let numberContainer: Container<number> = new Container<number>(1)
let stringContainer: Container<string> = new Container<string>('Hello world')
```

위 코드에서 Container 클래스는 value 속성을 포함한다

이 클래스는 여러가지 타입을 대상으로 동작할 수 있다

### 대수 타입

다른 자료형 값을 가지는 자료형을 의미한다

합집합 타입(|)과 교집합 타입(&) 두 가지가 있다

```ts
type NumberOrString = number |string
type AnimalAndPerson = Animal &Person
