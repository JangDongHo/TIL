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

## #2.3 The Tower of Babel

### express 사용 방법

```js
const express = require("express"); // express 생성

const app = express(); // express 애플리케이션 생성
```

- 이 코드들은 너무 구식이라, 최신 자바스크립트 코드를 쓰려고 한다.
- NodeJS는 우리가 작성한 자바스크립트를 이해하겠지만 아직 NodeJS가 이해하지 못하는 최신 자바스크립트 코드가 있다.
- 그래서 두 가지 옵션이 있다.
  1. nodeJS가 이해하는 자바스크립트만 쓴다.
  2. `babel`을 사용한다. (babeljs.io)

### babel

- 우리가 작성한 최신 자바스크립트를 컴파일 해준다.
- nodeJS가 자바스크립트를 문제 없이 이해하도록 변환해준다.

`npm install --save-dev @babel/core`

- dependencies: 우리 프로젝트에 필요한 것
- devDependencies: 개발자에게 필요한 dependencies
- `--save-dev`: devDependencies에 저장한다.

### babel.config

- presets: babel을 위한 엄청 거대한 플러그인

## #2.4 Nodemon

### babel-node 실행방법

1. script에 `babel-node 파일명` 입력
2. 터미널에 `npm run 스크립트명` 입력

- `const express = require("express")` 보다는 `import express from "express"`가 더 이해가 잘된다.
- 결국, 후자는 최신 자바스크립트 코드기 때문에 babel이 필요했던 것
- 문제는, 내가 코드를 수정할 때마다 `npm run` 을 실행해갸 해서 매우 불편하다. 그래서 `nodemon` 이라는 패키지를 사용한다.

### nodemoon

- 우리가 만든 파일이 수정되는 걸 감시해주는 패키지이다.
- 파일이 수정되면 nodemon이 알아서 재시작을 해준다. 그러면 npm run을 계속 실행할 필요가 없다.
- 사용법은 스크립트에 `nodemon --exec babel-node 파일명` 을 작성한다. 그리고 `npm run 스크립트명` 을 최초 1회만 실행하면 된다.

# #3 INTRODUCTION TO EXPRESS

## #3.0 Your First Server

- 코드와 조직을 가지고 있는 모든 파일들을 src 안에 넣는다.

### server.js 구성

1. express import 하기

   ```js
   import express from "express";
   ```

   - node.js와 npm은 똑똑해서 `node_moduels/express`로 적지 않아도 알아서 찾아낸다.

2. express application 생성

   ```js
   const app = express();
   ```

3. app.listen(포트, 콜백함수)
   - app이 listen 할 수 있게 해야 한다.
   - 서버는 항상 켜져 있는 컴퓨터이고, 인터넷에 연결 돼 있다. 그리고 request를 항상 listening 하고 있다. (서버와 상호작용하는 모든 일들을 서버는 listen 하고 있다.)
   - 서버가 사람들이 무언가를 요청할 때까지 기다리게 해야한다. => `app.listen()`
   - 서버에게 어떤 port를 listening 할 지 얘기해줘야 한다.
     - port는 컴퓨터의 문이나 창문 같은 것
     - 몇몇 port는 인터넷에 오픈 되어 있다.
   ```js
   app.listen(4000, handleListening);
   ```

### 서버 들어가는 법

- 보통, localhost를 통해서 접속한다.

### 서버 종료하는 법

- nodemon과 서버를 종료하려면 `Ctrl`+`C` 를 누르면 된다.

## #3.1 GET Requests

- 처음 서버를 만들어서 접속하면 `Cannot GET /` 이 보인다.
- `/` 는 서버의 root, 혹은 첫 페이지를 뜻한다.
- `GET` 은 HTTP Method 이다.
- http는 우리가 서버와 소통하는 방법
  - 많은 방법 중 하나지만, 가장 안정적이고, 오래되고, 처음 사용한 방법
- 우리가 서버에 접속하면 브라우저가 대신 http request를 만들어준다.
- http request는 웹사이트에 접속하고 서버에 정보를 보내는 방법이다.
- 브라우저는 자동으로 페이지를 GET 하려 한다.
- 웹사이트에 접속하려 할 때, 내가 직접 접속하는 게 아닌 웹사이트한테, "이봐, 나한테 너네 홈페이지 갖다 줘"라고 얘기하는 것이다.

## #3.2 GET Requests part Two

### request

- 유저가 뭔가를 요청하거나, 보내거나, 네게 무슨 행동을 하는 것

### app.get()

- 누군가가 어떤 루트로 get request를 보낸다면, 반응한다.

```js
app.get("/", 콜백함수);
```

## #3.3 Responses

- app.get에는 두 가지 중요한 argument가 있다.

1. request(req) object => 쿠키나 url 등을 불러 온다.
2. response(res) object
   - `res.end()` => response를 끝낸다
   - 'res.send()' => html 요소 추가

## #3.4 Recap

> express 공식 레퍼런스를 참고해서 공부해라!

## #3.5 Middlewares part One

### Middleware

- request와 response 사이에 있다.
- 모든 middleware는 handler이다.
- 원래 controller에는 두 개의 argument 말고도 하나가 더 있다. (`next`)

### next argument

- next는 다음 함수를 호출해준다.
- next를 쓰기 위해서는 middleware가 필요하다.

```js
app.get("/", gossipMiddleware, handleHome);
```

- 모든 controller가 middleware가 될 수 있다.
- middleware는 작업을 다음 함수에 넘기는 함수다. 응답하는 함수가 아니다.

## #3.6 Middlewares part Two

### app.use()

- global middleware를 만들 수 있게 해준다.
- 모든 route에서 이 함수를 사용한다.
- 단, 순서가 중요한데 절대 app.get()뒤에 이 함수를 쓰지 않는다. (적용X)

## #3.11 External Middlewares

### Morgan

- morgan은 node.js용 request logger middleware다.
- morgan 함수를 호출하면, 자기가 설정한 대로 middleware를 return 해준다.
- `dev`: method, url, status code, 응답시간
- `combined`: 시간, method, http 버전, 사용중인 브라우저, os 등
- `common`, `tiny`

# #4 ROUTERS

## #4.0 What are Routers?

### Router

- 라우터는 우리의 컨트롤러와 URL의 관리를 쉽게 해준다.
- 쉽게 말해, 미니 어플리케이션을 만들게 해주는 것과 같다.
- 라우터를 이해하는 가장 쉬운 방법 => 맞으면서 배워라!
- 프로젝트에 대해 생각해 볼 때 가장 먼저 생각해야하는건 데이터다.
  - 어떤 종류의 데이터를 쓸 것인가? (`video`, `user`)
- 이후 URL을 디자인한다.

```
** USER **
/ => home
/join => Join
/login => Login
/search => Search

** Video **
watch-video
edit-video
delete-video
```

- URL은 뭔가를 수정하거나 프로필을 삭제하는 등 하는 행동들을 나타낸다.
- 가장 좋은 방법은 라우터를 도메인 별로 나눈다.
  - ex) 유저의 URL을 가져와서 라우터 안에 넣는다.
  - ex) 동영상의 URL을 가져와서 라우터 안에 넣는다.

```
`/` `/join` `/login` `/search` => 글로벌 라우터
`/users/edit` `/users/delete` => 유저 라우터
`/videos/watch` `/videos/watch` `/videos/delete` => 비디오 라우터
```

- 라우터는 우리가 작업중인 주제를 기반으로 URL을 그룹화해준다.

## #4.1 Making Our Routers

### 규칙 외 예외사항

- URL을 깔끔하게 하고, 마케팅 하는 사람이 편하려고 예외적으로 규칙을 적용하지 않는게 있다.
  - ex) `/users/join (x)` `/join (o)`

### 라우터 만드는 법

`const router = express.Router();`

### 라우터 사용법

`app.use(루트url, 라우터)`

### 라우터 request 연결

`라우터.get(url, 콜백함수)`

## #4.2 Cleaning the code

- 사람들은 처음에 코드를 작성할 때 머릿 속의 코드들을 얼른 쓰고 싶어한다. (창작 과정)
- 그리고, 그 다음에 코드를 작성하는데 쓴 시간만큼의 시간을 또 할애해야한다. 그만큼의 시간을 코들르 정리하는 데 써야한다. (코드 정리 과정)

### 정리법

- 먼저, 컨트롤러와 라우터를 나눈다.
  - routers 폴더를 만들어서 파일을 쪼갠다.
    - 우리가 만들고 있는 파일들은 하나의 모듈이고, 그것들은 독립되어 있다.
    - 그러니, 한 파일 안에서도 돌아가는 환경을 코드로 만들어야한다.
    - 항상, import 하기 전에는 export를 해야한다. 그렇지 않으면 에러가 생긴다.

### default export

- `export default 라우터명`
- default export는 한번만 정의할 수 있다.
- 그래서, 이름을 같게 유지할 필요가 없다.

## #4.3 Exports

- 라우터와 컨트롤러를 섞어서 쓰는건 좋지 않다.
- 컨트롤러를 위한 폴더를 따로 만들자.
- 그러면 왜 글로벌 컨트롤러는 없을까?

  - 필요가 없기 떄문이다. 회원가입은 유저가 하는 것이고 따라서 유저 컨트롤러에 들어가면 된다.
  - 홈으로 가면 뭐가 보이지? 동영상이다. 이건 비디오 컨트롤러에 들어가면 된다.

- 글로벌 라우터는 단지 url을 깔끔하게 하기 위해 쓴다.

### export

- export default는 단 한 개의 변수만 export 할 수 있다.
- 그래서, 변수를 생성할 때 앞에 export를 붙여주는 방식을 사용하면 여러 개를 export 할 수 있다.
- 단, export const를 하면 이름을 못 바꾸고 실제 이름 그대로 써야 한다. (export를 여러 개 했기 때문!)
- import 할 때는 `{ }` 를 사용한다.

## #4.7 URL Paramaters part One

### 파라미터 (parameter)

- url 안에 변수를 포함시킬 수 있다.
- 단, 주의할 점은 파라미터가 없는 url을 코드 순서 상 제일 위에 두어야 한다.
- 그렇지 않으면 파라미터가 없는 url이 파라미터 변수로 들어갈 수도 있다.

## #4.8 URL Parameters part Two

- 이 문제를 해결하기 위해서 `정규식`에 대해서 알아야 한다.
- `\w+`: 모든 문자, 숫자 선택
- `\d+`: 모든 숫자

```js
videoRouter.get("/:id(\\d+)".see);
```

- 이렇게 작성하면 숫자만 받는다고 express에 알려줄 수 있다.

> Routing: https://expressjs.com/ko/guide/routing.html

> 정규 표현식 테스트 사이트: https://www.regexpal.com

# #5 TEMPLATES

## #5.0 Returning HTML

- 기존의 res.send()는 한번 HTML를 수정하면 다른 것도 다 바꿔야해서 불편함이 컸다.
- 그래서 매번 복붙하지 않도록 해주는 녀석이 필요한데, 그것이 바로 `pug`다.

## #5.1 Configuring Pug

### Pug

- Pug는 템플릿 엔진(Template Engine)이다.
- 템플릿을 이용해서 뷰를 만드는걸 돕는다.
- HTML을 간략히 쓰기만 하면 알아서 Pug가 변환해준다.
  - title 태그를 닫거나, head 태그를 닫는 대신에 우리는 그냥 title이 head 안에 있다고 하면 됨

```
head
  title = pageTitle
  script(type="text/javascript")
    if (foo) bar (1 + 5)
```

### Pug 사용법

- npm으로 pug를 설치한 후 Express에게 html 헬퍼로 pug를 쓰겠다고 말한다.
- express의 app에서 중요한 것은 뷰 엔진(View Engine)을 설정할 수 있다는 것이다.
- express에게 우리가 사용할 뷰 엔진은 pug라고 말해주어야한다.

### 뷰 엔진 설정법

```
app.set("view engine", "pug")
```

- 기본적으로 Express는 views 폴더 안에 있는 파일을 찾는다.
- views는 어플리케이션의 뷰에 대한 디렉토리나 배열을 담고있다.
- express는 여기에서 view를 찾을 것이다.
- 그리고 이 context 안에서는 뷰나 템플릿이나 HTML이나 같다.
- 뷰는 유저가 보는 대상을 말한다.

### express가 뷰를 찾는 방법

`process.cwd() + '/views'` => 현재 작업 디렉토리에서 /views라는 디렉토리 찾는다.

- views 폴더를 만들고 pug 파일을 생성한다.

## #5.2 Patrials

- cwd를 바꾸려면 디폴트값을 바꿔야한다.

```js
app.set("views", process.cwd() + "/src/views");
```

- pug 파일명을 지을 때 주의할 점은 띄워쓰기, 대문자를 쓰지마라.

### Patrial

- pug의 최고 장점은 똑같은 요소들을 수정할 때 반복할 필요가 없다.
- patrials 폴더를 만들고, pug 파일을 생성한다.
  > 피그 공식문서 includes 참고

### include

- include는 다른 파일을 포함시킬 수 있다.
- `include <파일명>`

### Pug의 장점

1. 깔끔하게 HTML 작성 가능
2. html에 자바스크립트를 포함시킬 수 있다.
3. 반복하지 않아도 되고, 한 파일로 모든 템플릿을 업데이트 할 수 있다.

### Pug 작성법

- 일단 소문자로 작성하고, 속성이 있으면 괄호 안에 작성한다.
- 그리고 모든건 부모 속성보다 안 쪽에 있어야 한다. (2칸을 띄우거나, 탭으로)

### Pug 이용법

- Pug가 파일을 렌더링해서 평범한 html로 변환한다.
- `res.render(뷰명)`
- express가 views 디렉토리에서 pug 파일을 찾도록 설정되어 있어서 따로 import해 줄 필요는 없다.
- express는 아까도 말했듯이 `현재 작업 디렉토리`에서 /views라는 디렉토리를 찾는다.
  - cwd(현재 작업 디렉토리): 서버는 기동하는 파일의 위치에 따라 결정된다.
  - 어디서 노드를 부르고 있는지에 따라 결정된다. (여기서는 `package.json`)

## #5.3 Extending Templates

- 불필요한 반복을 더 줄여주기 위해서 inheritance(상속) 개념을 알아야 한다.

### inheritance (상속)

- 상속은 레이아웃(HTML)의 베이스를 만들어준다.
- 모든 파일들이 그 베이스에서부터 확장해 나간다.
- `extends 파일명` => 파일 가져오기

### block (블록)

- 블록은 템플릿의 창문 같은 존재
- `block 블록명` => 블록 생성
- 다른 pug 파일들이 내용을 채워넣을 공간을 마련하는 것

## #5.4 Variables to Templates

### 템플릿으로 변수 보내기

- `res.render()`에 `{ }`를 이용해서 보내고 싶은 변수를 다 보낸다.

```
res.render("home", { pageTitle: "Home" });
```

## #5.6 MVP Styles

- CSS는 모든 HTML, Javascript 작업이 끝나면 진행해라!
- 대신, 못생긴 HTML을 조금이나마 개선해주는 멋진 파일이 있다.

### mvp.css middleware

- 우리 HTML 태그에 몇 가지 기본 스타일을 입혀준다.
