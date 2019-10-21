
## 객체

자바스크립트는 객체(object) 기반의 스크립트 언어이며 자바스크립트를 이루고 있는 거의 “모든 것”이 객체이다. 원시 타입(Primitives)을 제외한 나머지 값들(함수, 배열, 정규표현식 등)은 모두 객체이다.

자바스크립트의 객체는 키(key)과 값(value)으로 구성된 프로퍼티(Property)들의 집합이다. 

객체 생성

가장 일반적인 자바스크립트의 객체 생성 방식이다. 클래스 기반 객체 지향 언어와 비교할 때 매우 간편하게 객체를 생성할 수 있다. 중괄호({})를 사용하여 객체를 생성하는데 {} 내에 1개 이상의 프로퍼티를 기술하면 해당 프로퍼티가 추가된 객체를 생성할 수 있다. {} 내에 아무것도 기술하지 않으면 빈 객체가 생성된다.
```
const person = {
  name: 'Lee',
  gender: 'male',
  sayHello: function () {
    console.log('Hi! My name is ' + this.name);
  }
};

console.log(typeof person); // object
console.log(person); // {name: "Lee", gender: "male", sayHello: ƒ}

person.sayHello(); // Hi! My name is Lee
```

## 배열

배열 생성
0개 이상의 값을 쉼표로 구분하여 대괄호([])로 묶는다. 첫번째 값은 인덱스 ‘0’으로 읽을 수 있다. 존재하지 않는 요소에 접근하면 undefined를 반환한다.

```
const arr = [
  'zero', 'one', 'two', 'three', 'four',
  'five', 'six', 'seven', 'eight', 'nine'
];

console.log(arr[1]);      // 'one'
console.log(arr.length);  // 10
console.log(typeof arr);  // object
```
위의 배열을 객체 리터럴로 유사하게 표현
```
const obj = {
  '0': 'zero',  '1': 'one',   '2': 'two',
  '3': 'three', '4': 'four',  '5': 'five',
  '6': 'six',   '7': 'seven', '8': 'eight',
  '9': 'nine'
};
```

### forEach
- [참조링크](https://poiemaweb.com/js-array-higher-order-function)

- forEach 메소드는 for 문과는 달리 break 문을 사용할 수 없다. 다시 말해, 배열의 모든 요소를 순회하며 중간에 순회를 중단할 수 없다.

- forEach 메소드는 for 문에 비해 성능이 좋지는 않다. 하지만 for 문보다 가독성이 좋으므로 적극 사용을 권장한다.
```
// forEach

const numbers = [1, 3, 5];

numbers.forEach(function (item, index, self) {
    console.log(`numbers[${index}] = ${item}`);
});

/*
numbers[0] = 1
numbers[1] = 3
numbers[2] = 5
 */

numbers.forEach(function (item, index, self) {
    self[index] = Math.pow(item, 2);
});

console.log(numbers);   // Array(3) [1, 9, 25]

```

### map

- 배열을 순회하며 각 요소에 대하여 인자로 주어진 **콜백 함수의 반환값으로 새로운 배열을 생성하여 반환한다.** 이때 원본 배열은 변경되지 않는다.
- forEach 메소드는 배열을 순회하며 요소 값을 참조하여 무언가를 하기 위한 함수이며 map 메소드는 배열을 순회하며 요소 값을 다른 값으로 맵핑하기 위한 함수이다.

```
// map

const numbers = [1, 4, 9];

const roots = numbers.map(function (item) {
    return Math.sqrt(item);
});

// const roots = numbers.map(Math.sqrt);
console.log(roots); // [1, 2, 3]
```

### reduce
- 배열을 순회하며 각 요소에 대하여 이전의 콜백함수 실행 반환값을 전달하여 콜백함수를 실행하고 그 결과를 반환한다
    ```
    // reduce

    const arr = [1, 2, 3, 4, 5];

    /*
    previousValue: 이전 콜백의 반환값
    currentValue : 배열 요소의 값
    currentIndex : 인덱스
    array        : 메소드를 호출한 배열, 즉 this
    */
    // 합산
    const sum = arr.reduce(function(previousValue, currentValue,    currentIndex, self) {
        console.log(previousValue + '+' + currentValue + '=' + (previousValue + currentValue));

        return previousValue + currentValue;
    })

    console.log(sum); // 15: 1~5까지의 합
    /*
    1: 1+2=3
    2: 3+3=6
    3: 6+4=10
    4: 10+5=15
    15
    */

    // 최대값 취득
    const max = arr.reduce(function (pre, cur) {
        return pre > cur ? pre : cur;
    });
  
  console.log(max); // 5: 최대값
  ```

### filter
- if문을 대체할 수 있다.
- 배열을 순회하며 각 요소에 대하여 인자로 주어진 **콜백함수의 실행 결과가 true인 배열 요소의 값만을 추출한 새로운 배열을 반환한다.**
- 배열에서 특정 케이스만 필터링 조건으로 추출하여 새로운 배열을 만들고 싶을 때 사용한다. 이때 원본 배열은 변경되지 않는다.
```
const result = [1, 2, 3, 4, 5].filter(function (item, index, self) {
    return item % 2;
});

console.log(result); // [1, 3, 5]
```

### some
- 배열 내 일부 요소가 콜백 함수의 테스트를 통과하는지 확인하여 그 결과를 boolean으로 반환한다. 
```
let res = [2, 5, 8, 1, 4].some(function (item) {
    return item > 10;
});

console.log(res); //false

let ras = [1,2,3].some(item => item > 2);
console.log(ras); //true
```
### every
- 배열 내 모든 요소가 콜백함수의 테스트를 통과하는지 확인하여 그 결과를 boolean으로 반환한다.
```
let res = [2, 5, 8, 1, 4].every(function (item) {
    return item < 10;
});

console.log(res); //true

let ras = [1,2,3].every(item => item > 2);
console.log(ras); //false
```

## 함수 선언식 vs 함수 표현식
- 함수 선언식 : 일반적인 프로그래밍 언어에서의 함수 선언과 비슷한 형식
    ```
    function funcDeclarations() {
        return 'A function declaration';
    }
    funcDeclarations(); 
    ```

- 함수 표현식 : 함수 표현식 방식으로 정의한 함수는 함수명을 생략할 수 있다. 이러한 함수를 익명 함수(anonymous function)이라 한다. 함수 표현식에서는 함수명을 생략하는 것이 일반적이다.
    ```
    var funcExpression = function () {
        return 'A function expression';
    }
    funcExpression(); // 'A function expression'
    ```

- 함수 선언식과 표현식의 차이점 ([참고링크](https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/))

     1. 함수 선언식은 호이스팅에 영향을 받지만, 함수 표현식은 호이스팅에 영향을 받지 않는다 
     
         -> 함수 호이스팅은 함수를 사용하기 전에 반드시 함수를 선언해야한다는 규칙을 무시하므로 코드 구조를 엉성하게 만들 수 도 있으므로 함수 표현식을 권장한다

    2. 함수 표현식으로 클로져 생성

    3. 함수 표현식을 다른 함수의 인자 값으로 넘김




## 화살표 함수(arrow function)
- 화살표 함수(Arrow function)는 function 키워드 대신 화살표(=>)를 사용하여 보다 간략한 방법으로 함수를 선언할 수 있다. 
- 화살표 함수는 익명 함수로만 사용할 수 있다. 따라서 화살표 함수를 호출하기 위해서는 함수 표현식을 사용한다.
    ```
    const pow = x => x * x;
    console.log(pow(10)); // 100
    ```
- 콜백함수로 사용할 수 있다.
    ```
    const arr = [1, 2, 3];
    const pow = arr.map(x => x * x);

    console.log(pow); // [ 1, 4, 9 ]
    ```
- [this](https://poiemaweb.com/js-this)
- 사용해서는 안되는 경우
    
    1. 화살표 함수로 메소드를 정의하는 것은 피해야 한다.
    ```
    // Bad
    const person = {
        name: 'Lee',
        sayHi: () => console.log(`Hi ${this.name}`)
    };

    person.sayHi(); // Hi undefined
    // 메소드를 호출한 객체를 가리키지 않고 상위 컨택스트인 전역 객체 window를 가리킨다
    ```

    2. 화살표 함수로 정의된 메소드를 prototype에 할당하는 경우도 동일한 문제가 발생한다.

    3. 화살표함수는 생성자 함수로 사용할 수 없다.
    4. addEventListener 함수의 콜백 함수를 화살표 함수로 정의하면 this가 상위 컨택스트인 전역 객체 window를 가리킨다.

## destructuring(디스트럭쳐링)
- 디스트럭처링(Destructuring)은 구조화된 배열 또는 객체를 Destructuring(비구조화, 파괴)하여 개별적인 변수에 할당하는 것이다. 배열 또는 객체 리터럴에서 필요한 값만을 추출하여 변수에 할당하거나 반환할 때 유용하다.

```
// ES6 Destructuring
const arr = [1, 2, 3];

// 배열의 인덱스를 기준으로 배열로부터 요소를 추출하여 변수에 할당
// 변수 one, two, three가 선언되고 arr(initializer(초기화자))가 Destructuring(비구조화, 파괴)되어 할당된다.
const [one, two, three] = arr;
// 디스트럭처링을 사용할 때는 반드시 initializer(초기화자)를 할당해야 한다.
// const [one, two, three]; // SyntaxError: Missing initializer in destructuring declaration

console.log(one, two, three); // 1 2 3
```

- 객체 디스트럭처링은 객체의 각 프로퍼티를 객체로부터 추출하여 변수 리스트에 할당한다. 이때 할당 기준은 프로퍼티 이름(키)이다.
```
// ES6 Destructuring
const obj = { firstName: 'Ungmo', lastName: 'Lee' };

// 프로퍼티 키를 기준으로 디스트럭처링 할당이 이루어진다. 순서는 의미가 없다.
// 변수 lastName, firstName가 선언되고 obj(initializer(초기화자))가 Destructuring(비구조화, 파괴)되어 할당된다.
const { lastName, firstName } = obj;

console.log(firstName, lastName); // Ungmo Lee
```
- 객체 디스트럭처링을 위해서는 할당 연산자 왼쪽에 객체 형태의 변수 리스트가 필요하다.

