# 배열 렌더링

그냥 그대로 코드로 작성 시 비효율적이다 

따라서 컴포넌트를 재사용할 수 있도록 만들어 효율적으로 한다

한 파일에 여러개의 컴포넌트를 선언해도 괜찮다

## 정적 배열

배열의 인덱스를 하나하나 조회해가면서 렌더링한다

```jsx
const User = ({user}) => {
  return(
    <div>
      <b>{user.username}</b> <span>({user.email})</span>
    </div>
  )
}

const UserList = () => {
  const users = [
    {
      id: 1,
      username: 'velopert',
      email: 'public.velopert@gmail.com'
    },
    {
      id: 2,
      username: 'tester',
      email: 'tester@example.com'
    },
    {
      id: 3,
      username: 'liz',
      email: 'liz@example.com'
    }
  ];

  return(
    <>
      <User user={users[0]} />
      <User user={users[1]} />
      <User user={users[2]} />
    </>
  )
}
```

동적 배열은 렌더링할 수 없다

## 동적 배열

```map()``` 함수를 사용한다

이 함수로 일반 데이터 배열을 리액트 엘리먼트로 이루어진 배열로 변환해준다

```jsx
const UserList = () => {
  const users = [
    {
      id: 1,
      username: 'velopert',
      email: 'public.velopert@gmail.com'
    },
    {
      id: 2,
      username: 'tester',
      email: 'tester@example.com'
    },
    {
      id: 3,
      username: 'liz',
      email: 'liz@example.com'
    }
  ];

  return (
    <>
      {users.map(user => (
        <User user={user} key={user.id} />
      ))}
    </>
  )
}
```

리액트에서 배열을 렌더링 할 때에는 ```key``` 라는 props를 설정해야한다

```key``` 값은 각 원소들마다 가지고 있는 고유 값으로 설정 해야한다 (지금의 경우 id)

만약 배열 안의 원소가 가지고 있는 고유한 값이 없다면 ```map()```의 콜백함수의 두번째 파라미터 index를 key로 사용한다

```jsx
<>
  {users.map((user, index) => (
    <User user={user} key={index}>
  ))}
</>
```

## key 존재유무에 따른 업데이트 방식

key가 존재하지 않을 시에 변경사항이 있을 시 기존의 값을 수정하는 식으로 비효율적으로 렌더링이 되지만

key가 존재할 시 수정되지 않는 기존의 값은 그대로 두고 원하는 곳에 내용을 삽입하거나 삭제한다

## 주의할 점

배열을 업데이트 할 때에는 불변성을 지켜주기 위하여 기존의 배열을 복사하고 사용한다