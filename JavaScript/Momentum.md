![Momentum](https://nomadcoders.co/_next/image?url=https%3A%2F%2Fd1telmomo28umc.cloudfront.net%2Fmedia%2Fpublic%2Fthumbnails%2FjsThumb.jpg&w=3840&q=75)

> 위 문서는 [노마드코더 바닐라 JS로 크롬 앱 만들기](https://nomadcoders.co/kokoa-clone/lobby) 강의에서 중요하다고 생각하는 내용들을 요약한 것입니다.

# #1 INTRODUCTION

## #1.4 Why JS

### 자바스크립트의 역사

- 자바스크립트를 만든 이유: 사람들이 좀 더 인터렉티브한 웹페이즈를 원했기 때문
- 자바스크립트가 만들어지고 인터넷 붐이 일어난 후, 사람들은 새로운 것을 만들어 웹 생태계를 망치는 것보다 기존의 자바스크립트를 쓰자고 결정했다.
- 자바스크립트는 10일 만에 만들어진 프로그래밍 언어기 때문에 굉장히 불안정해서 덕지덕지 고치고 패치하기를 반복했다. (그래서 잘 만들어진 프로그래밍 아니다)
- 하지만, 자바스크립트가 프론트엔드로 쓸 수 있는 유일한 프로그래밍 언어라 나머진 쓸모가 없다.

### 자바스크립트의 장점

- 자바스크립트는 따로 설치할 필요 없이 모든 브라우저에 내장되어 있기 때문에 접근성이 좋다. → 물량면에서 유리

### 자바스크립트의 단점

- 백엔드랑 다르게 프론트엔드는 자바스크립트를 좋아하던 싫어하던 무조건 배워야한다. (Why? 자바스크립트가 유일하기 때문!)

## #1.5 Why JS II

- 자바스크립트를 배우고 좀 더 깊이 파고드려면 프레임워크로 넘어가면 된다.

### 프레임워크

- 프레임워크란 개발자가 하려는 일을 도와주는 도우미이다.

### 대표적인 프레임워크들

- 리액트 네이티브: 자바스크립트만으로 안드로이드와 IOS앱을 만들 수 있다.
- 일렉트론: 자바스크립트로 데스크탑 앱을 만들 수 있게 해준다.
- socket.io: 채팅, 실시간 기능 제공
- m15.js: 머신러닝 모델 생성 및 훈련

- 이 모든 것들을 자바스크립트 하나만 배우면 가능해짐!

# #2 WELCOME TO JAVASCRIPT

## #2.0 Your First JS Project

- 브라우저는 HTML을 열고, HTML은 CSS와 JS를 가져온다.
- 일반적으로, JS 파일은 맨 위에서 가져오지 않고 주로 끝에서 가져온다.
- 브라우저 개발자 도구의 콘솔은 항상 열어두는 것이 좋다. (Why? 문제 확인을 위해서!)

## #2.1 Basic Data Types

### 자바스크립트에서 중요한 두 가지 유형

1. 숫자

- integer(정수)
- float(실수)

2. 문자

- string(문자) - 문자는 큰따옴표("")로 묶어서 표기한다.

## #2.3 Variables

- variable을 만들기 위해서는 const와 let을 사용한다.
- let은 중간이 값을 바꿀 수 있고, const는 값이 바뀔 수 없다.
- 이 두 가지 코드들만 보고 사람의 의도를 알 수 있다. const를 보면 값이 나중에 절대 변할 일이 없겠구나! let을 보면 값이 나중에 바뀔 수도 있겠구나 등
- 대부분의 프로그래머들은 기본적으로 const를 사용하고 variable을 업데이트 하고 싶을 때 let을 사용한다.
- 과거에는 const나 let이 없었고 var 밖에 없었다. var의 가장 큰 문제점은 어디서나 값을 실수로 바꿀 수 있었고, 실수로 그 값을 바뀌는 것을 방지하기 위해 const와 let이 등장했다.

## #2.4 Booleans

- boolean = true or false

### null vs undefined

- null: 값은 있는데 "아무것도 아닌 것"
- undefined: variable은 존재하는 데 정의되지는 않음 (컴퓨터 메모리 안에는 존재하고 공간은 있는데, 값이 없다.)

## #2.5 Arrays

- 사람들은 예전부터 데이터를 어떻게하면 효율적으로 저장할 지 연구해옴.

### array(배열)

- 가장 기본적인 데이터 구조
- 배열이름.push(): 항목 하나를 array 안에 추가

## #2.6 Objects

- object를 생성할 때는 대괄호 대신 중괄호를 사용한다.
- object 안에서는 =를 사용하지 않는다. 대신 :를 사용한다.
- property는 콤마(,)로 구분한다.

```js
const player = {
  name: "nico",
  points: 10,
  fat: true,
};
```

- 속성을 추가하고 싶을 땐 그냥 `player.lastName = "potato"` 식으로 적으면 된다.

- player 오브젝트의 name 프로퍼티에 접근하려면 player.name을 써도 되고 player["name"]을 써도 된다.

## #2.7 Functions part One

- argument(인수)는 function(함수)를 실행하는 동안 어떤 정보를 function에게 보낼 수 있는 방법이다.

## #2.8 Functions part Two

- object 안에도 프러퍼티에 함수를 넣을 수 있다.

```js
sayhello: function() {
  ...
}
```

## #2.13 Conditionals

### prompt()

- prompt()는 사용자에게 창을 띄울 수 있게 한다.
- 입력값을 받을 때 까지 자바스크립트 코드의 실행을 멈추게 한다.
- 항상 string의 값으로 받는다.

### typeof

- value의 type을 볼 수 있다.

```js
console.log(typeof num);
```

### parseInt()

- 숫자로 된 string을 number로 변환한다.
  - 만약, string을 문자로 받았다면 NaN(Not a Number)을 출력

## #2.14 Conditionals part Two

### isNaN()

- NaN인지 아닌지 boolean으로 알려주는 함수

## #2.16 Recap

- ===: 같음을 확인하는 오퍼레이션
- !==: 다름을 확인하는 오퍼레이션

# #3 JAVASCRIPT ON THE BROWSER

## #3.0 The Document Object

### Document

- HTML을 가리키는 객체
- 브라우저가 HTML 정보가 아주 많이 들어있는 document라는 object를 전달해주는 것
- 자바스크립트에서 HTML을 읽어올 뿐만 아니라, HTML을 변경할 수도 있다.

## #3.1 HTML in Javascript

- 브라우저에서 제공하는 객체(object) 중 document라는 객체는 JS에서 HTML 파일을 불러올 수 있도록 도와준다.
- document라는 객체 안에 getElementById라는 함수가 있는데 이 함수의 기능은 해당 HTML의 고유 ID를 추적하여 해당 HTML 파일을 찾은 뒤에 JS가 해당 ID를 가진 HTML 파일을 보완 수정할 수 있게 해준다.

## #3.2 Searching For Elements

### document.getElementsByClassName()

- class로 HTML 코드를 추적해 가져온다.
- 같은 class name이 많은 경우 array로 표시한다.

### document.getElementsByTagName()

- tag로 HTML 코드를 추적해 가져온다.
- 마찬가지로 array로 반환해 써먹기 불편하다.

### document.querySelector

- element를 CSS 방식으로 검색한다.

```js
document.querySelector(".hello h1");
```

- 단 하나의 element를 return 해주므로 쓰기 용이하다.
- 그러나, querySelector은 같은 element를 모두 다 가져오는 것이 아닌 첫 번째 것만 가져온다.
  - 만약 같은 것들을 다 수정하려면 `querySelectAll()`를 써주면 된다. (array로 반환)
- 강의에서는 99.8% querySelector을 사용한다.

## #3.3 Events

### event

- 브라우저에서 행하는 동작들

### addEventListener(이벤트 종류, 함수이름)

- 말 그대로 event를 listen 하는 것
- 이때, 함수이름에는 괄호를 넣으면 안된다.
  - Why? 자바스크립트가 이벤트를 감지하고 실행해야 하기 때문

## #3.4 Events Part Two

- listen 하고 싶은 event를 찾는 가장 좋은 방법은, 구글에 찾고 싶은 element의 이름, 예를 들어 h1 html element mdn을 검색한다. 우리는 javascript의 element를 원하니, 링크에 `Web APIs`라는 문장이 포함된 페이지를 찾는다. 왜냐하면 이건 JS 관점의 HTML Heading Element란 의미이기 때문이다. 너무 복잡하면 element를 `console.dir()`로 출력해서 `on~` 이라고 적혀있는걸 사용하면됨.

### mouseenter 이벤트

- 마우스가 요소에 올라오면 감지

### mouseleave 이벤트

- 마우스가 요소에서 나가면 감지

## #3.5 More Events

### 이벤트를 사용하는 두 가지 방법

```js
title.onclick = handleTitleClick;
```

```js
title.addEventListener("click", handleTitleClick);
```

- 니꼬쌤 같은 경우는 후자를 더 선호 (Why? 코드 가독성도 더 좋고 removeEventListener을 할 수 있어서)

### window object

- resize event (화면 크기가 바뀔 때 발동)
- body, head, title 같은 태그는 특별해서 document로 바로 불러오기 가능

```js
document.body.style.backgroundColor;
```

- 나머지 element들은 querySelector로 불러와야 한다.

## #3.6 CSS in Javascript

- Step1. element를 찾아라
- Step2. event를 listen 해라
- Step3. 그 event에 반응해라

## #3.7 CSS in Javascript Part Two

- 자바스크립트에서 직접적으로 요소의 style을 건드리는건 보기에 좋지 않다.
- 그 대신 태그의 클래스나 아이디를 수정해서 스타일을 입힌다.

```js
h1.className = "active";
```

- 그러나 자바스크립트로 모든 class name을 변경하는건 비효율적이다.

## #3.8 CSS in Javascript Part Three

- className 대신 classList를 사용해라.
  - Why? className은 이전의 class들은 상관하지 않고 그냥 모든걸 교체해버린다.

### classList.contains()

- 우리가 명시한 class가 HTML element의 class에 포함되어 있는지 말해준다.

### classList.remove()

- 클래스를 삭제한다.

### classList.add()

- 클래스를 추가한다.

### classList.toggle()

- 앞서 설명했던 classList의 add와 remove, contains를 다 합쳤다.

# #4 LOGIN

## #4.1 Form Submission

- JS 뿐만 아니라 브라우저가 기본적으로 제공해주는 옵션들을 적극 활용해라!

```
form input에 required, maxlength 등
```

- input의 유효성 검사를 작동시키기 위해서는 form으로 씌워야 한다.
- 우리가 form 안에서 엔터를 누르고 input이 더 존재하지 않는다면 자동으로 submit 된다.

## #4.2 Events

- submit 이벤트: 엔터를 누르거나 버튼을 누를 때 감지한다.

### preventDefault()

- 어떤 event의 기본 행동이든지 발생되지 않도록 막는다.
- 어떤 event가 발생해서 함수를 실행시킬 때 함수의 첫 번째 argument로 발생한 일에 대해 개발자가 필요로 할 만한 정보들을 준다.
- argument 공간만 제공하면 JS가 알아서 방금 일어난 event에 대한 정보를 지닌 argument를 채워넣어준다.
- 보통 argument 이름은 event로 적는게 관행이다.

## #4.4 Getting Username

- 무언가 반복되면 항상 변수로 만들어라. 일반적으로 string만 포함된 변수는 대문자로 표기하고 string을 저장하고 싶을 때 사용한다.
  - loginForm이나 loginInput처럼 중요한 정보를 담은게 아니라면 대문자로 작성한다.
- 니꼬는 문자열을 합칠 때 +를 쓰는걸 좋아하지 않는다. 그 대신 ``를 이용한다. (백틱 기호)

```js
`Hello $(username}`;
```

## #4.5 Saving Username

### local storage API

- 우리가 브라우저에 뭔가를 저장할 수 있게 해준다.

### localStorage.setItem()

- key, value 값 생성

### localStorage.getItem()

- value 값 불러오기

### localStorage.removeItem()

- key 삭제

## #4.6 Loading Username

- 항상 똑같은 이름을 가진 것은 변수를 따로 지정해서 사용해라
  - Why? 일반적인 string은 오타가 나도 JS가 바로 지적해주지 않지만, 변수명은 오타가 나면 JS가 바로 지적해준다.
