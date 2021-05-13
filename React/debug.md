# debug

vscode에서 React 디버깅하기 (+ webpack)

## 준비

1. vscode에서 `Debugger for Chrome` extension 설치
2. launch.json파일의 webRoot 경로설정 (경로설정이 잘못되어있다면 breakpoint를 잡지못함)
3. webpack에서 `source-map` 설정 (번들파일로는 디버깅을할 수 없기 때문에 번들된 코드와 원본 코드를 매핑해야한다)
4. webpack `mode`를 `development`로 설정 (production mode는 코드양을 줄이기 위해 코드를 간단한 형태로 압축해버려서 디버깅시 개발자가 코드를 알아볼 수 없음)
5. 개발 생산성 향상을 위해 webpack에 `HTMLWebpackPlugin`과 `HOTModuleReplacementPlugin` 추가
  - HTMLWebpackPlugin : HTML에 자동으로 bundle 경로가 들어있는 script를 추가해줌.
  - HOTModuleReplacementPlugin : 코드가 변경될 때 마다 실시간으로 변경사항을 반영함.
6. webpack serve 실행
7. vscode에서 Start Debugging
