# map

map 은 배열 안의 각 원소를 변환 할 때 사용 되며, 이 과정에서 새로운 배열이 만들어진다.

`map` 함수 구문은 아래와 같다.

`arr.filter(callback(element[, index[, array]])[, thisArg])`

callbackFunction, thisArg 두개의 매개변수가 있고
callbackFunction은 currentValue, index, array 3개의 매개변수를 갖는다.

1. currentValue : 배열 내 현재 값
2. index : 배열 내 현재 값의 인덱스
3. array : 현재 배열.

그리고 thisArg은 callbackFunction 내에서 this로 사용될 값이다

예를 들어서 다음과 같은 배열이 있다.
`const array = [1, 2, 3, 4, 5, 6, 7, 8];`

배열 안의 모든 숫자를 제곱해서 새로운 배열을 만드려고 할 때 map 함수를 사용하지 않는다면 다음과 같이 구현 할 수 있다.

**for문**

```
const array = [1, 2, 3, 4, 5, 6, 7, 8];

const squared = [];
for (let i = 0; i < array.length; i++) {
  squared.push(array[i] * array[i]);
}

console.log(squared);
```

</br>

**forEach**

```
const array = [1, 2, 3, 4, 5, 6, 7, 8];

const squared = [];

array.forEach(n => {
  squared.push(n * n);
});

console.log(squared);
```

</br>

만약 map 을 사용하면 이를 더 짧은 코드를 사용하여 구현 할 수 있다.

</br>

**map**

```
const array = [1, 2, 3, 4, 5, 6, 7, 8];

const square = n => n * n;
const squared = array.map(square);
console.log(squared);
```

결과는 다음과 같다.

`[1, 4, 9, 16, 25, 36, 49, 64];`

map 함수의 파라미터로는 변화를 주는 함수를 전달해준다.
현재 변화를 주는 함수 square 는 파라미터 n 을 받아와서 이를 제곱해 준다.
array.map 함수를 사용 할 때 square 를 변화를 주는 함수로 사용함으로서, 내부의 모든 값에 대하여 제곱을 해서 새로운 배열을 생성한다.
그런데 변화를 주는 함수를 꼭 이름을 붙여서 선언 할 필요는 없다.
코드를 다음과 같이 작성할 수 있다.

```
const squared = array.map(n => n * n);
console.log(squared);
```
