## closure

**내부 함수가 정의될 때 외부 함수의 환경을 기억하고 있는 내부 함수를 말한다.**
쉽게 말해 함수 안에 함수내에서 함수를 선언하고 사용하는 것인데
외부 함수 안에서 선언된 내부 함수는 그 외부 함수의 `지역 변수`나 `함수`에 접근하여 사용할 수 있다.

**클로저 함수의 기본 형태**

```js
// 외부 함수
function closuer() {
  // 변수 정의
  var count = 0;
  // 내부 함수(클로저) 선언
  function inner() {
    return ++count;
  }
  // 내부 함수 반환
  return inner();
}

// 익명 함수를 이용한 방법
function closure() {
  var count = 0;
  // 익명 함수(클로저) 반환
  return function () {
    return ++count;
  };
}
```

**클로저 함수 사용 예시**

```js
function outter() {
  // 외부 함수
  var data = 1;

  function inner() {
    // 내부 함수
    return data;
  }

  return inner();
}
```

outter 안에는 지역변수 data와 inner라는 내부 함수가 선언되어 있고 inner 함수를 반환하고 있다.
inner 함수는 외부에 있는 data 변수를 사용하고 있다.

**클로저 함수 호출**

```js
var func = outter();
console.log(func); // 1
```

outter 함수의 지역변수였던 data의 값 1이 출력된다.
원래는 outter 함수를 호출하지 않았기 때문에 지역변수 data는 사용하지 못하는 것이 일반적이지만 자바스크립트에서는 사용할 수 있다.

**클로저 특징**

1. 클로저는 단독으로 호출돼도 외부 함수의 정보와 연결되어 있기 떄문에 **값들이 동적으로 바뀌어도 반영된다**.
2. **전역 변수의 남용**을 막을 수 있다.
3. **변수의 값을 은닉**할 수 있다.
