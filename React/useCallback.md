## useCallback

`useCallback()`은 함수를 **메모이제이션**(memoization)하기 위해서 사용되는 hook 함수입니다.

`useMemo` 는 **특정 결과값을 재사용** 할 때 사용하는 반면, `useCallback` 은 **특정 함수를 새로 만들지 않고 재사용**하고 싶을때 사용합니다.

첫번째 인자로 넘어온 **함수**를, 두번째 인자로 넘어온 **배열 내의 값**이 변경될 때까지 저장해놓고 재사용할 수 있게 해줍니다.

```
const memoizedCallback = useCallback(함수, 배열);
```

<br />

함수들은 컴포넌트가 리렌더링 될 때 마다 새로 만들어진다.
함수를 선언하는 것 자체는 사실 메모리도, CPU도 리소스를 많이 차지 하는 작업은 아니기에
함수를 새로 선언한다고 해서 그 자체만으로 큰 부하가 생길일은 없지만

나중에 컴포넌트에서 props 가 바뀌지 않았으면 Virtual DOM 에 새로 렌더링하는 것 조차 하지 않고
컴포넌트의 결과물을 재사용 하는 최적화 작업을 하기 위해 **함수를 재사용**하는것이 필수이다.

```
const onToggle = useCallback(
    id => {
      setUsers(
        users.map(user =>
          user.id === id ? { ...user, active: !user.active } : user
        )
      );
    },
    [users]
  );
```

이런 코드에서 users 배열의 값이 변경되지 않는다면 useCallback()의 첫번째 인자인 함수를 저장해놓고 재사용하게 된다.

주의 할 점은, 함수 안에서 사용하는 상태 혹은 props 가 있다면 꼭, deps 배열안에 포함시켜야 된다는 것이다.
만약에 deps 배열 안에 함수에서 사용하는 값을 넣지 않게 된다면,
함수 내에서 해당 값들을 참조할때 가장 최신 값을 참조 할 것이라고 보장 할 수 없다.
props 로 받아온 함수가 있다면, 이 또한 deps 에 넣어주어야 한다.

사실, useCallback 은 useMemo 를 기반으로 만들어졌다.
다만, 함수를 위해서 사용 할 때 더욱 편하게 해준 것 뿐이고 이런식으로도 표현 할 수 있다.

```
const onToggle = useMemo(
  () => () => {
    /* ... */
  },
  [users]
);
```
