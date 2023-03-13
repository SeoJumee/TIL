## var, let, const의 차이

1. 변수 선언 방식

`var`는 변수 선언 방식에 있어서 큰 단점을 가지고 있다.

**var**

````js
 var name = 'bathingape'
    console.log(name) // bathingape

    var name = 'javascript'
    console.log(name) // javascript
    ```
````

변수를 한 번 더 선언했음에도 불구하고, 에러가 나오지 않고 각자 다른 값이 출력되는 것을 볼 수 있다.

var는 유연한 변수 선언으로 간단한 테스트에는 편리 할 수 있지만, 코드량이 많아 진다면 어디에서 어떻게 사용 될지도 파악하기 힘들고 나중에 값이 바뀔 수 있다.

그래서 ES6 이후, 이를 보완하기 위해 추가 된 변수 선언 방식이 `let` 과 `const` 이다.

**let**

```js
let name = 'bathingape';
console.log(name); // bathingape

let name = 'javascript';
console.log(name);
// Uncaught SyntaxError: Identifier 'name' has already been declared
```

let과 const의 경우 name이 이미 선언 되었다는 에러 메세지가 나온다.
그 둘은 var와 다르게 변수 재선언이 되지 않는다.
그렇다면 **let 과 const 의 차이점**은 무엇일까?

이 둘의 차이점은 `immutable` 여부이다.
let 은 변수에 **재할당이 가능**하다. 그렇지만,

```js
let name = 'bathingape';
console.log(name); // bathingape

let name = 'javascript';
console.log(name);
// Uncaught SyntaxError: Identifier 'name' has already been declared

name = 'react';
console.log(name); //react
```

const는 **변수 재선언, 변수 재할당 모두 불가능**하다.

**const**

```js
const name = 'bathingape';
console.log(name); // bathingape

const name = 'javascript';
console.log(name);
// Uncaught SyntaxError: Identifier 'name' has already been declared

name = 'react';
console.log(name);
//Uncaught TypeError: Assignment to constant variable.
```
