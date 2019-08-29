### 안드로이드 (app)폴더 구조

1. manifest
 - AondroidManifest.xml : 안드로이드 어플리케이션을 구동하는데 필요한 설정값을 관리 (컨트롤타워)
 - 안드로이드 프로젝트는 "application"위에 "activity"가 실행되는 구조이다.

2. java ( 클래스를 관리하는 폴더 )
 - setContentView(R.layout.activity_main) : layout 패키지 아래에 있는 activity_main.xml이라는 파일을 View로 연결한다. 
 - Activity 파일과 Xml파일은 언제나 한쌍이다.

3. res ( Resource 폴더로 UI와 관련된 파일과 디자인 리소스, 문자열 리소스를 담고있는 폴더 )
  - drawable : 이미지 파일 저장 패키지
  - layout : 디자인의 뼈대
  - mipmap : 이미지(앱 아이콘) 저장 패키지
  - values : 컬러값 + 문자열값 + 스타일값 저장 파일 패키지

### Gradle Scripts
- 어플리케이션을 빌드하기위해 필요한 설정 옵션, 라이브러리 정보들이 들어있음