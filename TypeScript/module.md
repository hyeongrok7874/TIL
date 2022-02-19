# 모듈

TS에서는 index.ts와 같은 소스 파일을 모듈이라고 한다

## export 키워드

모듈을 내보낼 때 사용한다

interface, class, type, let, const, function 앞에 붙일 수 있다

```ts
export interface Person {
  name: string
  age: number
}
```

### export default 키워드

한 모듈이 내보내는 기능 중 오직 한 개에만 붙일 수 있다

export 등이 있는 파일에서도 사용할 수 있다

import 시에 중괄호 없이 사용할 수 있다

```ts
export default interface Person {
  name: string
  age: number
}
```

```ts
import 

## import 키워드

export로 내보내진 심벌을 불러오기 위한 키워드

```ts 
import { 심벌 목록 } from '파일의 상대 경로'
```

### import * as 구문

```ts
import * as 심벌 from '파일 상대 경로'

심벌.불러온함수();
```

심벌로 접근할 수 있다

### 외부 패키지를 사용할 때 import 문

하나만 export default 형태로 제공하는 경우

```ts
import 심벌 from './가 생략된 외부 패키지'
```

여러개를 import 하는 경우 

```ts
import { 심벌 목록 } from './가 생략된 외부 패키지'
```

\* as로 import

```ts
import * as 심벌 from './가 생략된 외부 패키지'
```