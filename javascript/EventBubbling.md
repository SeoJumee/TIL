## 이벤트 버블링

이벤트 버블링이란 한 요소에 이벤트가 발생하면 이 요소에 할당된 핸들러가 동작하고, 이어서 부모 요소의 핸들러가 동작하고 최상단의 부모 요소를 만날 때까지 반복되면서 핸들러가 동작하는 현상을 말한다.

```js
<body>
  <div class="DIV1">
    DIV1
    <div class="DIV2">
      DIV2
      <div class="DIV3">DIV3</div>
    </div>
  </div>
</body>
```

```js
const divs = document.querySelectorAll('div');

const clickEvent = (e) => {
  console.log(e.currentTarget.className);
};

divs.forEach((div) => {
  div.addEventListener('click', clickEvent);
});
```

div를 클릭하면 해당하는 클래스의 이름이 콘솔로 출력되는 코드이다.
자바스크립트는 기본적으로 버블링이 발생하기 때문에 `<div class="DIV3">DIV3</div>`를 클릭한다면 콘솔에는 DIV3, DIV2, DIV1이 순서대로 출력이 될 것이다.
클릭하면 할당되어 있는 이벤트가 발생하고 다음에는 바깥의 div 태그에 할당된 이벤트가 발생하고 document 객체를 만날 때까지 이벤트가 전파된다.

## 이벤트 전파막기

캡처링은 버블링과는 반대로 최상위 태그에서 해당 태그를 찾아 내려간다.

**event.stopPropagation()** 을 사용하면 되는데 버블링의 경우에는 클릭한 타깃의 이벤트만 발생하고 상위 요소로 이벤트가 전파되는 것을 막을 수 있다.

버블링에서 작성된 코드에 event.stopPropagation() 을 추가하고 실행해보자.

```js
const clickEvent = (e) => {
  e.stopPropagation();
  console.log(e.currentTarget.className);
};
```

아까는 DIV3을 클릭했을 때 이벤트가 전파되어 DIV3, DIV2, DIV1 이 출력이 됐지만 이번에는 클릭한 타깃의 이벤트만 발생하는 것을 알 수 있다.
