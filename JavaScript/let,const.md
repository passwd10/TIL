## var 

var 키워드로 선언된 변수의 특징
1. 함수 레벨 스코프
    - 함수의 코드 블록만을 스코프(유효범위)로 인정. 따라서 전역 함수 외부에서 생성한 변수는 모두 전역 변수. 이는 전역 변수를 남발할 가능성을 높임
    - for문의 변수 선언문에서 선언한 변수를 for문의 코드 블록 외부에서 참조할 수 있다.
2. var 키워드 생략 허용
    - 암묵적 전역 변수를 양산할 가능성이 크다.
3. 변수 중복 선언 허용
    - 의도하지 않은 변수값의 변경이 일어날 가능성이 크다.
4. 변수 호이스팅
    - 변수를 선언하기 이전에 참조할 수 있다.

전역변수는 유효범위(scope)가 넓어서 어디에서 어떻게 사용될 것인지 파악하기 힘들며, 비순수 함수에 의해 의도하지 않게 변경될 수도 있어서 복잡성을 증가시킨다.


## let

1. let 키워드로 선언된 변수는 **블록레벨스코프**를 따른다.

    대부분의 프로그래밍 언어는 **블록레벨스코프**를 따르지만 자바스크립트는 **함수레벨스코프**를 따른다

    ```
    블록레벨스코프
    모든 코드블록(함수, if문, for문, while문 등) 내에서 선언된 변수는 코드 블록 내에서만 유효하며 블록 외부에서는 참조 불가. 즉 코드 블록 내부에서 선언한 변수는 지역 변수이다.

    함수레벨스코프
    함수 내에서 선언된 변수는 함수 내에서만 유효하며 함수 외부에서는 참조 불가. 함수 내부에서 선언함 변수는 지역변수이며 외부에서 선언한 변수는 모두 전역변수이다
    ```
2. 변수 중복 선언 금지
    ```
    var foo = 123;
    var foo = 456; // 중복 선언 허용

    let bar = 123;
    let bar = 456; //중복 선언 불가
    ```

3. 호이스팅

    호이스팅 : var, function등을 선언하고 초기화했을 때 선언 부분이 최상단으로 끌어올려지는 것처럼 동작하는 특성

    var 키워드로 선언된 변수는 선언단계와 초기화 단계가 한번에 이루어진다.
    ```
    // 스코프의 선두에서 선언 단계와 초기화 단계가 실행된다.
    // 따라서 변수 선언문 이전에 변수를 참조할 수 있다.
    console.log(foo); // undefined 

    var foo;
    console.log(foo); // undefined

    foo = 1; // 할당문에서 할당 단계가 실행된다.
    console.log(foo); // 1
    ```

    let 키워드로 선언된 변수를 선언문 이전에 참조하면 에러가 발생.

    ```
    // 스코프의 선두에서 선언 단계가 실행된다.
    // 아직 변수가 초기화(메모리 공간 확보와 undefined로 초기화)되지 않았다.
    // 따라서 변수 선언문 이전에 변수를 참조할 수 없다.
    console.log(foo); // ReferenceError: foo is not defined

    let foo; // 변수 선언문에서 초기화 단계가 실행된다.
    console.log(foo); // undefined

    foo = 1; // 할당문에서 할당 단계가 실행된다.
    console.log(foo); // 1
    ```

## const

const는 상수(변하지 않는 값)를 위해 사용한다. 하지만 반드시 상수만을 위해 사용하지는 않는다.

1. 선언과 초기화
    - let은 할당이 자유로우나 const는 재할당이 금지된다.
    - 주의할점. const는 반드시 선언과 동시에 할당이 이루어져야함
    - let과 마찬가지로 블록레벨스코프를 갖는다.

2. 상수
    - 상수는 가독성과 유지보수의 편의를 위해 적극적으로 사용해야한다.
    ```
    // 10의 의미를 알기 어렵기 때문에 가독성이 좋지 않다.
    if (rows > 10) {
    }

    // 값의 의미를 명확히 기술하여 가독성이 향상되었다.
    const MAXROWS = 10;
    if (rows > MAXROWS) {
    }
    ```

3. 객체
    - const 변수의 타입이 객체인 경우, 객체에 대한 참조를 변경하지 못한다. 하지만 **객체의 프로퍼티는 보호되지 않는다.** 재할당은 불가능하지만 할당된 객체 내용은 변경할 수 있다.
    ```
    const user = { name: 'Lee' };

    // const 변수는 재할당이 금지된다.
    // user = {}; // TypeError: Assignment to constant variable.

    // 객체의 내용은 변경할 수 있다.
    user.name = 'Kim';

    console.log(user); // { name: 'Kim' }
    ```
    따라서 **객체 타입 변수 선언에는 const를 사용하는것이 좋다.**


## var vs let vs const

- 변수 선언에는 기본적으로 const를 사용
- let은 재할당이 필요한 경우에 한정해 사용(객체 재할당하는 경우는 생각보다 흔하지않음) 이때 변수의 스코프 최대한 좁게!
- ES6를 사용한다면 var키워드는 X
- 변경이 발생하지 않는 원시값과 객체는 const사용