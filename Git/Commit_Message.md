# Commit Message Convetion
<https://doublesprogramming.tistory.com/256>

### Commit Message Structure

모든 커밋 메시지는 다음과 같이 세 영역으로 구성되며, 각 영역은 빈줄로 분리된다.
```
type : subject

body

footer
```
### Commit Type
- feat : 새로운 기능 추가
- fix : 버그 수정
- docs : 문서 수정
- style : 코드 포멧팅, 세미콜론 누락, 코드변경이 없는경우
- refactor : 코드 리펙토링
- test : 테스트 코드, 리펙토링 테스크 코드 추가
- chore : 빌드 업무 수정, 패키지 매니저 수정

### Subject
- 대문자로 작성, 마침표X, 과거시제X, 명령어O

### Body
- 선택사항이기 때문에 모든 커밋에 본문내용을 작성할 필요는 없다.
- 부연설명이 필요하거나 커밋의 이유를 설명할 경우 작성
- 72자를 넘지않고 제목과 구분되기 위해 한칸을 띄워 작성

### footer
- 선택사항이기 때문에 모든 커밋에 꼬리말을 작성할 필요는 없다
- issue tracker id를 작성할 때 사용한다.

