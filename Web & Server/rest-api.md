# [REST API](https://poiemaweb.com/js-rest-api)

"REST API를 위한 최고의 버저닝 전략은 버저닝을 안하는것"

REST API : REST 아키텍쳐 스타일을 따르는 API

### REST (Representational State Transfer)

- 분산 하이퍼미디어 시스템(예: 웹)을 위한 아키텍쳐 스타일
- 아키텍쳐 스타일 : 제약조건의 집합. 제약조건을 모두 지켜야 REST를 따른다
-  URI는 자원을 표현하는 데에 집중하고 행위에 대한 정의는 HTTP Method를 통해 하는 것

### REST는 어떤 제약조건이 있는가

REST를 구성하는 스타일
- client-server (http만 잘 따라도 지켜짐)
- stateless (http만 잘 따라도 지켜짐)
- cache (http만 잘 따라도 지켜짐)
- uniform interface 
- layered system (http만 잘 따라도 지켜짐)
- code-on-demand(optional) : 서버에서 코드를 클라이언트로 보내서 실행할 수 있어야한다.(자바스크립트)

Uniform Interface의 제약조건
1. identification of resources : resource가 uri로 식별돼야 한다 (잘 지킴)
2. manipulation of resources through representations : representation 전송을 통해서 resource를 조작해야한다(resource를 만들거나 업데이트하거나 삭제하거나 할때 http 메세지에 표현을 담아서 전송 / 잘 지킴)
3. self-descriptive messages (잘 못 지킴)
    - 메시지는 스스로를 설명해야한다
    - 목적지, Content-Type, Media-Type, 어떻게 해석하는가
    - 메시지를 봤을때 메시지의 내용만으로 온전히 해석이 다 가능해야함

4. hypermedia as the engine of application state(HATEOAS / 잘 못지킴)
    - HATEOAS : 애플리케이션의 상태가 Hyperlink를 이용해 전이되어야 한다
```
HTTP/1.1 200 OK
Content-Type: text/html

<html>
<head></head>
<body><a href="/test">text</a></body>
</html>

a태그를 통해서 하이퍼링크가 나와있고 하이퍼링크를 통해 전이가 가능하기 떄문에 HATEOAS 만족

```

Uniform Interface가 왜 필요한가?
독립적 진화를 위해
- 서버와 클라이언트가 각각 독립적으로 진화한다. 
- 서버가 기능이 변경되어도(새로운 api가 추가, 삭제 uri가 바뀌는등) 클라이언트가 업데이트할 필요가 없어짐 
- REST API를 만들게된 계기(내가 http를 고치면 web이 깨질꺼같은데 어떻게하면 이 문제를 해결할 수 있을까)

REST가 지켜지고 있는가? 사례

웹(잘 만족함)
- 웹 페이지를 변경했다고 웹 브라우저를 업데이트할 필요는 없다.
- 웹 브라우저를 업데이트 했다고 웹페이지를 변경할 필요도 없다.
- HTTP 명세가 변경되어도 웹은 잘 동작한다.(HTTP버전이 바뀌어도 접속잘됨)
- HTML 명세가 변경되어도 웹은 잘 동작한다.(HTML버전이 바뀌어도 접속잘됨)

어떻게 한걸까요?
- W3C Working groups(HTML 만듦)
- IETF Working groups(HTTP 만듦)
- 웹 브라우저 개발자들
- 웹 서버 개발자들

이 정도의 노력을 합니다
- HTML5 첫 초안에서 권고안 나오는데까지 6년
- HTTP/1.1 명세 개정판 작업하는데 7년
- 하위호환성을 깨뜨리면 안돼서 이렇게 오래 걸림

상호운용성(interoperability)에 대한 집착(지금 고치면 웹이 꺠짐)
- Referer 오타지만 안 고침
- charset 잘못 지은 이름이지만 안 고침
- HTTP 상태 코드 416 포기함(I'm a teapot)
- HTTP/0.9 아직도 지원함(크롬, 파이어폭스)

REST가 웹의 독립적 진화에 도움을 주었나
- HTTP에 지속적으로 영향을 줌
- HOST 헤더 추가
- 길이 제한을 다루는 방법이 명시(414 URI Too Long 등)
- URI에서 리소스의 정의가 추상적으로 변경됨: "식별하고자 하는 무언가"
- 기타 HTTP와 URI에 많은 영향을 줌
- HTTP/1.1 명세 최신판에서 REST에 대한 언급이 들어감
- Reminder: Roy T.Fielding이 HTTP와 URI 명세의 저자 중 한명입니다

REST는 성공했는가
- REST는 웹의 독립적 진화를 위해 만들어졌다
- 웹은 독립적으로 진화하고 있다 성공!

그런데 REST API는?
- REST API는 REST 아키텍쳐 스타일을 따라야한다.
- 오늘날 스스로 REST API라고 하는 API들의 대부분이 REST 아키텍쳐 스타일을 따르지 않는다.

REST API도 저 제약조건들을 다 지켜야 하는건가? 그렇다.

원격 API가 꼭 REST API여야 하는가?
- 시스템 전체를 통제할 수 있다고 생각하거나, 진화에 관심이 없다면, REST에 대해 따지느라 시간을 낭비하지 마라
