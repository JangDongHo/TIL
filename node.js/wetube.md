![Wetube](https://nomadcoders.co/_next/image?url=https%3A%2F%2Fd1telmomo28umc.cloudfront.net%2Fmedia%2Fpublic%2Favatars%2FytThumbnail_rtMv4Du.jpg&w=1920&q=75)

> 위 문서는 [노마드코더 유튜브 클론코딩](https://nomadcoders.co/kokoa-clone/lobby) 강의에서 중요하다고 생각하는 내용들을 요약한 것입니다.

# #1 INTRODUCTION

## #1.3 What is NodeJS

- NodeJS는 쉽게 말하면 크롬 V8 자바스크립트 엔진으로 빌드된 자바스크립트 런타임이다.
- NodeJS는 브라우저 밖에서 돌아가는 자바스크립트라고 생각하면 된다. 브라우저에서만 작동하던 JS를 다른 프로그래밍 언어처럼 다른 곳에서도 쓸 수 있게 만들었다.

## #1.4 What is NPM

- npm은 자바스크립트 언어를 위한 패키지 매니저다.
- npm과 nodeJS는 서로 상호작용하므로 같이 써야한다.
- 앞으로 대부분은 npm 명령어를 쓰고, 가끔 node 명령어를 쓴다.
- npm을 사용하면 다른 누군가 이미 만들어 놓은 패키지를 가져다 쓰기 정말 쉽다. (개발시간 단축)
- 유명한 패키지 중 하나는 `express`

# #2 SET UP

## #2.0 Your First NodeJS Project

- json: 프로그래머가 파일에 정보를 저장하기 위해 만든 방식 중 하나 (파일에 정보를 입력하는 방식)
- node.js는 `package.json`으로 파일명을 써야한다.

### 준비하기

1. vs code 터미널 열기
2. git init 입력 (소스 코드를 git으로 관리하겠다는 선언)
3. github repo 생성
4. git remote add origin [repo-url] (github 연결)
5. npm init

## #2.1 Installing Express

### package.json 설명

- main: 우리가 만들고 배포한 package를 다른 사람들이 설치하면 main을 사용한다.
- scripts: 실행하고 싶은 것

> 터미널에 `npm run 이름` 입력 시 파일 실행

### npm install 패키지명

- 패키지들을 설치한다. 설치된 패키지들은 `node_modules` 폴더에 저장된다.

- express를 사용하려면 다른 패키지도 설치해야 한다.
  - 어떤 패키지를 설치해야하는지 확인하려면 해당 패키지의 package.json에 들어가 `dependencies` 부분을 참고한다.
  - 이 모든건 npm이 참고해서 알아서 설치해주니, 우리는 신경 쓸 필요없다!

## #2.2 Understanding Dependencies

- `npm i` 만 쳐도 npm이 알아서 `dependencies` 를 참고해서 필요한 모듈들을 자동을 설치해준다.
- 만약 팀으로 NodeJS 프로젝트를 진행하거나 컴퓨터를 바꿀 때 깃허브에 node_moduels를 따로 올려줄 필요 없이 package.json만 있으면 설치가 가능하니 너무 편리하다.

### package-lock.json

- 패키지들을 안전하게 관리해준다.
- 패키지가 수정됐는지 해시값으로 체크해준다.
- 다른 사람들이 npm으로 모듈을 설치할 때 이 파일을 참고해서 **똑같은 버전**으로 설치한다.
