# require, import, exports

## import

```
// file1.js
export {
    a: "a",
    b: "b",
    c: "c",
};

// file2.js
import { a } from './file1';
console.log(a);
```
실제로 사용할 a값을 가져올 수 있으며 나머지 값들은 tree shaking으로 인해 빌드에서 제거됩니다. 즉 불필요한 파일을 제거합니다.
```
// 모듈 전체를 import
import module
import module as myModule


// 모든 속성 import
import * from module


// 특정 멤버(함수 등)만 import
import {moduleFunc, moduleFunc2} from module
```
## require

동적으로 모듈을 불러올 수 있지만, 불필요한 코드들까지 불러오기 때문에 실제로 어떤 코드가 사용되었는지 명확히 알수가 없습니다.
```
// 모듈 전체를 import
var module = require('./someModule.js')
```

## exports

- 여러개의 객체를 내보낼 경우, exports 변수의 속성으로 할당한다.
```
exports.canadianToUs = canadianToUs;    // 내보내기1
exports.usToCanadian = usToCanadian;    // 내보내기2
```
- 딱 하나의 객체를 내보낼 경우, module.exports 변수 자체에 할당한다.
```
module.exports = obj;
```


## Module.exports, export default 차이

- default가 기본값. import 시 괄호가 없어도 값이 저절로 저장된다. 변수명도 마음대로 받아올 수 있다.
- Module 객체에 담아서 보내면 이름 변경x, 변경하려면 as를 붙여야 한다