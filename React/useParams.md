## useParams

`useParams`는 리액트 라우터 라이브러리에서 제공하는 Hook으로, Route path 와 일치하는 현재 URL에서 동적 매개변수의 키/값 쌍의 개체를 반환한다.

쇼핑몰 웹사이트를 예를들면 메인 페이지에서 여러개의 값을 렌더링하고, 클릭한것만 렌더링 시키고자 할때 하나하나 다 onclick 이벤트를 사용하기가 번거로운데, useParams 로 해결 가능하다.

사용법은 다음과 같다.

`import { useParams } from 'react-router-dom';`

</br>

**예제**

```JS
import { useParams } from 'react-router-dom';

function App() {

  return (
  <div className="App">
      <Routes>
        <Route path="/detail/:id" element={<Detail/>}/>
      </Routes>
  </div>
  );

function Product() {

  const productList =[
  {id : 0, name : Jorden1 Chicago, color: red},
  {id : 1, name : Jordan1 Oreo, color: black},
  {id : 2, name : Jorden1 Smokegrey, color: grey },
  ]

  const {id} = useParams();
  return (
  	<div className="product-list">
    	<h3> productList[id].name </h3>
      	<p> productList[id].color </p>
    </div>
  );
```

신발 상품 리스트 코드를 예를들어, 여러 상품중 클릭한 것만 렌더링 시킬때 사용한다.
Url : main/0 로 접속한경우 id가 0 이므로 jorden1 Chicago , red 인 상품을 렌더링 시킨다.
