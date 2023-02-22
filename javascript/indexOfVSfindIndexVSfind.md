## indexOf

**`indexOf` 는 원하는 항목이 몇번째 원소인지 찾아주는 함수이다.**

`indexOf` 함수는, 문자열(string)이나 배열에서 특정 문자열(searchvalue)을 찾고,
검색된 문자열이 '첫번째'로 나타나는 위치 index를 리턴한다.

`string.indexOf(searchvalue, position)`

**파라미터**

1. searchvalue : 필수 입력값, 찾을 문자열
2. position : optional, 기본값은 0, string에서 searchvalue를 찾기 시작할 위치

- 찾는 문자열이 없으면 -1을 리턴한다.
- 문자열을 찾을 때 대소문자를 구분한다.

예를 들어서 다음과 같은 배열이 있을 때

`const superheroes = ['아이언맨', '캡틴 아메리카', '토르', '닥터 스트레인지'];`

토르가 몇번째 항목인지 알고싶다면 이렇게 입력 할 수 있다.

```
const superheroes = ['아이언맨', '캡틴 아메리카', '토르', '닥터 스트레인지'];
const index = superheroes.indexOf('토르');
console.log(index);
```

index 값은 0 부터 시작하기 때문에 0: 아이언맨 1: 캡틴 아메리카 2: 토르
이렇게 돼서 2라는 값이 나타난다.

</br>

## findIndex

**`findIndex`는 판별 함수를 만족하는 첫 식별자 반환한다.**

`arr.findIndex(callback)`

- 반환 타입 number, 없다면 -1 한다.
- callback(element, index, array) → 콜백함수가 받는 인자(각 인자는 findIndex 메서드를 호출한 배열에서 받아옴)
- 원하는 요소의 식별자 찾기
- 원하는 요소를 찾자마자 메서드를 종료함

</br>

만약에 배열 안에 있는 값이 숫자, 문자열, 또는 불리언이라면 찾고자하는 항목이 몇번째 원소인지 알아내려면 indexOf 를 사용하면 된다.
하지만, 배열 안에 있는 값이 객체이거나, 배열이라면 indexOf 로 찾을 수 없다.

예를 들어서 다음과 같은 배열이 있다고 가정해보자.

```
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
```

여기서 만약 id 가 3 인 객체가 몇번째인지 찾으러면, findIndex 함수에 검사하고자 하는 조건을 반환하는 함수를 넣어서 찾을 수 있다.

```
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

const index = todos.findIndex(todo => todo.id === 3);
console.log(index);
```

결과는 2가 나타난다.

</br>

## find

**`find` 함수는 판별 함수를 만족하는 첫 요소를 반환한다.**

find 함수는 findIndex 랑 비슷한데, 찾아낸 값이 몇번째인지 알아내는 것이 아니라, 찾아낸 값 자체를 반환한다.

`arr.find(callback)`

- 반환 타입은 찾은 요소의 타입, 없다면 undefinded
- callback(element, index, array) → 콜백 함수가 받는 인자(각 인자는 find 메서드를 호출한 배열에서 받아옴)
- 원하는 요소 찾기
- 원하는 요소를 찾자마자 메서드를 종료함

```
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

const todo = todos.find(todo => todo.id === 3);
console.log(todo);
```

결과는 다음과 같다.

```
{id: 3, text: "객체와 배열 배우기", done: true}
```
