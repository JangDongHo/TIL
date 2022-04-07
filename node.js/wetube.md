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

## #5.7 Conditionals

- 변수를 다른 텍스트와 섞어쓰는게 아니라면 그냥 `태그 = "변수명"` 으로 쓰면 된다.
- varibale을 text와 섞게 된다면 #{ }를 사용한다.

### conditionals

- Javascript에서 쓰던 if, else if랑 똑같다.
- if, else를 잘 쓰면 template 상에서 뭘 보여줄지 말지 결정할 수 있다.

## #5.8 Iteration

- Iteration은 기본적으로 elements의 list를 보여준다.

```
each 변수 in 배열
```

- `변수`: array 안의 각 item을 가리킴 (명칭 상관X)
- `배열`: 컨트롤러의 배열 이름과 동일 해야함
- 만약 Iteration 뒤에 else를 사용하면 pug가 자동으로 videos 안에 뭐가 있는지 없는지 체크한다.
  > 더 자세한 Iteration 예제는 Pug 공식 문서 참고

## #5.9 Mixins

- Iteration은 배열 뿐만 아니라 객체도 지원한다.

### mixin

- mixin은 partial이긴 한데 데이터를 받을 수 있는 partial을 말한다.
- 일반적인 partial: HTML의 한 조각을 나타내고, 데이터를 받지 못함.
- 만약 블록이 같은 형태를 지니지만 서로 다른 데이터를 가져야 한다면?
- 유튜브는 component를 여러 페이지에서 재사용하고 있다.
- 개발자로서 우리의 목표는 "복붙을 최소화 하는 것" | 대신 똑같은 구조를 재사용 하겠다는 것.

### mixin 생성

- 먼저, views 폴더에 mixins 폴더 생성
- mixin 할 pug 파일 생성 `mixin 함수(item명)`
- 그리고 mixin을 불러올 pug에는 `+video(item명)`을 쓴다.
- 마지막으로, mixin pug를 include 시킨다.

# #6 MONGODB AND MONGOOSE

## #6.0 Array Database part One

- 백엔드에 데이터 보내는 법을 알아야 한다.
- \# 기호는 attribute(href, class, id 등)에는 사용이 불가하다.
  - attribute에 변수를 넣을 땐 백틱을 써서 ${ 변수 }로 사용하자.

## #6.1 Array Database part Two

### ternary operator

- `#{ 조건문 ? True일 때 : False일 때 }
- `&rarr;` => 오른쪽 화살표

### absoulte와 relative url의 차이

- 만약 내가 href의 앞머리 부분에 /를 넣으면 내가 어디있든 상관없이 root 경로 + /edit 으로 간다.
- 만약 /를 지우면 그냥 relative url이 된다.

## #6.2 Edit Video part One

### 데이터 보내기

- `form(action = " ")`
  - action에 데이터를 어디로 보낼지 정할 수 있다. 그 값은 내 서버가 가져야 하는 url이다.
  - 근데 서버는 벌써 이 url을 가지고 있으니(이미 그 페이지에 있으니) action을 지우고 method를 바꾼다.
- `form(method="POST")`
  - method를 기존의 get에서 post로 변경

### <`get request vs post request`>

- 기본값으로 method는 GET이다.
- get 방식을 쓰는 form은 구글이나 네이버에서 뭔가 검색을 할 때 많이 쓴다.
- post 방식은 파일을 보내거나, database에 있는 값을 바꾸는 뭔가를 보낼 때 사용한다. (+로그인)
- 그리고, 해당 라우터에서 post 해주면 된다.

```js
videoRouter.post("/:id(\\d+)/edit");
```

## #6.3 Edit Video part Two

- `method`: form과 backend 사이의 정보 전송에 관한 방식
- `get method`: form에 있는 정보가 url에 들어가게 됨

```js
videoRouter.route("/:id(\\d+)/edit").get(getEdit).post(postEdit);
```

### res.redirect()

- 브라우저가 redirect(자동으로 이동)하도록 한다.

### express.urlencoded

- 우리의 express application은 form을 어떻게 다루는지 모른다.
- 우린 application에게 form을 처리하고 싶다고 말해야 한다.
- parameter Limit를 써서, 필요하다면 parameter 갯수에 제한을 줄 수도 있고 또는 limit를 써서 form의 사이즈에 제한을 줄 수 있다.
- extended: body에 있는 정보들을 보기 좋게 형식을 갖춰주는 일을 한다.
- 이걸 쓰기 전에 middleware부터 적용해야 한다. 이 미들웨어가 form을 이해하고, 자바스크립트로 변형해서 우리가 사용할 수 있게 해준다.

```js
app.use(express.urlencoded({ extended: true }));
```

### req.body

- form의 정보를 불러올 수 있다.

```js
const { title } = req.body;
```

## #6.6 More Practice part Two

### videos.push(newVideo)

## #6.7 Introduction to MongoDB

### MongoDB

- MongoDB가 섹시한 이유는 바로 document-based(문서 기반)이라는 점 이다.
  - 일반적으로, database는 document-based가 아님. 보통 sql-based이다. (행 기반)
- MongoDB에서 저장하는 것들은 JSON-like-document이다.
- 또한, document 내부를 검색할 수 있도록 해준다. (CRUD)

### MongoDB 설치

- MongoDB 사이트 => Docs => Server => Installation => Install MongoDB Community Edition

## #6.8 Connecting to Mongo

### Mongoose

- node.js와 mongoDB를 이어주는 다리가 되어준다.

### Mongoose 설치

- `npm i mongoose`

### Mongoose 사용법

1. `db.js` 파일 생성
2. 터미널에 `mongo` 입력 후 url 따오기
3.

```js
import mongoose from "mongoose";
mongoose.connect("URL");
```

4. 새로운 DB를 추가하려면 url 연결 후, `/` 뒤에 database 이름을 적어주면 된다.
5. `server.js`에 `db.js` 파일 경로 import 해주기

- 만약 콘솔창에 경고가 뜬다면 문장 잘 읽어보고 mongoose.connect에 속성 추가하기

### 에러 출력

```js
const db = mongoose.connection;
const handleOpen = () => console.log("Connected to DB");
const handleError = (error) => console.log("DB Error", error);
db.on("error", handleError);
db.once("open", handleOpen);
```

## #6.9 CRUD Introduction

### CRUD

- Create(생성)
- Read(읽기)
- Update(수정)
- Delete(삭제)

### model 생성

1. src/models 폴더 생성
2. Video.js 생성 => video model 만들기

- mongoose에게 우리 애플리케이션의 데이터들이 어떻게 생겼는지 알려줘야 한다.
- ex) 비디오에 제목이 있고, 세부설명이 있고 등등

## #6.10 Video Model

### Schema

- 모델의 형태를 정의해 줄 필요가 있다.

  ```js
  const videoSchema = new mongoose.Schema({
    title: String,
    createdAt: Date,
  });
  ```

- 이후 모델 생성

  ```js
  const movieModel = mongoose.model("video", VideoSchema);
  ```

- export 해주기

  ```js
  export default movieModel;
  ```

- server.js에 import 해주기

## #6.11 Our First Query

- 따지고 보면 import는 server에서 중요한 부품이 아님.
- 그래서 `src/init.js`를 만들어서 import 관리 + application 작동
- server.js는 express 된 것들과 server의 configuration에 관련된 것을 처리하기 위해 만들어졌다.
- database나 models 같은 것들을 import를 하기 위함이 아니다.
- 이렇게 폴더를 변경하면 nodemon이 제대로 작동하지 않는데, `package.json`을 수정해서 문제를 해결한다.

### db 연결

- mongoose documentation 참고
- Model.find()
  1. call back function 활용
  2. promise 활용
- callback이란 무언가가 발생하고 난 다음 호출되는 function을 말한다. javascript에서 기다림을 표현하는 하나의 방법이라 생각하면 편하다.
- database는 javascript 밖에 존재하기 때문에 예기치 못한 일이 발생할 수도 있다. (기다림 지속 등)

### callback function 활용

- configuration이랑 호출 할 function 필요

```js
Video.find({}, (error, videos) => {});
```

- {}: search terms => 이게 비어 있으면 모든 형식을 다 찾는다는 것
- 콜백 함수(error, docs)

## #6.12 Our First Query part Two

### 코드 실행 순서

1. page를 request
2. console.log 출력
3. render 과정 거친 후 logger 출력
4. db 출력

- 코드에 따라 실행되는 시간이 다를 수 있다.

## #6.13 Async Await

- callback의 장점은 에러들을 바로 볼 수 있다는 것
- 단점은 function 안에 function을 작성해야해서 코드가 더럽다.

### promise

- promise는 callback의 최신 버전

```js
export const home = async (req, res) => {
  const videos = await Video.find({});
};
```

- 코드가 순서대로 실행된다.

### callback과의 차이점

- 차이점은 await을 find 앞에 적으면 내가 callback을 필요로 하지 않는다는걸 알게 된다.
- 에러를 출력하기 위해선 try catch문을 사용
  - try{}를 먼저 시도한 후 안되면 catch{}를 실행

### await가 대단한 이유

- await가 database를 기다려주기 때문이다.
- 코드가 매우 직관적 => javascript가 어디서 어떻게 기다리는지 바로 알 수 있기 때문이다.
- 코드 규칙상 await는 asynchronous를 가진 function 안에서만 작동한다.

## #6.14 Returns and Renders

- 컨트롤러에 return을 쓸 필요는 없지만 쓰는 이유는 function이 render 작업 후에 종료되도록 하기 위해서다.
- return이 아니라 실행되는 function들에 집중해야한다.

## #6.15 Creating a Video part One

### document 생성

- document는 데이터를 가진 비디오라 생각하면 편하다.
- document를 database에 저장해야 한다.

```js
const video = new Video({
  title,
  description,
});
```

- 이 코드 안에 video model의 구성 요소들을 담아준다.

### map 함수

```js
hashtags.split(",").map((word) => `#${word}`);
```

=> `,`를 기준으로 split한 후 단어 앞에 `#`를 붙여준다.

## #6.16 Creating a video part Two

- mongoose가 데이터 타입의 유효성 검사를 도와주고 있어서 잘못된 데이터 형식을 넣으면 보호해준다.
  => 데이터 형태를 미리 정해뒀을 때 얻는 장점

### 데이터 db에 저장하기 (방식 두가지)

1. video.save();

- save가 되는 순간 우리는 기다려야한다. await 사용해야함!

2. video.create();

- video.save() 쓸 필요없이 만들어진 video 객체를 바로 db에 저장한다.
- 대신 잘못된 형식의 데이터 타입이 들어오면 콘솔 창에 오류가 뜨면서 에러가 날 수도 있으니 try, catch 사용

## #6.17 Exceptions and Validation

```js
catch(error) {
  console.log(error);
  return res.render("upload", {
    pageTitle: "Upload Video",
    errorMessage: error._message,
  })
}
```

- 그냥 error 메시지를 사용자에게 출력하기에는 너무 기니 error 메시지의 \_message를 이용하면 짧게 출력할 수 있다.
- 그리고 pug에서 코드를 수정하면 된다.
  ```js
  if errorMessage
    span=errorMessage
  ```

### 스키마 default값 설정

```js
createdAt: { type: Date, required: true, default: Date.now },
```

- default 값을 설정해주면 우리가 나중에 값을 지정하지 않아도 알아서 설정이 된다.
- 여기서 중요한 점은 함수 형식이라면 절대 ()를 붙여서는 안된다.

### exist()

- 영상이 실제로 있는지 없는지 체크한다. 있으면 true 없으면 false
- 인자는 id가 아닌, filter(조건)을 받는다.

- db에 저장하기 전에 뭔가를 하거나 체크를 보통 한다.

### Middleware

- object가 저장 되기 전에 무엇인가를 먼저 하고 나머질 처리할 수 있게 해준다.

## #6.18 More Schema

> 스키마가 가질 수 있는 옵션들은 Mongoose 공식 문서 참고

- 데이터에 대한 구체적인 설정은 정말 중요하다. 데이터 타입을 더 구체화 할 수록 Mongoose의 도움을 받을 수 있다.
- form과 database 모두 minlength(maxlength)를 해야하는 이유는 누군가 임의로 웹페이지의 글자 수 제한을 풀고 길게 입력할 수도 있기 때문이다. => 홈페이지를 보호하기 위함.

## #6.19 Video Detail

- 문제는 우리가 설정했던 정규표현식이 mongoDB가 만들어낸 id 포맷과는 맞지 않다.
  => 그래서 상세 페이지로 가면 에러 메시지가 뜬다.

### regular expression

- id는 24byte hexadecimal string(24바이트 16진수)
- regular expression은 개발자에게 매우 유용하기 때문에 더 공부해봐라.
- `[0-9a-f]{24}` => 0~9, a~f까지의 24자 string을 찾아낸다. (패턴)

### findById, findOne

- findOne은 내가 보내는 모든 condition을 적용시켜준다.
- findById은 id로 영상을 찾아낼 수 있는 기능을 지원해준다.

## #6.20 Edit Video part One

### exec()

- query를 실행(execute)하는 것
- 배열.join()

## #6.21 Edit Video part Two

- `word.startsWith("#") ? word1 ! word2`
- 만약 단어가 #로 시작한다면 word1을 return하고 아니라면 word2 리턴

## #6.22 Edit Video part Three

### findByIdAndUpdate(id, items)

- id의 데이터베이스를 찾고 구성 요소 업데이트
- video의 소문자 v는 데이터베이스에서 검색할 영상 object이고 대문자 Video는 Video의 모델이다.

## #6.23 Middlewares

- express에서 middleware라는건 request를 중간에서 가로채서 뭔가를 하고 이어서 진행하는 것
- mongoose에서도 똑같이 document에 무슨 일이 생기기 전이나 후에 middleware를 적용할 수 있다.
- 차이점은 흐름을 방해하지 않는다. 중간에 뭔가를 할 뿐 그 뒤로 흐름을 이어간다.
- middleware는 무조건 model이 생성되기 전에 만들어야 한다.

```js
videosSchema.pre("save", asyncfunction(){});
```

- 이 미들웨어의 함수에는 this라는 인자가 있는데, 우리가 저장하고자 하는 문서를 가리킨다.

## #6.24 Statics

### static

- 우리도 Video 모델의 함수들 처럼 직접 함수를 만들 수 있다.

```js
videoSchema.static("함수명", function (인자) {});
```

- 이제 내가 직접 만든 function이 `함수 이름`을 통해 접근이 가능해짐.

## #6.25 Delete Video

- findByIdAndDelete와 remove의 차이
  - 둘은 조금 다른데, 가능하면 delete를 써라!

## #6.26 Search part One

- Mongoose가 좋은 이유는 굉장히 훌륭한 쿼리 엔진을 갖고 있다는 것

```js
Video.find({}).sort({ created: "asc" });
```

=> createdAt(등록 시간) 기준으로 오름차순

### req.query

- req.query를 이용하면 url의 정보들을 따올 수 있다.

## #6.27 Search part Two

- keyword를 포함하고 있는 것은 검색하고 싶으면 regex라는 연산자(operator)를 써야한다.

```js
$regex: new RegExp(keyword, ";");
```

=> keyword를 포함하는 것을 찾는다.

```js
$regex: new RegExp(`^${keyword}`, "i");
```

=> keyword로 시작하는 것을 찾는다.

```js
$regex: new RegExp(`${keyword}$`, "i");
```

=> keyword로 끝나는 것을 찾는다.

# #7 USER AUTHENTICATION

## #7.1 Create Account part Two

### 터미널 사용법

1. `mongo` 입력
2. `show dbs` 입력
3. `use wetube`
4. `show collections`
5. db.users.find() / db.users.remove({})

- password는 저장하기 전에 따로 보안 처리를 해주어야 한다.

## #7.2 Creating Account part Three

### password hash (해시화)

- 해싱은 일방향 함수인데, 문자열이 필요하다.
- 입력을 하면 출력값이 나오는데, 출력값으로는 입력값을 알아낼 수 없다.
- 같은 입력값으로는 항상 같은 출력값이 나온다.
  - `deterministic function(결정적 함수)`

### bcrypt

- 아주 오래 전에 만들어진 password 해싱 모듈
  > 해커가 해싱된 password를 가지고 할 수 있는 공격 => rainbow table
- bcrypt는 이 rainbow table 공격을 막아준다.

```js
bcrypt.hash(password, saltRounds, function (err, hash) {});
```

- saltRounds: password를 더 예측하기 어렵게 만든다. 해싱을 몇 번 할지 정한다.

## #7.3 Form Validation

### $or operator

- 각 조건이 true일 때 실행되게 만들 수 있다.

```js
const usernameExists = await User.exists({ $or: [{ username }, { email }] });
```

## #7.4 Status Codes

- 계정 생성에 실패했는데도 브라우저 창에서 아이디와 비번을 저장할건지 물어볼 때가 있다.
- 그래서 그걸 막아주기 위해 status code(상태 코드)라는 걸 알 필요가 있다.

### 상태 코드 200: OK

- 구글 크롬에서 username과 password 정보를 가지고 요청한 다음 응답을 200을 받으면 크롬이 계정 생성이 성공적이었다고 판단
- 보통 res.render을 하면 응답으로 200을 보내주기 때문에 브라우저한테 render는 잘 됐는데 에러가 있었다고 알려줘야한다.

### 상태 코드 400: BAD Request

- 클라이언트에서 발생한 에러 때문에 요청을 처리하지 못할 때 쓴다.

### <상태코드 변경법>

- res와 render 사이에 status(400)만 추가하면 된다.
- 상태코드를 적절히 보내주는건 아주 중요하다. 그래야 브라우저한테 상황을 알려줄 수 있다.

## #7.6 Login Part Two

### <비밀번호 확인>

- `bcrypt.compare(유저pw, DB해쉬값);`

```js
async function checkUser(username, password) {
  const match = await bcrypt.compare(유저pw, DB해쉬값);
  if (match) {
  }
}
```

## #7.7 Sessions and Cookies part one

### 세션

- 세션은 백엔드와 브라우저 간에 어떤 활동을 했는지 기억하는 걸 말한다.
- 브라우저와 백엔드 사이의 memory, history 같은 것
- 작동하려면 백엔드와 브라우저가 서로에 대한 정보를 가지고 있어야 한다.
- 서버가 요청을 받고 처리를 끝내면 서버에서는 누가 요청을 보냈는지 잊어버리게 되고 브라우저도 잊이버리게 된다. => `stateless (무상태)`
- 유저가 뭔가 요청할 때마다 누가 요청하는지 알 수 있게 만들어줘야함.
- 그래서 유저가 로그인 할 때마다 유저에게 무언가(텍스트)를 줄꺼임 (유저를 구분할 수 있게 된다.)

### express-session

- express에서 session을 처리할 수 있게 만든 미들웨어
- router 앞에서 초기화 시켜준다.

```js
app.use(
  session({
    secret: "Hello!",
  })
);
```

- 이제 이 미들웨어가 사이트로 들어오는 모두를 기억하게 된다.
- 브라우저가 우리 서버에 요청을 보내고 서버에서는 session 미들웨어가 브라우저한테 텍스트를 보낸다.

### 쿠키

1. 브라우저가 서버에 접근
2. 서버가 브라우저에게 쿠키 제공
3. 브라우저가 서버에 다시 접근할 때 앞에서 받은 쿠키 함께 제공
4. 서버는 쿠키를 통해 브라우저를 구분

## #7.8 Sessions and Cookies part Two

- 서버를 재시작 할 때마다 세션이 사라진다.
- 나중에는 백엔드가 잊지 않도록 세션을 mongoDB와 연결해본다.
- 세션 id를 가지고 있으면 세션 Object에 정보를 추가할 수 있다.

### req.session.이름

- 세션에 `이름`이라는 정보를 불러온다.

- 브라우저한테 준 id를 요청에 담아 보내주고 있다.

### 정리

- 내가 브라우저에서 웹사이트를 방문할 때마다 이 세션 미들웨어가 있으면 express가 알아서 그 브라우저를 위한 세션 id를 만들고 브라우저한테 보내준다.
- 브라우저가 쿠키에 그 세션 id를 저장하고 express에서도 그 세션을 세션 DB에 저장한다.
- 세션 DB에 있는 id = 쿠키에 있는 id
- 그러면 브라우저한테 보내서 쿠키에 저장한 세션 id를 브라우저가 `localhost:4000`의 모든 url에 요청을 보낼 때마다 세션 id를 요청과 함께 보낸다.
- 그러면 백엔드에서 어떤 유저가, 어떤 브라우저에서 요청을 보냈는지 알 수 있다.

## #7.9 Logged In User

- 세션 DB가 유저가 누구인지는 알아도 그 정보를 pug 템플릿과 공유하지 못한다. (`req.session.loggedIn`)

## #7.10 Logged In User part Two

- pug template에서 대신 locals에는 접근할 수 있다.
- pug랑 express가 서로 locals를 공유할 수 있도록 설정되어 있다.

```js
res.locals.변수 = 변수값;
```

- 이 방식으로 templates와 data를 공유
- global(전역 변수)라서 모든 template에서 쓸 수 있다.
- 물론 middleware를 router에 적용을 했을 때에 한해서다.
  => locals object는 이미 모든 pug template에 import된 object다.
- locals Middleware가 session middleware 다음에 오기 때문에 가능하다.

## #7.11 Recap

- cookie는 단지 정보를 주고 받는 방법인거고, 자동적으로 처리돼서 좋다. cookie를 받고, 보내는 과정에서 사용자는 아무것도 안해도 되고 별개의 코드를 작성할 필요가 없다. (http 표준을 따르고 있기 때문)
- session ID는 cookie에 저장된다. 왜냐면 cookie는 session ID를 전송하는데 사용되기 때문이다.
- session ID가 cookie 안에 저장되고, 백엔드에도 저장된다는게 요점이다.
- 백엔드는 생성된 모든 session ID를 관리하는 곳이다.
- Session Store는 우리가 session을 저장하는 곳이다.
- 내가 매번 코드를 저장하면 서버가 재시작 되는데, 이때 session store는 사라진다. 왜냐하면 테스트를 위한 저장소기 떄문이다.
- 그래서 서버 재시작시 쿠키 값이 아예 바뀐다.
- Cookie: 어떠 브라우저를 위한 session ID인지 알 수 있다.

## #7.2 MongoStore

- session id는 쿠키에 저장되지만, 데이터 자체는 서버에 저장된다.
- 서버에 저장되는 default session storage는 Memory Store이고, 실제 사용하기 위해 있는 건 아니다.
- 그래서 우리는 session store를 사용해야한다. 세션을 database에 저장해야 한다.

### connect-mongo

- connect-mongo는 세션을 MongoDB에 저장한다.

```js
MongoStore.create({ mongoUrl: "url" });
```

- 우리의 Mongo database의 url을 가지고 있는 configuration object를 만들어야한다.

## #7.3 Uninitialized Sessions

- session을 DB에 모두 저장하는 방법은 좋지 못한 생각이다.
- 로그인한 사용자의 session만 저장하는게 좋다.

### save Uninitialized

- 세션을 수정할 때만 세션을 DB에 저장하고 쿠키를 넘겨준다.

## #7.14 Expiration and Secrets

- secret은 우리가 쿠키에 sign할 때 사용하는 string이다.
- 쿠키에 sing 하는 이유는 우리 backend가 쿠키를 줬다는걸 보여주기 위함이다.
- secret은 그래서 길게 작성되고 강력하고 무작위로 만들어야한다.
- 이 string을 가지고 쿠키를 sign하고 우리가 만든 것임을 증명할 수 있다.

### domain

- domain은 이 쿠키를 만든 backend가 누구인지 알려준다.
- domain은 쿠키가 어디서 왔는지, 어디로 가야하는지 알려준다.

### path

- path는 단순히 url이라 별거아님.

### Expires

- 만약 내가 만료날짜를 지정하지 않으면 이전 session cookie로 설정되고 사용자가 닫으면 session cookie는 끝나게 된다.

### Max-Age

- 말그대로 세션이 언제 만료되는지 알려준다. 기본값은 14일이고 원한다면 바꿀 수 있다.

### session secret 값, db url 값 숨기기

- 값을 숨기기 위해서 environment file(환경 변수)가 필요하다.
- `.env`라는 파일을 생성한 후 gitignore에 추가한다.
- `.env`에는 코드에 들어가면 안되는 값들을 추가한다.
- 관습적으로 env 파일에 추가하는 건 모두 대문자로 적는다.
- env 파일에 접근하려면 그냥 `process.env.변수명`을 써주면 된다.

## #7.15 Environment Variables

### dotenv

- 내 env 파일을 읽고 각각의 변수들을 `process.env` 안에 넣는다.
- `process.env`: node.js process의 환경
- dotenv는 최대한 빨리 env를 load 해야하기 때문에 가능한 한 가장 먼저 사용해야 한다.
- wetube에서는 init.js의 가장 위에 넣어야한다.
- require을 하려면 dotenv를 사용하고 싶은 모든 파일에 require를 추가 해줘야한다.
- 그래서 그 대신, require를 import하는 부분을 우리가 import 하는 방식으로 수정한다.

```js
import "dotenv/config";
```

## #7.16 Github Login part One

### 깃허브 로그인

- 모든 소셜미디어 로그인의 흐름은 같다.

1. 사용자의 이메일, 패스워드 등을 깃헙으로 보낸다.
2. 깃헙이 우리에게 정보를 공유하는 것을 승인한다.
3. 깃헙은 사용자를 우리 웹사이트로 돌려보낸다.

- 이때 사용자를 token과 함께 redirect 시킨다.
- 그 토큰으로 사용자의 정보를 받아온다.

- 더 나아가기 전에 Github Application에서 설정을 해줘야한다.
  - Developer Settings 클릭 -> OAuth Apps 클릭

```
https://github.com/login/oauth/authorize?client_id=
```

- 무언가 더 많은 정보를 받고싶다면 scope에 뭔가를 더 전송한다.
- scope에는 너가 사용자에 대해 어디까지 알 수 있는지 적으면 된다.
- URL에 있는 것들을 바꿈으로써 다양한 방법으로 사용자를 승인할 수 있다.

## #7.17 Github Login part Two

- scope는 유저에게서 얼마나 많이 정보를 읽어내고 어떤 정보를 가져올 것에 대한지다.
- 우리가 원하는건 `read:user`과 `user:email`이다.
  > 자세한건 내가 요청하고 싶은 것이 담긴 API 문서를 참고
- URL을 하나한 다 복사해서 쓰면 매우 비효율적
- href를 `users/github/start` 로 잡고 새로운 유저 라우터, 컨트롤러를 하나 만들어서 redirect시키는 방식을 쓰는게 더 좋다.

### UrlSearchParams

```js
const params = new URLSearchParams(config).toString();
```

=> config에서 설정한 속성들을 인코딩해서 url로 만들어준다.

## #7.18 Github Login part Three

- `finish` url로 redirect 시키기 전에 Github에서 받은 토큰을 Access 토큰으로 바꿔줘야한다.

```
POST https://github.com/login/oauth/access_token
```

- 필수 파라미터는 `client_id`, `client_secret`, `code`가 있다.
- fetch 함수를 써서 url에 POST 요청을 보내고, json 형식으로 출력하기 위해 `Accept: "application/json"`을 넣어준다.
- 근데 문제는 fetch는 브라우저 상에서만 사용이 가능하다. (node.js 지원 x)

## #7.19 Github Login part Four

### node-fetch

- fetch를 node.js에서도 사용 가능하게 해준다.
  > wetube에서는 node-fetch 버전 2.6.1을 사용하는걸 권장한다. 그러지 않으면 에러가 뜬다.

### JSON.stringfy(json);

- json 파일을 브라우저에 출력한다.

-code를 가지고 github 백엔드에 request를 보내니 access-token이 생긴다.

- 이제 access_token을 가지고 user의 정보를 얻을 수 있다.

```
GET https://api.github.com/user
```

- 윗 주소로 인증을 위한 access_token을 보내주어야 한다.

- 계정을 불러오는데 성공했다면, 또 다른 문제가 있는데 사용자의 email이 비공개일 수도 있기 때문에 그에 대비해서 또 다른 request를 만들어야 한다.

## #7.20 Github Login part Five

> Github API로 가면 우리가 무엇을 할 수 있는지 다 볼 수 있다.

## #7.21 Github Login part Six

### 로그인 규칙 만들기

- 만약 primary인 email을 받고 db에서 같은 email을 가진 user를 발견하면 그 user를 로그인 시켜준다.
- 유저 스키마에 `socialOnly`를 추가해서 user가 github로 로그인 했는지 여부를 확인하게 한다.
  - 로그인 페이지에서 유저가 email로 로그인 하려는데 password가 없을 때 유용할 수 있다.
- 소셜미디어로 회원가입 시 비밀번호가 없기 때문에 password에는 빈 문자열을 넣고 socialOnly를 true로 해준다.

## #7.22 Log Out

### req.session.destroy();

- 세션을 없앤다.

# #8 USER PROFILE

## #8.0 Edit Profile GET

### 문제점 두 가지

1. loggedInUser에 접근하려는데 로그인 되어 있지 않으면 생기는 에러
2. 로그인 돼 있지 않은 사람들은 edit 페이지에 올 수 없어야 한다.

- 그래서 몇몇 route를 보호하는 middleware가 필요하다.

- 첫 번째 문제는 middleware에서
  `res.locals.loggedInUser = req.session.user || {};` 를 해줌으로써 해결이 가능하다.
- 로그인 안 한 유저는 undefined가 뜨니 끝에 `|| {}`를 붙이면 된다.

## #8.1 Protector and Public Middlewares

- 두 번째 문제로 로그인 하지 않은 사람들이 우리가 보호하려는 페이지로 가는 걸 막는 것이다.
- 그래서, protectorMiddleware를 하나 만들어서 로그인 하지 않은 상태면 홈으로 리다이렉트 시킨다.
- 추가로, 로그인 돼 있지 않은 사람들만 접근할 수 있게 하는 middleware도 만들어야 한다.

## #8.2 Edit Profile POST part One

- 비디오의 소유자를 설정하려면 videoController에서 몇 가지를 수정해야 한다.
- 우리 웹사이트에 계정이 있고, 로그인 돼 있는 사람만 video를 업로드 할 수 있게 해야한다.

## #8.3 Edit Profile POST part Two

- DB에 있는 user 정보를 업데이트 한 후, session도 같이 업데이트 해주어야 한다.
- 그러기 위해서 findByIdAndUpdate를 사용할건데, 기본적으로 update 되기 전의 데이터를 return 한다.
- 만약 `new` 옵션을 true로 설정하면 업데이트 된 데이터를 받을 수 있다.

## #8.4 Change Password part One

- 깃허브를 통해 계정을 만든 경우에는 비밀번호 변경을 볼 수 없어야한다.

## #8.5 Change Password part Two

- 깃허브로 로그인 하지 않은 사람들을 위한 middleware를 만든다.
- 코드를 여러 번 반복한다면, middleware를 만들어라.
- session에서 현재 로그인 된 사용자를 확인하고, form에서 정보를 가져온다.
- 비밀번호 변경을 시킬 때 하나는 pre save middleware를 거치고 User.create를 사용한다.
- 그리고 user.save()를 해도 pre save middleware를 작동시킨다.
- 우리는 user.save()를 사용해서 pre save middleware를 작동시킬 것이다.
- session에서 정보를 받으면, 잊지 말고 업데이트도 해줘야한다.

## #8.6 File Uploads part One

### multer middleware

- multer은 우리가 파일을 업로드 할 수 있게 도와준다.
- multer에게 도움을 받고 싶으면 form을 multipart form으로 만들어야한다.

```
enctype = "multipart/form-data"
```

- 파일을 백엔드로 보내기 위해 필요한 encoding type(enctype)
- 이후 미들웨어를 만든다.

```js
export const uploadFiles = multer({});
```

- multer에는 configuration object가 있다.

### destination

- 파일을 어디에 보낼지 정한다. (저장)
- 사용자가 보낸 파일을 지정한 폴더에 저장하도록 설정된 middleware가 필요하다.
- 그리고 그 미들웨어를 route에 적용한다.

- middleware를 실행한 다음, postEdit을 실행한다.

```js
.post(uploadFiles.single("avatar"), postEdit);
```

- `single`: 하나의 파일만 업로드
- `avatar`: input name이 들어갈 자리

- input으로 avatar 파일을 받아서 그 파일을 uploads 폴더에 저장한 다음 그 파일 정보를 postEdit에 전달한다.
- 이렇게 하면 req.file이 추가된다.

## #8.7 File Uploads part Two

- 내가 파일을 보내지 않고 수정하면, req 안에 file은 undefined가 된다.

```js
avatarUrl: file ? file.path : avatarUrl;
```

- 그리고, uploads 폴더를 .gitignore에 추가한다.

- DB에는 절대 파일을 저장하지 않는다. 대신에 폴더에 파일을 저장하고 DB에는 파일의 경로만 저장한다. (매우 중요!!)
- avatarUrl의 경로를 그대로 저장하면 상대 경로가 되니, 앞에 `"/"`를 붙여서 절대 경로로 만들어준다.
- 이렇게 해도 안되는 이유는 Express한테 uploads 폴더가 새로 생겼다고 말을 해준 적이 없기 때문이다.

## #8.8 Static Files and Recap

- 브라우저가 서버에 있는 파일에 접근할 수 없으니까 우리가 브라우저한테 어디로 가야 하는지 얘기 해줘야한다.
- 우리가 브라우저한테 어떤 페이지와 폴더를 볼 수 있는지 알려줘야한다.

### Static files serving

- 폴더 전체를 브라우저에게 노출시킨다.
- 먼저, route를 만든다.

```js
app.use("/uploads", express.static(폴더명));
```

### 문제점

1. 우리가 파일을 서버에 저장하고 있다.
   - 뭔가를 업데이트 하면 새로운 서버를 만들어서 다시 시작하는데 그 전 서버에 저장돼 있던 파일들은 날라가버린다.
2. 서버가 두 개 필요할 때 uploads 폴더를 공유할건가? 이상하다.
3. 서버가 죽으면 파일이 날라간다.

=> 파일을 서버에 저장하지 말고 다른 곳에 저장하자.

## #8.9 Video Upload

### filesize

- multer option 중에는 `fileSize`라는 옵션이 있어서 최대 파일 용량을 지정할 수 있다. (bytes)

## #8.11 Video Owner

- 비디오 모델 owner의 type은 number, string, date가 아니고 objectId다.
- objectId는 `mongoose` 코드에서만 사용할 수 있다.

```
type: mongoose.Schema.Types.ObjectId`
```

- `reference`도 추가해 줄 필요가 있는데, 그 이유는 mongoose에게 owner에 id를 저장하겠다고 알려줘야 하기 때문이다.
- `ref: "user"`를 사용함으로써 이 objectID가 `model user`에서 온다고 알려준다.
- 이제 영상을 업로드 할 때 업로드하는 사용자의 `id`를 전송해야한다.

## #8.12 Video Owner part Two

### populate()

- populate는 video 모델의 owner 부분을 실제 User 데이터로 채워준다.
- populate를 하면 `mongoose`가 `video`를 찾고 그 안에서 `owner`도 찾아준다.

## #8.14 Bug fix

- model은 save 해 줄 때마다 비밀번호가 계속 hash 되는 버그가 있다.
- 그래서 비밀번호가 수정될 때만 새로 hash 하게 미들웨어를 수정해주어야 한다.

### isModified()

- property가 하나라도 수정되면 isModified가 `true`고, 그게 아니면 `false`가 뜬다.

# #9 WEBPACK

## #9.0 Introduction to webpack

- Javascript를 프론트엔드에 사용될 부분에 도달했다.
- 지금부터 우리가 작성한 코드들은 브라우저에서 작동할 코드들이다.

### Webpack

- 백엔드에선 `babel-node`가 있기에 무슨 코드를 쓰든 Node.js가 이해할 수 있게 된다.
- 이런건 프론트엔드 javascript에서도 해야한다.
- 우리는 섹시한 css 코드와 동시에 브라우저가 이해할 수 있는 코드를 넘겨줘야한다.
- 섹시한 js를 쓰고싶은데 브라우저가 이해를 못할 수도 있고, 크롬에선 잘 돌아가는데 다른 브라우저가 이해를 못 할 수도 있는데 `webpack`은 모든 브라우저에서 인식 가능한 javascript로 바꿔준다.
- webpack은 우리가 주는 모든 파일들을 받아서 다른 파일들로 처리, 변경 시켜준다. (최신 기술 -> 오래된 기본 js, css로 변형)

### Webpack을 배워야 하는 이유

- webpack은 어렵고 따분하지만, nico와 그의 동료들은 잘 쓰지 않고 webpack이 포함된 툴을 쓴다.
- 그러나, 무조건 배워야 하는 이유는 거의 업계 표준이고, 적어도 이게 어떻게 작동하는지 그 뒤에 무슨 일이 일어나는지는 이해해야 한다.

  > gulp는 webpack의 쉬운 대체제이나, webpack만큼 유용하지는 않다.

- 리액트, 리액트 네이티브 같은 대부분의 프레임워크엔 webpack이 내장돼있다.
- 이번 섹션의 목표는 webpack configuration 파일을 작성하는 것이다.
- webpack이 어렵게 느껴져도 괜찮다. 대부분의 사람들도 어려워 한다.

## #9.1 Webpack configuration part One

- webpack은 파일들을 모아서, 압축, 변형시켜서 최소화하고, 필요한 과정을 다 거친 다음 정리된 코드를 결과물로써 내 놓는다.
- 이것저것 터미널로 파일들을 설치할건데, 이것들은 다 front-end 코드에 필요한 것들이다.

```
npm i webpack webpack-cli -D
```

- webpack을 설정하기 위해서는 webpack.config.js 파일을 생성한다.
  - 참고로 이 파일은 굉장히 오래된 js 코드만 이해할 수 있다.
  - ex) import, export default를 지원하지 않는다.

### config 설정 시 주의할 점

#### 1. entry

- entry는 소스코드를 의미한다. 즉, 우리가 처리하고 싶은 파일을 의미한다.
- config에서는 `export default`가 안되므로 구식인 코드를 써야한다.

```js
module.exports = {
  entry: "",
};
```

- 모든 파일들에는 entry가 필요하고, output이 필요하다.

#### 2. output

- output에는 filename, path가 필요하다.
- path는 절대경로여야 한다.
- webpack CLI을 이용해서 콘솔에서 webpack을 불러낼 수 있다.
- script에는 아래와 같이 추가한다.

```
"assets": "webpack --config webpack.config.js"
```

## #9.2 Webpack Configuration part Two

### \_\_dirname

- dirname은 말 그대로 파일까지의 경로 전체를 말한다. (절대 경로)
- js가 기본적으로 제공하고 있는 상수다.

### .path.resolve()

- 몇 개가 됐든 내가 입력하는 파트들을 모아서 경로를 만들어준다.

```js
path.resolve(__dirname, "assets", "js"));
```

### rules

- 우리가 각각의 파일 종류에 따라 어떤 전환을 할 건지 결정하는 것
- 내가 어떤 파일을 가지고 있던지 loader를 찾으면 된다.
- webpack은 loader를 통해서 전환시킨다.
- 자바스크립트의 경우 `babel-loader`가 필요하다.
- 이제부터 우리는 프론트엔드랑 백엔드 양쪽에서 `babel-core`랑 `babel/preset-env`를 사용한다.

### 작동방식

1. javascript 코드를 `babel-loader` 라는 loader로 가공
2. webpack은 `node_modules`에서 `babel-loader`를 찾는다.
3. 몇 가지 옵션을 전달한다.

- `entry`, `output`, `rules`, `변형할 파일`까지는 모든 webpack 구조가 똑같으므로 이해하고 기억해야한다.
- 갭라을 마치기 전 까지는 webpack의 mode를 `development`(개발 중)으로 맞춘다. 그렇지 않으면 너의 js 코드가 한 줄로 압축돼서 나온다.
- 만약 완성된 결과물을 원한다면 mode를 `production`으로 바꾸면 된다.

## #9.3 Webpack configuration part Three

- Express한테 assets 안에 js 안에 main.js가 있다고 알려줘야 한다. (express.static 사용)

## #9.4 SCSS Loader

- scss를 css로 변형시키려면 세 가지 loader가 필요하다.

1. scss를 가져다가 일반 css로 변형시켜주는 `sass-loader`
2. 폰트 같은 걸 불러올 때 css에 굉장히 유용하게 쓰일 `css-loader`
   - import랑 url을 풀어서 해석해준다.
3. 변환한 css를 웹사이트에 적용시킬 `style-loader`
   - css를 DOM에 주입

- **중요한건 제일 마지막 loader부터 역순으로 시작해야한다. => webpack은 뒤에서부터 시작하기 때문**

## #9.5 MiniCssExtractPlugin

- 이제 style loader 대신 webpack plugin을 쓴다.
- 그 이유는 style loader는 js에서 css를 넣기 때문에 좋은 방법은 아니다.

### MiniCssExtractPlugin

- css를 추출해서 별도의 파일로 만들어준다.

- js는 js 폴더에, css는 css 폴더에 넣기 위해서 loader들의 `filename` 옵션을 잘 써먹자.
- 이후, pug에서 css파일을 연결한다.

- `client` 파일은 webpack에 의해서만 로딩하게 되고, 나머지 사용자랑 pug, 브라우저는 `assets` 파일들만 보게 된다.

## #9.6 Better Developer Experience

- 우리는 수동으로 변경사항이 있을 때 마다 assets 폴더를 삭제하고 `npm run assets`를 실행했다.
- 이걸 자동화 시키려면 `watch`라는 함수를 사용하면 된다.
- 나중에 Heroku와 서버 등으로 deploy할 때는 변경할테지만 지금은 그냥 `watch: true,`로 해두면 된다.
- 이제 두 가지 console을 함께 구동하는 데 익숙해져야한다.
  1. back-end
  2. client 파일들을 watch
- 반드시 두 개 다 실행시켜야지 오류가 나지 않는다.
- `clean: true`를 하면 output folder를 build 하기 전에 `clean` 해준다.
- front-end 자바스크립트가 변경된다고 해서 back-end가 다시 재시작하는걸 원하지 않는다.
- 이를 해결하려면 `nodemon`에게 몇 가지 파일이나 폴더를 무시하는 방법을 알려줘야 한다.
- 감사하게도 `nodemon.json`이라는 파일을 만들고 아래처럼 적으면 된다.

```
{
  "ignore: ["파일명"],
  "exec": "babel-node src/init.js"
}
```

- `webpack.config.js`파일과 `src/client 디렉토리`와 `assets 디렉토리`를 ignore한다.
- 마지막으로, `assets` 폴더를 .gitignore에 추가한다.

# #11 VIDEO PLAYER

## #11.0 Player Setup

- 비디어 플레이어를 이쁘게 꾸미려면 HTML을 만들고, CSS를 만들고, JS를 만들어야한다.
- 지금 우리의 webpack은 모든 pug 파일에 똑같은 js를 적용시키고 있으므로, 다른 js 파일을 만들어서, 그 다른 js 파일을 다른 페이지에 포함시킨다.
- 지금 우리의 webpack은 하나의 entry point만 가지고 있다.
- entry를 object로 만들어서 js 파일을 분리시켜라.
- 그런데, 하나의 똑같은 output 파일을 분리시켜라.
- 그런데, 하나의 똑같은 output 파일로 나오면 안되니, webpack이 제공하는 `[name]` 변수를 사용한다.

```
filename: "js/[name].js"
```

- 이렇게 하면 entry에 있는 이름을 가져간다.
- pug에 주석을 달려면 `//`나 `//-`를 쓰면된다.

## #11.1 Play Pause

- 비디오(자바스크립트)를 만들기 전에 html 마크업을 해줘야한다.
- 비디오 element와 오디오 element는 둘 다 html media element로부터 상속 받는다.

## #11.3 Volume

- 볼륨의 range바 움직임을 감지하려면 `change`나 `input` event를 사용하면 된다.
- `chagne`는 마우스를 손에서 떼야지 감지되고, `input`은 실시간으로 감지한다.

## #11.4 Duration and Current Time

### <타임바 구현하기>

#### loadedmetadata

- meta data가 로드 될 때 실행된다.
- metadata는 비디오를 제외한 모든 것을 말한다.

#### timeupdate

- 비디오의 시간이 변할 때 마다 발생하는 event

- JS에서 handleLoadedMetadata() 이벤트를 추가하기 전에 video가 전부 로딩이 되어서, 시간이 불러와지지 않을 수도 있다. 해결법은 videoPlayer.js 끝 부분쪽에 하단의 코드를 넣는다.

```js
if (video.readyState == 4) {
  handleLoadedMetadata();
}
```

- video.readyState는 video가 충분히 불러와져서 사용이 가능하다는 뜻이다.

## #11.5 Time Formation

### date Constructor

- Javascript 안에 있는 date class
- 1970년 1월 1일 09:00가 JS의 제로타임(zero time)이다. 이걸 기준으로 밀리초를 추가할 수 있다.

```js
new Date(29 * 1000).toISOString().substr();
```

=> 29 \* 1000: 제로 타임에서 29000ms를 더한다.
=> toISOString(): 시간값을 보기 좋게 변환
=> substr(): 시작점에서 원하는 길이만큼 자른다. `ex) substr(11, 8)`

- 21년 12월 기준 subStr 함수는 JS에서 권장하는 함수가 아님. 대신에 substring 함수를 사용하면 된다.

```js
substring(시작 인덱스, 종료 인덱스);
```

## #11.7 Fullscreen

### element.requestFullscreen()

- 비디오를 전체화면으로 만들지만 문제는 버튼들은 같이 나오지 않는다.
- 그래서, videoContainer를 하나 만들어주고, 이 element를 풀스크린으로 만들어준다.

### document.fullscreenElement

- 이 property를 현재 풀스크린 모드로 보여지고 있는 element가 뭔지 알려준다.
- fullScreenElement가 null를 반환하면 풀스크린인 element가 없다는 뜻이다.

## #11.8 Controls Events part One

### mousemove

- 마우스가 비디오에 들어가고, 언제 비디오 안에서 움직이는지를 탐지한다.

### mouseleave

- javascript에서 기다리게 하려면, `setTimeOut`을 사용하면 된다. `mouseleave(함수, ms)`
- 만약 마우스가 다시 돌아오면 timeout을 취소시켜줘야한다.

### setTimeout()

- setTimeout을 실행시키면 특수한 id를 retrun 하는데, 우리는 clearTimeout()에 id를 건네주면 된다.

## #11.9 Controls Events part Two

- 영상 위에서 마우스 멈추는 걸 감지할건데 불행히도 `mousestop`이라는 이벤트는 없다.
- 그래서, timeout과 cleartimeout을 사용한다.

# #12 VIEWS API

## #12.0 Register View Controller

### API Views

- 영상을 시청할 때마다 백엔드에 요청을 보내고 영상 id에 해당되는 조회수를 증가시킨다.
- 그러기 위해선 템플릿을 렌더링하지 않는 API Views가 필요하다.
- 우리는 SSR(Server Side Rendering) 방식을 사용하고 있다.
  - 서버가 템플릿을 렌더링 하는 일까지 처리하는 것을 뜻한다. 요즘 시대에는 이렇게 하지 않는다.
- API는 프론트엔드와 백엔드가 서버를 통해 통신하는 방법을 말한다.
- 이동 없이 URL을 호출할 수 있게 하는 것은 Interactive 하게 만드는 가장 기본적인 방법이다.
  - Interactivity라 함은 URL이 바뀌지 않아도 페이지에서 변화가 생기는걸 말한다.

## #12.1 Register View Event

- 우리가 추가하려는 이벤트는 유저가 비디오 시청을 끝냈을 때 생기는 이벤트다.

### ended

- 미디어가 끝까지 재생 완료된 시점에 발생

### fetch(url)

- api에게 요청을 보낼 수 있다.

- 프론트엔드 js에서는 비디오의 id를 알지는 못하기 때문에 템플릿을 렌더링하는 pug한테 비디오의 정보를 남기라고 말해줘야한다.
- pug한테 video id를 data attribute에 저장하라고한다.

### data attribute

- `data-`로 시작하는 attribute
- dataset을 이용하면 자바스크립트로 데이터에 쉽게 접근할 수 있다.

## #12.2 Conclusions

- 그냥 `res.status()`를 하면 응답에 상태 코드를 추가하기만 할 뿐 아무 일도 일어나지 않는다.
- 그래서, 대신에 `sendStatus()`를 사용해야한다.
- 상태 코드를 꼭 쓸 필요는 없지만 쓰는 이유는 어떤 기능이 잘 처리됐는지 상태 코드가 알려주기 때문이다.

# #13 VIDEO RECORDER

## #13.0 Recorder Setup

### navigator.mediaDevices.getUserMedia()

- 사용자의 navigator에서 카메라와 오디오를 가져다준다.
- 작업하는데 시간이 걸리기 때문에 await를 사용한다.
- 이 함수는 `constraints`라는 객체를 argument를 받는다.

```
{ audio: true, video: true }
```

- 프론트엔드 상에서 async랑 await를 사용하려면 `regenerator Runtime`을 설치해야 한다.

## #13.1 Video Preview

```
video.srcObject = stream;
video.play()
```

- srcObject에 stream을 추가하고 video를 재생한다.
- srcObject는 video가 가질 수 있는 무언가를 의미한다.

## #13.2 Recording Video

### MediaRecorder

- 녹화(녹음)를 할 수 있게 도와준다.
- `recorder.stop();`을 호출하게 되면 `dataavailable` 이벤트가 실행된다.

## #13.3 Recording Video Part Two

### URL.createObjectURL()

- 이 createObjectURL은 브라우저 메모리에서만 가능한 URL을 만들어준다.
- 웹사이트 상에 존재하는 URL처럼 보이지만 실제로는 없다.
- 단순히 브라우저의 메모리를 가리키고 있는 URL일 뿐
- 그냥 파일을 가리키고 있는 URL이라고 생각해라.

## #13.4 Downloading the File

- 동영상 다운로드를 하려면 사용자가 직접 우클릭해서 비디오 저장을 누르게 하는 것을 대신해서 가짜 클릭을 만들어서 해본다. (링크를 걸긴 하는데 가짜 링크를 걸어준다는 것)

### a.download

- 사용자로 하여금 URL을 통해 어디로 보내주는 게 아니라 URL을 저장하게 해준다.
