# Commit Message

## Commit Message 작성법
    [type](optional scope) : [subject] ,  
    [optional body]  
    [optional footer]  

####
    feat(HeaderAction) : Add dropdown animation,
    div box animation not yet applied
    fixes # 0000

### type의 종류
- feat :	새로운 기능 추가
- fix :	버그 수정
- docs : 문서 수정
- style :	코드 formatting, 세미콜론(;) 누락, 코드 변경이 없는 경우
- refactor :	코드 리팩터링
- test :	테스트 코드, 리팩터링 테스트 코드 추가(프로덕션 코드 변경 X)
- chore	: 빌드 업무 수정, 패키지 매니저 수정(프로덕션 코드 변경 X)
- design :	CSS 등 사용자 UI 디자인 변경
- build	: 관련 변경 사항 빌드
- ci : CI 관련 변경 사항
- perf : 성능을 향상시키는 코드 변경
- comment : 필요한 주석 추가 및 변경
- revert : 되돌리기
- rename : 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우
- remove :	파일을 삭제하는 작업만 수행한 경우
- !BREAKING CHANGE : 커다란 API 변경의 경우
- !HOTFIX : 급하게 치명적인 버그를 고쳐야 하는 경우

### scope
- 선택사항이며, 변경된 부분을 표기한다.
- 함수가 변경됐으면 함수명을 필드나 메소드가 변경됐으면 클래스 명을 입력한다.

### subject
- 변경사항을 나타내는 제목을 입력한다.
- 제목의 첫글자는 대문자로 작성한다.
- 제목줄은 50자 이내가 좋다.
- 제목 줄을 마침표로 끝내지 않는다.

### body
- commit messege의 각 line은 72 글자를 넘기지 않아야 한다.
- 명령문, 현재 시제로 작성하는 것이 좋다.
- 변경한 이유, 변경 전과 후의 차이점을 기재한다.
- 어떻게 했는지 보다 무엇을 왜 했는지 작성한다.

### footer
- 메세지 하단에는 변경점, 변경 사유, 마이그레이션 지시 기록한다.
- 관련된 이슈를 번호와 함께 언급한다.
- 주로 Closes(종료), Fixes(수정), Resolves(해결), Ref(참고), Related to(관련) 키워드를 사용한다.


