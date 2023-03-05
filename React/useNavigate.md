## useNavigate

`useNavigate`는 특정 행동을 했을 때 해당 주소로 이동해줄 수 있게 만들어준다.

useNavigate는 양식이 제출되거나 특정 event가 발생할 때, url을 조작할 수 있는 interface를 제공한다.

</br>

```JS
import { useNavigate } from 'react-router-dom';

function Func() {
  const navigate = useNavigate();

  const onClickImg = () => {
    navigate(`/comment/id/등등 내가 원하는 주소`);
  };

  return (
  	<img src={...} alt={...} onClick={onClickImg} />
  );
}

export default Func;
```

이렇게 작성하며 이 코드에서의 url이 www.naver.com 이었다면 이는 www.naver.com/comment/id... 으로 바뀐다.

**useNavigate 특징**

**1. 페이지 이동시 파라미터 전달 방법**
`navigate("../success",  { replace: true});`
첫 번째 인자로는 주소를 받으며 두 번째 인자로 { replace, state } 인수를 사용한다.

- replace (true or false)
  true를 사용한다면, navigate에 적힌 주소로 넘어간 후 뒤로가기를 하더라도 방금의 페이지로 돌아오지 않습니다. 이 때는 자신의 메인 페이지 ("/")로 돌아오게 된다. false는 뒤로가기가 가능하며 이 것이 기본 값이다.

- state (any)
  두번째 인자의 state 속성에 파라미터를 넣어준다.

  <br />

아래 예제코드는, 버튼을 클릭하면 '/test' 경로로 이동하면서 id, job을 인자로 넘긴다.

```JS
import { useNavigate } from 'react-router-dom';

export default function Test() {
  const navigate = useNavigate();

  // 버튼 클릭시 호출
  const move = () => {
    // 두번재 인자의 state 속성에 원하는 파라미터를 넣어준다. (id, job을 넣어봤다)
    navigate('/test2', {
      state: {
        id: 1,
        job: '개발자'
      }
    });
  };
  return (
    <div>
      <button onClick={move}>이동</button>
    </div>
  );
}
```

**2. 이동한 페이지에서, 파라미터 취득 방법**

1. useLocation() 훅으로 location을 취득한다.
2. locaiton.state 로 전달 받은 파라미터를 취득할 수 있다.

- location.state.키

<br />

아래 예제코드는 전달 받은 id와 job을 취득하여 화면에 표시한다.

```JS
import { useLocation } from 'react-router-dom';

export default function Test2() {
  // 1. useLocation 훅 취득
  const location = useLocation();

  // 2. location.state 에서 파라미터 취득
  const id = location.state.id;
  const job = location.state.job;

  return (
    <div>
      <p>id: {id}</p>
      <p>job: {job}</p>
    </div>
  );
}
```

<br />

**타입스크립트**의 경우, state의 타입이 unknown이므로 아래와 같이 타입을 지정해주면 된다.

```JS
import { useLocation } from 'react-router-dom';

export default function Test2() {
  // 1. useLocation 훅 취득
  const location = useLocation();

  // 2. location.state 에서 파라미터 취득 - 타입을 지정해줌.
  const state = location.state as { id: string; job: string };
  const id = state.id;
  const job = state.job;
  return (
    <div>
      <p>id: {id}</p>
      <p>job: {job}</p>
    </div>
  );
}
```

**3. useHistory의 기능**
useNavigate는 react v6 에서 useHistory 가 변화한 것이다.
이 때 useHistory 에서 사용하던, window의 history 를 이용한 navigate 기능도 할 수 있게 되었다.

```JS
<>
  <button onClick={() => navigate(-2)}>
    Go 2 pages back
  </button>
  <button onClick={() => navigate(-1)}>
    Go back
  </button>
  <button onClick={() => navigate(1)}>
    Go forward
  </button>
  <button onClick={() => navigate(2)}>
    Go 2 pages forward
  </button>
</>
```

History란 세션 기록(페이지 방문 기록)에 대한 접근 방법과 메서드를 제공하는 것이다.
또한 세션(session)이란 웹 사이트의 여러 페이지에 걸쳐 사용되는 사용자 정보를 저장하는 방법을 의미한다.
