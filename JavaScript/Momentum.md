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
