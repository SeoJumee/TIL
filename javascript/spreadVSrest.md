## spread

spread 라는 단어가 가지고 있는 의미는 펼치다, 퍼뜨리다 이다.
이 문법을 사용하면, 객체 혹은 배열을 펼칠 수 있다.

객체 예시

```js
const slime = {
  name: '슬라임',
};

const cuteSlime = {
  name: '슬라임',
  attribute: 'cute',
};

const purpleCuteSlime = {
  name: '슬라임',
  attribute: 'cute',
  color: 'purple',
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);
```

<img src="https://i.imgur.com/XeRXMXb.png">

기존에 선언한 slime 을 건들이지 않고 cuteSlime이라는 새로운 객체를 만들어서 slime 이 가지고 있는 값을 그대로 사용할 수 있다.

purpleCuteSlime 객체는 cuteSlime 이 가지고 있는 속성을 그대로 사용하면서 추가적으로 color 가 추가되었다.

위 코드에서의 핵심은, 기존의 것을 건들이지 않고, 새로운 객체를 만든다는 것 인데,
이러한 상황에 사용 할 수 있는 유용한 문법이 **spread** 이다.

```js
const slime = {
  name: '슬라임',
};

const cuteSlime = {
  ...slime,
  attribute: 'cute',
};

const purpleCuteSlime = {
  ...cuteSlime,
  color: 'purple',
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);
```

`... 문자`가 바로 spread 연산자이다.
spread 연산자는 배열에서도 사용 할 수 있다.

배열 예시

```js
const animals = ['개', '고양이', '참새'];
const anotherAnimals = [...animals, '비둘기'];
console.log(animals);
console.log(anotherAnimals);
```

<img src="https://i.imgur.com/Z8t1wEt.png">

기존의 animals 는 건드리지 않으면서, 새로운 anotherAnimals 배열에 animals 가 가지고 있는 내용을 모두 집어넣고, '비둘기' 라는 항목을 추가적으로 넣었다.

```js
const numbers = [1, 2, 3, 4, 5];

const spreadNumbers = [...numbers, 1000, ...numbers];
console.log(spreadNumbers); // [1, 2, 3, 4, 5, 1000, 1, 2, 3, 4, 5]
```

배열에서 spread 연산자를 여러번 사용 하는 것 또한 가능하다.

## rest

rest는 생김새는 spread 랑 비슷한데, 역할이 매우 다르다.
rest는 객체, 배열, 그리고 함수의 파라미터에서 사용이 가능하다.

객체 예시

```js
const purpleCuteSlime = {
  name: '슬라임',
  attribute: 'cute',
  color: 'purple',
};

const { color, ...rest } = purpleCuteSlime;
console.log(color);
console.log(rest);
```

<img src="https://i.imgur.com/XYg74q3.png">

rest 안에 name 값을 제외한 값이 들어있다.

rest 는 객체와 배열에서 사용 할 때는 이렇게 비구조화 할당 문법과 함께 사용된다.
주로 사용 할때는 위와 같이 rest 라는 키워드를 사용하게 된다.

배열 예시

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [one, ...rest] = numbers;

console.log(one);
console.log(rest);
```

<img src="https://i.imgur.com/tEpTlMQ.png">

배열 비구조화 할당을 통하여 원하는 값을 밖으로 꺼내고, 나머지 값을 rest 안에 넣었다.

오류 예시

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [..rest, last] = numbers;
```

rest 파라미터는 이름 그대로 먼저 선언된 파라미터에 할당된 인수를 제외한 나머지 인수들이 모두 배열에 담겨 할당된다.
따라서 Rest 파라미터는 반드시 **마지막 파라미터**이어야 한다.

함수 예시

위에서의 sum 함수는 7개의 파라미터를 받아오는데 6개만 넣어준다면 g 값이 undefined 가 된다.
sum 에 더하는 과정에서 += undefined 를 하게 되면 결과는 NaN 이 되버린다.
그렇기 때문에 함수에서 하나하나 유효한 값인지 확인을 해줘야 한다.
함수의 파라미터가 몇개가 될 지 모르는 상황에서 rest 파라미터를 사용하면 매우 유용하다.

```js
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // 21
```
