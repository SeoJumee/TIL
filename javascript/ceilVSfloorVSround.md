## ceil, floor, round

Math는 다음 함수들을 제공하고 있다.

- Math.ceil() : 소수점 이하 숫자를 **올림** 하여 정수를 리턴한다.
- Math.floor() : 소수점 이하 숫자를 **버림**하여 정수를 리턴한다.
- Math.round() : 소수점 이하 숫자를 **반올림**하여 정수를 리턴한다.

1. **Math.ceil()** 예제
   Math.ceil()으로 소수점 이하의 숫자를 올림하는 예제이다.

```
const num1 = 1.1234;
const num2 = 12.5678;
const num3 = 123.5678;

console.log(Math.ceil(num1));   // 2
console.log(Math.ceil(num2));   // 13
console.log(Math.ceil(num3));   // 124
```

</br>

2. **Math.floor()** 예제
   Math.floor()으로 소수점 이하의 숫자를 버림하는 예제이다.

```
const num1 = 1.1234;
const num2 = 12.5678;
const num3 = 123.5678;

console.log(Math.floor(num1));   // 1
console.log(Math.floor(num2));   // 12
console.log(Math.floor(num3));   // 123
```

</br>

3. **Math.round()** 예제
   Math.round()으로 소수점 이하의 숫자를 반올림하는 예제이다.

```
const num1 = 1.1234;
const num2 = 12.5678;
const num3 = 123.5678;

console.log(Math.round(num1)); // 1
console.log(Math.round(num2)); // 13
console.log(Math.round(num3)); // 124
```
