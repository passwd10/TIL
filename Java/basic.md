### JVM(Java Virtual Machine)
자바 소스코드로부터 만들어지는 자바 바이너리 파일(.class)을 실행할 수 있다. 또한 플랫폼에 의존적이다.
리눅스의 JVM과 윈도우즈의 JVM은 다르다. 단 컴파일된 바이너리 코드는 어떤 JVM에서도 동작시킬 수 있다.
- 바이너리 코드(자바파일을 컴파일하면 바이너리코드가 됨) 를 읽는다.
- 바이너리 코드를 검증한다.
- 바이너리 코드를 실행한다.
- 실행환경(Runtime Environment)의 규격을 제공한다. (필요한 라이브러리 및 기타파일)

### JRE(Java Runtime Environment)
자바 실행환경. JRE는 JVM이 자바 프로그램을 동작시킬 때 필요한 라이브러리 파일들과 기타 파일들을 갖고있다.
물리적으로 존재하는 JVM을 구현하는 역할을 한다.

### JDK(Java Development Kit)
자바 개발도구. JRE + 개발툴을 포함한다.

### 기초
환경변수 설정 이유
- 환경변수에 등록된 경로는 컴퓨터의 어떤 경로에서라도 접근(=실행) 할 수 있다.
즉 파일의 접근을 쉽고 편하게 하기위해 환경설정을 하는것.

import
- 외부 패키지의 클래스를 불러올때 클래스명 앞에 패키지를 명시할 필요 없이 바로 사용할수있음

System
- System클래스는 JVM의 표준 장치를 뜻하는 클래스이다. 

문자 입력받기
- 자바는 문자를 입력받는 기능이 없으므로 String에서 첫번째 문자를 꺼내와야한다.
- Scanner sc = new Scanner(System.in);
- char chr = sc.next().charAt(0);

소수점나타내기

- Math.round()
- double pie - 3.1415926;
- Math.round(pie) => 3
- Math.round(pie*100)/100.0 => 3.14
- Math.round(pie*1000)/1000.0 => 3.142

- String.format()
- String.format("%.2f", pie) => 3.14
- String.format("%.3f", pie) => 3.142