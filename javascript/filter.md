# filter

`filter` 함수는 배열에서 특정 조건을 만족하는 값들만 따로 추출하여 새로운 배열을 만든다.

filter 함수의 구문은 아래와 같다.

`const newArray = arr.filter(callbackFunction(element, index, array), thisArg);`

filter 함수의 매개변수는 `callbackFunction` 과 `thisArg` 이다.

callbackFunction에는 3개의 매개변수를 사용할 수 있다.

1. element : 요소값
2. index : 요소의 인덱스
3. array : 사용되는 배열 객체

그리고 thisArg 는 filter에서 사용될 this 값이며 선택적으로 사용되며 사용하지 않을 경우 undefined 전달 된다.

예제로 todos 배열에서 done 값이 false 인 항목들만 따로 추출해서 새로운 배열을 만들어보면

```JS
const todos = [
  {
    id: 1,
    text: '자바스크립트 입문',
    done: true
  },
  {
    id: 2,
    text: '함수 배우기',
    done: true
  },
  {
    id: 3,
    text: '객체와 배열 배우기',
    done: true
  },
  {
    id: 4,
    text: '배열 내장함수 배우기',
    done: false
  }
];

const tasksNotDone = todos.filter(todo => todo.done === false);
console.log(tasksNotDone);
```

결과는 다음과 같다.

```JS
[
  {
    id: 4,
    text: '배열 내장 함수 배우기',
    done: false
  }
];
```

filter 함수에 넣는 파라미터는 조건을 검사하는 함수를 넣어주며, 이 함수의 파라미터로 각 원소의 값을 받아오게 된다.

방금 우리가 작성한 코드는 이렇게 입력 할 수도 있다.
`const tasksNotDone = todos.filter(todo => !todo.done);`
filter 에 넣어준 함수에서 true 를 반환하면 새로운 배열에 따로 추출을 해주는데, 만약 todo.done 값이 false 라면, !false 가 되고 이 값은 true 이기 때문에, 이전의 todo.done === false 와 똑같이 작동하게 된다.
