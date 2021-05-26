# react-redux

## Provider

Provider 컴포넌트 하위에 있는 컴포넌트는 리덕스의 상태값이 변경되면 자동으로 컴포넌트 함수가 호출되도록 할 수 있다.

```javascript
// ...
import store from './store';
import { Provider } from 'react-redux';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>
)
```
스토어 객체를 Provider 컴포넌트의 속성값으로 넣는다. `Provider 컴포넌트는 전달받은 스토어 객체의 subscribe 메서드를 호출해서 액션 처리가 끝날 때 마다 알림을 받는다`. 그 다음 Context API를 사용해서 리덕스의 상태값을 하위 컴포넌트로 전달한다.

## useSelector

useSelector hook은 리덕스의 상태값이 변경되면 이전 반환값과 새로운 반환값을 비교한다. 두 값이 다른 경우에만 컴포넌트를 리렌더링한다.

useSelector로 여러 상태값을 가져오려면 선택자 함수가 객체를 반환해야 한다. 이 때 객체 리터럴 문법을 이용하면 실제 상태값이 바뀌지 않아도 매번 새로운 객체가 반환되어 문제가 된다. 이를 위해 다음과 같은 방법을 이용할 수 있다.

- useSelector를 필요한 상태값 개수만큼 사용한다.
    - useSelector를 여러번 사용한다고 특별히 성능이 떨어지진 않는다. 코드를 여러번 작성하는 번거로움을 감수할 수 있다면 이 방법을 사용해도 좋다.
- 메모이제이션을 이용한다.
    - reselect와 같은 라이브러리의 메모이제이션 기능을 이용한다.
- useSelector의 두번째 매개변수를 활용한다.
    - 두번째 매개변수는 컴포넌트 렌더링 여부를 판단하는 역할을 한다. 이 때 매개변수를 입력하지 않으면 참조값만 비교하는 단순비교함수가 된다.(객체 리터럴 반환시 불필요한 렌더링 발생)

```javascript
import { shallowEqual } from 'react-redux';

export default function MyComponent() {
  const [value1, value2, value3] = useSelector(
    state => [state.value1, state.value2, state.value3],
    shallowEqual
  )
  // 두 번째 매개변수에 shallowEqual 함수를 입력하면 배열의 각 원소가 변경됐는지 검사한다.
}
```
