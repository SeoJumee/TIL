## scope

Scope는 직역하면 "범위"라는 뜻이다.
JavaScript 에서 Scope(스코프)는 `변수에 접근할 수 있는 범위`를 말한다.
`식별자(변수)를 찾기위한 규칙`이라고도 한다.

```js
var x = 'global';

function foo() {
  var x = 'function scope';
  console.log(x);
}

foo(); // ?
console.log(x); // ?
```

위 예제에서 x가 두번 선언되었는데, JavaScript는 각 x가 어떤 값을 가지는지 어떻게 구별할 수 있을까?
위 예제에서 전역에 선언된 변수 x는 어디에든 참조할 수 있다. 하지만 함수 foo 내에서 선어도니 변수 x는 함수 foo 내부에서만 참조할 수 있고, 외부에서는 참조할 수 없다.
이러한 규칙을 **스코프** 라고 한다.

**JavaScript Scope의 종류**

- 블록 레벨 스코프
- 함수 레벨 스코프

대부분의 C 기반 언어들은 **블록 레벨 스코프**를 따른다.
하지만 자바스크립트는 **함수 레벨 스코프**를 따른다.

**블록 레벨 스코프**
`코드 블록 ({})` 내에서만 참조(접근)가능한 범위를 말한다.

```js
int main(void) {
  // block-level scope
  if (1) {
    int x = 5;
    printf("x = %d\n", x);
  }

  printf("x = %d\n", x); // use of undeclared identifier 'x'

  return 0;
}
```

위 C 언어 코드를 보면 if 문 내에서 선언된 변수 x 는 if 문 코드 블록 내에서만 유효하다.
즉, if 문 코드 블록 밖에서는 참조가 불가능하다.

**함수 레벨 스코프**
`함수 코드 블록` 내에서만 참조(접근) 가능한 범위를 말한다.

```js
var x = 0;
{
  var x = 1;
  console.log(x); // 1
}
console.log(x); // 1

let y = 0;
{
  let y = 1;
  console.log(y); // 1
}
console.log(y); // 0
```
