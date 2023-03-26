## 구조 분해 할당

구조 분해 할당 구문은 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식이다.

함수에 객채나 배열을 전달해야 하는 경우가 생기거나 객체나 배열에 저장된 데이터 전체가 아닌 일부만 필요한 경우가 생긴다.

이럴 때 객체나 배열을 변수로 **분해**할 수 있게 하는 특별한 문법인 구조 분해 할당(destructuring assignment) 을 사용할 수 있다.

### 배열 분해

```js
let [firstName, surname] = [];

alert(firstName); // undefined
alert(surname); // undefined
```

할당하고자 하는 변수의 개수가 분해하고자 하는 배열의 길이보다 크더라도 에러가 발생하지 않는다.
할당할 값이 없으면 undefined로 취급되기 때문이다.

`=을 이용하면 할당할 값이 없을 때 기본으로 할당해 줄 값인 '기본값(default value)'을 설정할 수 있다.`

```js
// 기본값
let [name = 'Guest', surname = 'Anonymous'] = ['Julius'];

alert(name); // Julius (배열에서 받아온 값)
alert(surname); // Anonymous (기본값)
```

복잡한 표현식이나 함수 호출도 기본값이 될 수 있다. 이렇게 기본식으로 표현식이나 함수를 설정하면 할당할 값이 없을 때 표현식이 평가되거나 함수가 호출된다.

### 객체 분해

```js
let options = {
  title: 'Menu',
  width: 100,
  height: 200,
};
//  할당 연산자 우측엔 분해하고자 하는 객체를, 좌측엔 상응하는 객체 프로퍼티의 '패턴’을 넣는다. //
let { title, width, height } = options;

alert(title); // Menu
alert(width); // 100
alert(height); // 200
```

프로퍼티 options.title과 options.width, options.height에 저장된 값이 상응하는 변수에 할당된 것을 확인할 수 있다.

```js
let options = {
  title: 'Menu',
  width: 100,
  height: 200,
};

// { 객체 프로퍼티: 목표 변수 }
let { width: w, height: h, title } = options;

// width -> w
// height -> h
// title -> title

alert(title); // Menu
alert(w); // 100
alert(h); // 200
```

콜론은 '분해하려는 객체의 프로퍼티: 목표 변수’와 같은 형태로 사용한다. 위 예시에선 프로퍼티 `width`를 변수 `w`에, 프로퍼티 `height`를 변수 `h`에 저장했다.

> 프로퍼티가 없는 경우를 대비하여 =을 사용해 기본값을 설정하는 것도 가능하다.

콜론과 할당 연산자를 동시에 사용할 수도 있다.

```js
let options = {
  title: 'Menu',
};

let { width: w = 100, height: h = 200, title } = options;

alert(title); // Menu
alert(w); // 100
alert(h); // 200
```

### 중첩 구조 분해 (nested destructuring)

객체나 배열이 다른 객체나 배열을 포함하는 경우, 좀 더 복잡한 패턴을 사용하면 중첩 배열이나 객체의 정보를 추출할 수 있다. 이를 중첩 구조 분해(nested destructuring)라고 한다.

아래 예시에서 객체 options의 size 프로퍼티 값은 또 다른 객체이다. items 프로퍼티는 배열을 값으로 가지고 있다.

```js
let options = {
  size: {
    width: 100,
    height: 200,
  },
  items: ['Cake', 'Donut'],
  extra: true,
};
```

`대입 연산자 좌측의 패턴은 정보를 추출하려는 객체 options와 같은 구조를 갖추고 있다.`

```js
// 코드를 여러 줄에 걸쳐 작성해 의도하는 바를 명확히 드러냄
let {
  size: {
    // size는 여기,
    width,
    height,
  },
  items: [item1, item2], // items는 여기에 할당함
  title = 'Menu', // 분해하려는 객체에 title 프로퍼티가 없으므로 기본값을 사용함
} = options;

alert(title); // Menu
alert(width); // 100
alert(height); // 200
alert(item1); // Cake
alert(item2); // Donut
```

변수 `width`, `height`, `item1`, `item2`엔 원하는 값이, `title`엔 기본값이 저장되었다.

그런데 위 예시에서 `size`와 `items` 전용 변수는 없다는 점에 유의해야 한다. 전용 변수 대신 우리는 `size`와 `items` 안의 정보를 변수에 할당했다.
