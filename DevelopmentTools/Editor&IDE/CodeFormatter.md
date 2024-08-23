# Code Formatter

## 1. What is Prettier?
- 코드 포멧터란 개발자가 작성한 코드를 정해진 코딩 스타일에 따르도록 변환해주는 도구를 말한다.
- Prettier 는 이러한 코드 포멧터 중에서도 최근에 가장 인기를 많이 얻어 거의 표준이 되어가고 있는 자바스크립트 라이브러리이다.
- 코드 저장 시 정해놓은 규칙에 맞게 자동으로 정렬해서 가독성을 높이고 코드 스타일을 통일할 수 있다.

## 2. How to use Prettier?
- IDEA [settings] -> [plugins] -> [Prettier] -> [insatll] -> IDE restart
- 정확히 일치하는 버전의 패키지 추가

        % npm install --save-dev --save-exact prettier
- IDEA [settings] -> [Languages&Framworks] -> [JavaScript] -> [Prettier]
- Node Interpreter: 프로젝트에 사용중인 버전의 node 선택
- Prettier package: 프로젝트 루트 디렉토리/node_modules/prettier 모듈 디렉토리 선택
- .prettierrc.js 파일 생성ㅇ

        module.exports = {
              semi: true,
              trailingComma: 'all',
              singleQuote: ture,
              printWidth: 100,
              ttabWidth: 2,
        };
- Prettier 적용 [Ctrl + Shift + Alt + P]
