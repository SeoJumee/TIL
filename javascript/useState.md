## useState

Functional Components를 사용한다면 React Hook 기능을 사용할 수 있는데 useState는 Hook이 제공하는 기능중 하나이다.

useState는 기본적으로 getter와 setter이다. getter는 변수의 값을 가져오는데 사용하고, setter는 변수의 값을 변경하는데 사용한다.

아래와 같이 State의 생성과 동시에 가져야할 초기값을 useState함수에 인자로 넣어주면 state(getter)와 setState(setter)라는 두 가지 요소를 배열 형태로 리턴해준다. (setter는 setter임을 명시하기 위해 getter의 변수 이름 앞에 set을 붙여서 사용한다.)

`const [state, setState] = useState(초기값);`

state의 값을 변경하고 싶으면 아래와 같이 setState에 인자로 변경될 값을 전달하면된다.

`setState(변경값);`

**useState를 사용하는 이유**

React가 웹상에 렌더링 되기 위해서는 render() 메서드가 실행되어야 한다.
React의 컴포넌트는 초기 생성 후 Mount 상태에서 한번 render() 메서드를 실행한 후,
Update 상태에 진입해 shouldComponentUpdate의 값이 true일 경우에만 render() 메서드를 실행한다.

useState 함수를 사용하지 않고 state의 값을 직접 변경할 경우 리렌더링이 발생하지 않는다.
리액트는 값이 변경되었는지 확인하기 위해 객체의 메모리 주소를 비교해서 판단하므로 직접 state 값을 수정할 경우 변경이 없다 판단하여 Update 상태로 진입하지 않는다.

위와 같은 이유로 state 값을 직접 변경하지 않고 setState를 통해 할당하는 것으로 변경해야 한다.
