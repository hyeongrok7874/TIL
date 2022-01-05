# custom Hooks

커스텀 Hook으로 반복되는 로직을 쉽게 재사용 할 수 있다

## 만드는 법

```src/Hooks``` 아래에 ```use....```의 파일에 함수를 작성한다

ex) useSetInterval

```tsx
import React, { useEffect, useLayoutEffect, useRef } from "react";

const useSetInterval = (callback: () => void, delay: number | null) => {
  const savedCallback = useRef(callback);

  useLayoutEffect(() => {
    savedCallback.current = callback;
  }, [callback]);

  useEffect(() => {
    if (!delay && delay !== 0) {
      return;
    }

    const id = setInterval(() => savedCallback.current(), delay);

    return () => clearInterval(id);
  }, [delay]);
};

export default useSetInterval;
```