# tailwindcss

## utility-based styling

- component-based를 사용했을 때 발생하는 CSS의 중복문제를 해결해준다.

- class name을 고민하는데 시간을 낭비하지 않아도 된다.

- CSS가 계속해서 커지는걸 방지한다. 기존 CSS는 기능이 추가될수록 크기가 점점 커졌다. 하지만 utilities를 사용하면 모든걸 재사용할 수 있어서 CSS를 새로작성하지 않아도 된다.

- CSS는 글로벌하기 때문에 변경시 어디가 문제인지 발견하기가 어렵다. 하지만 tailwind는 클래스이름으로 로컬로 저장하기 때문에 문제를 발견하기 더 수월해진다.

- 미리 정의된 utilities만 사용할 수 있기 때문에 CSS의 magic number 사용을 방지한다.
