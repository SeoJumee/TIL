## useMemo

`useMemo`는 리액트에서 컴포넌트의 성능을 최적화 하는데 사용되는 훅이다.

useMemo에서 memo는 memoization을 뜻하는데 이것은 ‘메모리에 넣기’라는 의미이며 컴퓨터 프로그램이 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장해 재사용함으로 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게 하는 기술이다.

리액트에서 함수형 컴포넌트는 렌더링 => 컴포넌트 함수 호출 => 모든 내부 변수 초기화의 순서를 거친다.

<br />

```
function Component() {
    const value = calculate();
    return <div>{value}</div>
}

function calculate() {
    return 10;
}
```

컴포넌트가 렌더링 될 때마다 value라는 **변수가 초기화**된다.
즉, 렌더링 될 때마다 calculate 함수가 불필요하게 재호출된다는 것인데 만약 calculate가 무겁고 복잡한 함수라면 매우 비효율적일 것이다.

때문에 우리는 useMemo 훅을 사용하는 것인데 useMemo를 사용하면 렌더링 => 컴포넌트 함수 호출 => memoize된 함수 재사용하는 순서를 거친다.

이렇게 되면 calculate 함수를 반복적으로 실행할 필요가 없게 된다.
useMemo는 위에 말했듯이 처음에 계산된 값을 메모리에 저장해 컴포넌트가 계속 렌더링되어도 calculate를 다시 호출하지 않고 메모리에 저장되어있는 계산된 값을 가져와 재사용할 수 있게 해준다.

<br />

#### useMemo 구조

```
const value = useMemo(() => {
return calculate();
},[item])
```

useMemo는 useEffect처럼 첫 번째 인자로 `콜백 함수`, 두 번째 인자로 `의존성 배열(dependancyArray)`을 받는다.

**의존성 배열 안에있는 값이 업데이트 될 때에만 콜백 함수를 다시 호출하여 메모리에 저장된 값을 업데이트 해준다.**

만약 빈 배열을 넣는다면 useEffect와 마찬가지로 마운트 될 때에만 값을 계산하고 그 이후론 계속 memoization된 값을 꺼내와 사용한다.
