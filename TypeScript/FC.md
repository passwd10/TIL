# Function Component

사용했을 때
```tsx
import React, { FC } from 'react'

type Props = {
  who: string
  greeting: string
}

const Greeter: FC<Props> = (props) => {
  return (
    <div>
      {props.greeting} {props.who}
    </div>
  )
}
```

사용하지 않을 때
```tsx
import React from 'react'

type Props = {
  who: string
  greeting: string
}

const Greeter = (props: Props) => {
  return (
    <div>
      {props.greeting} {props.who}
    </div>
  )
}
```

## 사용했을 때

- defaultProps, propTypes, contextTypes, displayName 설정시 자동완성이된다.
- children이 옵셔널로 들어가있어 props의 타입이 명백하지 않다.
- defaultProps가 제대로 동작하지 않는다. ([참고](https://react.vlpt.us/using-typescript/02-ts-react-basic.html))

## 사용하지 않을 때

- 심플하며 바닐라 JS 패턴과 유사하다.
- props의 children을 명시적으로 정의함으로써 확실한 타입을 보장한다.

## etc

- defaultProps : 기본 props를 명시적으로 설정
- propTypes : prop의 각각의 타입을 설정
- displayName : 디버깅 메시지 표시에 사용됩니다. 디버깅시 다른 이름을 표시하거나 고차 컴포넌트 생성을 위해 명시적으로 설정한다.
