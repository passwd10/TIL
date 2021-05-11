# tsconfig.json

## 속성별 특징

- allowJS : JavaScript 파일의 컴파일을 허용
- noImplicitAny : any타입으로 암시한 표현식과 선언에 오류 발생
- removeComments : /*!로 시작하는 copy-right 헤더 주석을 제외한 모든 주석을 제거합니다.
- sourceMap : 해당하는 .map 파일을 생성
- rootDir : 입력파일의 루트 디렉토리를 지정. outDir로 출력 디렉토리 구조를 제어하기 위해서만 사용합니다.
- outDir : 출력 구조를 디렉토리로 리다이렉트합니다.

## sourceMap

해당 속성을 true로 하면 컴파일 후 .map 파일을 생성한다. .map파일은 TS코드를 디버깅할 때 사용한다. TS는 컴파일 후 JS를 생성하고 실제 실행되는 코드역시 JS다. 따라서 실행환경에서는 기존의 TS코드에 접근하여 디버깅할 수 없는데 .map파일이 이를 가능케한다. .map은 JS와 TS를 매핑해주기 때문에 TS원본코드에 접근하여 디버깅할 수 있다. 단 Chrome에서 sourceMap을 정상적으로 사용하려면 Chrome Devtool에서

- Automatically reveal files in navigator
- Enable JavaScript source maps

속성을 체크해줘야한다.

## 참고

- https://typescript-kr.github.io/pages/compiler-options.html
- [sourceMap](https://www.typescriptlang.org/tsconfig#sourceMap)
- [sourceMap 영상](https://www.youtube.com/watch?v=4oQutHz96is)
