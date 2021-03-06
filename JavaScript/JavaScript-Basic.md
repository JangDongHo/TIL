# 4. 자바스크립트 기초

## 13-1 자바스크립트로 무엇을 할까

### 웹의 요소를 제어합니다

- 자바스크립트를 추가하면 웹 문서의 각 요소를 가져와서 필요에 따라 스타일을 변경하거나 움직이게 할 수 있다.
- 자바스크립트는 HTML이나 CSS와 함께 사용해서 웹의 요소를 움직이거나 포토 갤러리를 펼쳐 놓는 것처럼 웹 사이트 UI 부분에 많이 활용한다.

### 웹 애플리케이션을 만듭니다

- 과거 웹은 단순히 정보를 나열하고 검색했다면, 최근 웹은 사용자와 실시간으로 정보를 주고 받으며 마치 애플리케이션처럼 동작한다.
- ex) 온라인 지도의 길 찾기 서비스, 코로나19 감염자 수 차트

### 다양한 라이브러리를 사용할 수 있습니다

- 웹 플랫폼을 중심으로 하는 서비스가 점점 늘어나면서 그만큼 웹 브라우저를 통한 상호 작용이 더욱 중요해지고 있다.
- 과거에는 서버에서 했던 일을 이제는 클라이언트에서도 할 수 있게 됐다. 클라이언트에서 처리해야 할 기능이 많아지면서 자바스크립트 기능은 더욱 강력해지고 있다.
- 웹 애플리케이션을 개발할 때 사용하는 리액트(React), 앵귤러(Angular), 뷰(Vue.js)같은 프레임워크도 있고, 그래픽 활용을 위한 D3.js나 DOM을 쉽게 조작할 수 있게 해주는 제이쿼리(jQuery) 같은 라이브러리도 있다.

### 서버 개발을 할 수 있습니다

- Node.js는 그동안 프런트엔드 개발에서 사용하던 자바스크립트를 백엔드 개발에서 사용할 수 있도록 만든 프레임워크이다.
- 흔히 백엔드 개발 언어라고 하면 PHP, 자바, 닷넷을 생각하지만 이제는 자바스크립트만 알아도 서버 개발까지 영역을 확대할 수 있다.

## 13-2 웹 브라우저가 자바스크립트를 만났을 때

### 웹 문서 안에 \<script> 태그로 자바스크립트 작성하기

- 자바스크립트 소스는 \<script>와 \</script> 태그 사이에 작성한다.
- 자바스크립트는 웹 문서에서 이미지나 텍스트 등의 요소를 제어하는 경우가 많으므로 되도록이면 이미지나 텍스트 등을 다 표시한 후에 실행하는 것이 좋다. 그래서 \</body> 태그 직전에 자바스크립트 소스를 삽입한다.
- HTML, CSS와는 달리 자바스크립트에서는 영어 대소 문자를 구별하므로 주의해야 한다.
- 그러나 이렇게 작성하면 문서가 복잡해지므로, 자바스크립트 소스를 작성할 때 외부 스크립트 파일로 저장해서 웹 문서와 연결하는 방법을 많이 사용한다.

### 외부 스크립트 파일로 연결해서 자바스크립트 작성하기

- 외부 자바스크립트 파일을 \<script> 태그 없이 자바스크립트 소스만 작성하고 확장자는 \*.js 파일로 저장한다.
  > 이렇게 자바스크립트 소스를 따로 작성하여 HTML 문서에 연결하는 것을 '외부 스크립트 파일을 연결한다'고 말한다.

```html
<script src="외부 스크립트 파일 경로"></script>
```

```html
<body>
  <h1 id="heading">자바스크립트</h1>
  <p id="text">위 텍스트를 클릭해 보세요</p>

  <script src="js/change-color.js"></script>
</body>
```

### 웹 브라우저에서 스크립트를 해석하는 과정

```html
1<!DOCTYPE html> 2
<html lang="ko">
  3<head>
    4
    <meta charset="UTF-8" />
    5
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    6
    <title>자바스크립트</title>
    7
    <style>
      8 body {
        text-align: center;
      }
      ...(생략) 14;
    </style>
    15
  </head>
  16
  <body>
    17
    <h1>간단한 입출력 방법</h1>

    20
    <script>
      21   console.log("안녕하세요?");
      22
    </script>
    23
  </body>
  24
</html>
```

1. 웹 브라우저는 1행에 있는 \<!DOCTYPE html>를 보고 이 문서가 웹 문서라는 것을 알게 된다. 그리고 \<html>과 \</html> 태그 사이의 내용을 HTML 표준에 맞춰 읽기 시작한다.
2. 웹 문서에서 HTML 태그의 순서와 포함 관계를 확인한다. \<head>와 \</head> 태그, \<body>와 \</body> 태그 사이에 각각 어떤 태그가 있는지 확인한다. 그리고 태그 간의 관계는 어떻게 되어 있는지 등을 분석한다.
3. 태그 분석이 끝나면 7~14행의 스타일 정보를 분석한다.
4. 20행에 있는 \<script> 태그를 만나면 웹 브라우저 안에 포함된 자바스크립트 해석기에게 스크립트 소스를 넘긴다. 자바스크립트 해석기는 \<script>와 \</script> 사이의 소스를 해석한다.
5. 2에서 분석한 HTML과 3에서 분석한 CSS 정보에 따라 웹 브라우저 화면에 표시한다.
6. 이제 웹 브라우저에서 자바스크립트 텍스트를 클릭하면 분석해 놓은 자바스크립트를 실행해서 그 결과를 화면에 표시한다.

## 13-3 자바스크립트 용어와 기본 입출력 방법

### 식과 문

- 자바스크립트의 언어의 큰 줄기는 **식(expression)** 과 **문(statement)** 이다.
- 자바스크립트에서 식은 **표현식** 이라고도 하는데, 연산식뿐만 아니라 실제 값도, 함수를 실행하는 것도 식이 된다.
- 즉, 어떤 값을 만들어낼 수 있다면 모두 식이 될 수 있으며, 식은 변수에 저장된다.

```
inch * 2.54 // 연산식은 식입니다.
"안녕하세요?" // 문자열도 식입니다.
5 // 숫자도 식입니다.
```

- 이에 비해 문은 명령이라고 생각할 수 있다. 문의 끝에는 세미콜론(;)을 붙여서 구분한다. 앞으로 배울 '조건문'이나 '제어문'등을 예로 들 수 있다.

### 간단한 입출력 방법

- 소스를 입력하다 보면 사용자에게 입력받아야 하거나 자바스크립트 실행 결과를 웹 브라우저에 표시해야 할 때가 있다.

#### 알림 창 출력하기

- **알림 창(alert)** 은 가장 많이 사용하는 간단한 대화 상자이다.

```
alter(메시지)
```

> 웹 브라우저에서 간단한 알림 내용을 표시하거나 사용자에게 어떤 값을 입력하게 하는 창을 '대화상자(dialogue box)'라고 한다.

```
alter("안녕하세요?")
```

#### 확인 창 출력하기

- **확인 창(confirm)** 은 사용자가 [확인]이나 [취소] 버튼 중에서 직접 클릭할 수 있다. 그러면 선택한 결과에 맞게 프로그램이 동작한다.

```
confirm(메시지)
```

```javascript
var reply = confirm("정말 배경 이미지를 바꾸겠습니까?");
```

#### 프롬프트 창에서 입력받기

- **프롬프트 창(prompt)** 은 텍스트 필드가 있는 작은 창이다. 필드 안의 내용을 가져와 프로그램에서 사용할 수 있다.

```
prompt(메시지) 또는 prompt(메시지, 기본값)
```

프롬프트 창을 만들 때는 기본값을 지정하거나 지정하지 않을 수 있다. 기본값을 지정하지 않으면 빈 텍스트 필드로 표시된다.

```javascript
var name = prompt("이름을 입력하세요.", "아무개");
```

```javascript
var name = prompt("이름을 입력하세요.");
```

#### 웹 브라우저 화면에 출력을 담당하는 document.write() 문

- 단순히 브라우저 화면에서 결괏값을 확인하는 용도로는 document.write()를 많이 사용한다.
- document.write()를 완전히 이해하려면 document 객체를 알아야 한다. 하지만 아직 document 객체를 배우지 않았으므로 **웹 문서(document)에서 괄호 안의 내용을 표시(write)하는 명령문** 이라는 정도로만 알아둔다.
- document.write()의 괄호 안에는 실제 웹 브라우저 화면에 표시할 내용이나 어떤 결괏값이 저장된 변수를 넣을 수도 있다. 물론 따옴표 안에는 HTML 태그도 함께 사용할 수 있다.

```javascript
document.write("<h1>어서오세요</h1>");
```

- - 연산자를 사용해서 웹 브라우저 화면에 표시할 내용과 변수를 섞어서 나타낼 수도 있다.
- - 연산자는 더하기 기호가 아니라 **연결 연산자** 이다.

```javascript
var name = prompt("이름을 입력하세요.");
document.write("<b><big>" + name + "</big></b>님, 환영합니다.");
```

#### 콘솔 창에 출력하는 console.log() 문

- console.log() 문은 괄호 안의 내용을 콘솔 창에 표시한다.
- 콘솔 창은 웹 브라우저의 개발자 도구 창에 포함되어 있는 공간이다.
- 콘솔 창에서 소스 코드의 오류를 발견하거나 변숫값을 확인할 수도 있다.
- console.log() 문의 괄호 안에는 변수가 들어갈 수도 있고 따옴표 사이에 표시할 텍스트를 넣을 수도 있다. 이때 따옴표 안에 HTML 태그는 사용할 수 없다.

```javascript
<script>
  var name = prompt("이름을 입력하세요."); console.log(name + "님,
  환영합니다.");
</script>
```

## 자바스크립트 스타일 가이드

### 코딩 규칙이 왜 필요할까요?

- 자바스크립트 코딩 규칙은 **스타일 가이드** 나 **코딩 컨벤션**, **코딩 스타일**, **표준 스타일** 이라고도 한다.
- 자바스크립트는 웹 문서에서 동적인 효과를 주기 위해 출발한 언어이므로 다른 프로그래밍 언어에 비해 데이터 유형(type)이 유연해서 곳곳에 사용자가 주의를 기울이지 않으면 오류가 발생한다.
- 게다가 오픈소스에 기여하거나 누군가와 공유할 소스라면 코드를 더욱 깔끔하게 작성해야 한다.
- 이때 스타일 가이드를 따라서 작성하면 소스 코드의 오류도 줄이고 일관성이 생겨 읽기 쉬워진다.

### 자바스크립트 스타일 가이드

- 보통 [구글](google.github.io/styleguide/jsguide.html)이나 [에어비앤비](github.com/airbnb/javascript)에서 배포한 것을 기준으로 작성한다.
- 자바스크립트를 더 깊게 공부하고 싶다면 두 스타일 가이드를 참고해서 작성해라.

### 자바스크립트 소스를 작성할 때 지켜야 할 규칙

1. 코드를 보기 좋게 들여쓰기한다

   - HTML 태그와 CSS를 작성했던 것처럼 자바스크립트 소스를 작성할 때도 **들여쓰기**를 해야한다.
   - 들여쓰기를 해서 작성하면 소스 간의 포함 관계를 알아보기가 쉽다.

2. 세미콜론으로 문장을 구분한다

   - **세미콜론(;)** 은 문장의 끝을 나타내며 문장과 문장을 구분하는 역할을 한다.
   - 사실 안 붙여도 실행은 되지만, 스타일 가이드에서는 문장을 끝낼 때 반드시 세미콜론을 붙이도록 권장한다. 이렇게 문장을 명확히 표시해 주면 소스를 디버깅하기 쉽기 때문이다.
   - 소스는 한 줄에 한 문장만 작성하는 것이 좋다.

3. 공백을 넣어 읽기 쉽게 작성한다

   - 예약어나 연산자, 값 사이에는 공백을 넣어서 소스 코드를 읽기 쉽게 작성한다.
   - 공백이 없어도 실행은 되나, 개발자가 소스 코드를 읽거나 디버깅을 할 때는 공백이 있어야 가독성이 좋다.

4. 소스 코드를 잘 설명하는 주석을 작성한다

   - 프로그래밍의 주석은 소스 코드를 살펴보기 위해 꼭 필요한 요소이다.

   1. 한 줄 주석: 주석 기호로 슬래시 2개(//)를 붙이고 내용을 작성한다. // 바로 뒤에 작성한 내용만 주석으로 인식한다.
   2. 여러 줄 주석: 주석 내용이 여러 줄이면 여는 주석 기호(/\*)를 맨 앞에, 닫는 주속 기호(\*/)를 맨 뒤에 넣는다. 그리고 그 사이에 주석 내용을 작성한다.

5. 식별자는 정해진 규칙을 지켜 작성한다.

   - 식별자(identifier)는 개발자가 자바스크립트의 변수, 함수, 속성 등을 구별하라고 이름 붙인 특정 단어를 의미한다.
   - 식별자의 첫 글자는 반드시 영문자나 언더스코어(\_), 또는 달러 기호($)로 시작해야 한다.
   - 두 단어 이상이 모여 하나의 식별자를 만들 경우 단어 사이에 공백을 둘 수 없고, 단어와 단어 사이를 하이픈(-)이나 언더바(\_)로 연결해서 사용한다.
   - 하이픈이나 언더바 없이 두 단어를 붙여 사용할 경우 첫 번째 단어는 소문자로 시작하고 두 번째 단어는 대문자로 시작하는 것이 일반적이다.

   ```
   num1          // 영문자로 시작하는 식별자
   _doSomething  // 언더스코어(_)로 시작하는 식별자
   checkTime()   // 두 단어로 만든 식별자
   ```

6. 예약어는 식별자로 사용할 수 없다
   - 예약어(keyword)는 키워드라고도 하는데, 식별자로 사용할 수 없도록 자바스크립트에 미리 정해 놓은 단어를 의미한다.
   - 예를 들어 var는 변수를 선언할 때 쓰는 예약어이며 식별자 이름으로는 사용할 수 없다.

## 14 자바스크립트 기본 문법

### 14-1 변수 알아보기

#### 변수란

- **변수(variable)** 란 프로그램을 실행하는 동안 값이 여러 번 달라질 수 있는 데이터를 가리킨다.
- 반면에 값을 한번 지정하면 바뀌지 않는 데이터를 상수(constant)라고 한다.

```css
나이 = 올해 연도 - 태어난 연도 + 1
/* 나이, 올해 연도, 태어난 연도: '변수' / 1: 값이 항상 일정하므로 '상수' */
```

#### 변수 선언의 규칙

- 변수를 사용하려면 변수를 구별할 수 있도록 이름을 붙여 주어야 하는데, 이것을 변수 선언이라고 한다.
- 변수 선언은 값을 저장할 컴퓨터 메모리 공간에 문패를 붙이는 것과 같다.
- 바뀐 값을 다시 같은 변수에 저장할 수도 있다. 따라서 프로그램에서 사용할 변수 이름은 서로 다르게 만들어야 한다.

1. 변수 이름은 영어 문자와 언더스코어(\_), 숫자를 사용한다
   - 변수 이름의 첫 글자는 영어 대소 문자나 언더스코어(\_)만 쓸 수 있으며 숫자나 기호, 띄어쓰기는 허용하지 않는다.
2. 자바스크립트는 영어 대소 문자를 구별하며 예약어는 변수 이름으로 쓸 수 없다.
3. 여러 단어를 연결한 변수 이름은 중간에 대문자를 섞어 쓴다.
   - 주로 한 단어로 이루어진 변수 이름은 모두 소문자로 쓰고, 두 단어 이상인 변수 이름은 totalArea나 TotalArea, 또는 Total_Area처럼 중간에 대문자를 섞어 사용한다.
   - 이 규칙을 '낙타 표기법'이라고 한다.
4. 변수 이름은 의미 있게 작성해야 한다
   - 자바스크립트로 프로그래밍할 때는 변수를 수십 개 사용하므로 각 변수의 역할을 일일이 기억하기가 쉽지 않다.
   - 그래서 변수 이름만 보고도 대충 어떤 값인지 추측할 수 있도록 하는 것이 좋다.

### 변수 선언하기

- 자바스크립트에서 변수 선언은 다음과 같이 var라는 예약어 뒤에 변수 이름을 적으면 된다.

```
var 변수명
```

- 변수를 선언했으면 '=' 기호를 사용해서 변수에 값을 저장할 수 있다. 이것을 **값 할당** 이라고 한다.
- 값 할당은 변수를 선언한 후에 따로 할 수도 있고, 변수를 선언하면서 동시에 할 수도 있다.

## 14-2 자료형 이해하기

### 자료형이란

- 컴퓨터가 처리할 수 있는 자료의 형태를 **자료형** 이라고 한다.
- 자바스크립트의 자료형은 숫자, 문자열, 논리형과 같은 **기본 유형**과 배열, 객체를 다루는 **복합 유형** 그리고 undefined, null 같은 **특수 유형**이 있다.

| 종류      | 설명                                                                               | 예시                                                 |
| --------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------- |
| 숫자형    | 숫자로만 표기                                                                      | var birthYear = 2000;                                |
| 문자열    | 작은따옴표나 큰따옴표로 묶어서 표기(숫자를 묶으면 문자로 인식)                     | var greeting = "Hello!";<var>var birthYear = "2000"; |
| 논리형    | true OR false 로 표기                                                              | var isEmpty = true;                                  |
| 배열      | 하나의 변수에 여러 개의 값을 저장                                                  | var seasons = ["봄", "여름", "가을", "겨울"];        |
| 객체      | 함수와 속성을 함께 포함                                                            | var date = new Date();                               |
| undefined | 자료형이 지정되지 않았을 때의 상태. (ex. 변수 선언만 하고 값을 할당하지 않은 변수) |
| null      | 값이 유효하지 않을 때의 상태                                                       |

### 숫자형

- 자바스크립트에서 **숫자형**은 정수와 실수로 나누어 구분한다.

#### 정수

- 정수는 소수점 없는 숫자이다.
  > 정수는 표현 방법에 따라 10진수, 8진수, 16진수로 나눈다.<br>
  > 10진수: 0~9로 표현할 수 있는 수 (ex. 2000, 17)
  > 8진수: 0~7로 표현할 수 있는 수. 이때 10진수와 구분하기 위하여 숫자 0을 맨 앞에 붙인다. (ex. 012, 013, 02000)<br>
  > 16진수: 숫자 0~9와 알파벳 A~F로 표현할 수 있는 수. 16진수는 프로그래밍을 할 때 가장 많이 사용한다. 10진수와 구분하기 위해서 0x(또는 0X)를 맨 앞에 붙인다. 이때 알파벳 A~F는 대소문자 상관없다. (ex. 0xfff, 0XFFF, 0xFFF)

#### 실수

- 실수는 소수점이 있는 숫자이다.
- C나 자바 같은 프로그램이 언어에서는 정수와 실수를 명확히 구분하고 처리 방법도 다르지만, 자바스크립트에서는 정수와 실수를 함께 묶어 숫자형이라고 한다.
- 자바스크립트에서는 실수를 정밀하게 계산하는 것은 적합하지 않는다.

### 문자열

- **문자열(string)** 은 작은따옴표나 큰따옴표로 묶은 데이터를 의미한다.
- 그래서 숫자도 작은따옴표나 큰따옴표로 묶으면 문자열로 인식한다.
- 큰따옴표로 묶은 문자열 안에 또 다른 문자열을 넣으려면 작은따옴표를 사용하면 된다.

```js
document.write("<span style='color:blue'>, "Do it", "</span>")
```

### 논리형

- **논리형**은 불린(boolean)유형이라고도 하며, 참(true)이나 거짓(false)의 값을 표현하는 자료형이다.

### undefined 유형과 null 유형

- undefined는 단순히 '변수에 값이 할당되지 않았다'는 의미이다.
- 반면에 null은 '데이터의 값이 유효하지 않은 상태'를 나타낸다.

### 배열

- **배열(array)** 는 하나의 변수에 값을 여러 개 저장할 수 있다.
- 다음과 같이 데이터 값을 쉼표로 구분해서 대괄호([])로 묶으면 배열을 선언할 수 있는데, 대괄호 안에 값을 입력하지 않으면 빈 배열이 만들어진다. 물론 빈 배열도 배열을 선언한 것이다.

```
배열명["값1", "값2", ....]
배열명[]
```

- 배열은 여러 개의 요소로 구성되고 각 요소는 자신만의 방 번호를 가진다.
- 이 방 번호가 **인덱스**이며, 0부터 시작한다.
  > 자바스크립트의 편리한 점이면서도 약점인 부분이 데이터 유형이 유연하다는 것이다. 다시 말해 변수의 데이터 유형이 중간에 바뀔 수도 있다는 것이다. 프롬프트 창에서 입력받은 값은 문자열이었지만 사칙연산에 사용된 문자열은 자동으로 숫자형으로 변환되어 계산된다.

## 14-3 연산자 알아보기

### 산술 연산자

- 산술 연산자는 수학 계산을 할 때 사용하는 연산자이다.
- 연산자의 왼쪽이나 오른쪽에 있는 연산 대상이 '피연산자'라고 하는데, 산술 연산자에서 피연산자는 숫자나 변수가 온다.
- 종류: +, -, \*, /, %/ ++, --

### 할당 연산자

- **할당 연산자**는 연산자(또는 연산식) 오른쪽의 실행 결과를 왼쪽 변수에 할당하는 연산자로 대입 연산자라고도 한다.
- 변수에 값을 할당하거나 연산식의 결과를 변수에 저장할 때 할당 연산자를 사용한다.
- 종류: =, +=, -=, \*=, /=, %=

### 연결 연산자

- **연결 연산자**는 둘 이상의 문자열을 합쳐서 하나의 문자열로 만드는 연산자이다.
- 연산자 기호로 '+' 기호를 사용한다.

```js
document.write(birthYear + "년에 태어난 사람의 나이는 " + age + "세입니다.");
```

### 비교 연산자

- **비교 연산자**는 피연산자 2개의 값을 비교해서 참이나 거짓으로 결괏값을 반환한다.
- 이 연산자는 주로 두 값을 비교하므로 어떠한 조건을 체크할 때 사용한다.
- 종류: ==, ===, !=, !==, <, <=, >, >=

#### ==, != 연산자와 ===, !== 연산자 비교

- == 연산자와 != 연산자는 피연산자의 자료형을 자동으로 변환해서 비교한다.
- 아래 식에서 숫자 3과 문자열 "3"을 비교하면 왼쪽의 숫자 3을 문자열로 변환해서 비교한다.

```
3 == "3"  // true
3 != "3"  // false
```

- 반면에 === 연산자와 !== 연산자는 피연산자의 자료형을 변환하지 않는다.

```
3 === "3" // false
3 !== "3" // true
```

- 그래서 프로그램에서 값을 비교할 때는 자료형을 자동으로 변환하지 않기 위해 === 연산자와 !== 연산자를 더 많이 사용한다.

#### 문자열의 비교

- 비교 연산자는 숫자뿐만 아니라 문자열도 서로 비교할 수 있다.
- 피연산자가 문자열이라면 문자열에 있는 문자들의 아스키(ASCII)값을 비교해서 결정한다.

  > 아스키(ASCII)값이란 컴퓨터에서 문자를 숫자에 일대일로 대응한 값을 의미한다. 예를 들어 대문자 A의 아스키값은 숫자 65이고 소문자 a의 아스키값은 97이다. 이렇게 아스키값을 정리한 표를 '아스키 코드 테이블'이라고 한다. [링크](theasciicode.com)

- 문자열에서 비교할 문자가 여러 개인 경우 맨 앞의 문자부터 하나씩 비교한다. 예를 들어 양쪽 문자열에서 첫 번째 문자의 아스키값이 같으면 두 번째 아스키값을 비교하고, 그것도 같으면 그 다음 아스키값을 비교하는 순으로 진행한다.
- 다음은 "javascript"와 "Javascript" 문자열을 서로 비교하는 예제입니다. 소문자 아스키값이 대문자 아스키값보다 크므로 "j"와 "J"를 비교하여 true를 출력한다.

```js
"javascript" > "Javascript"; // true (소문자 아스키값 > 대문자 아스키값)
```

### 논리 연산자

- 논리 연산자는 불리언(boolean) 연산자라고도 하며 true, false를 처리하는 연산자이다.
- 즉, true, false 자체가 피연산자인 연산자이다. 논리 연산자는 주로 프로그램에서 조건을 체크할 때 사용한다.
- 종류: ||, &&, !

## 14-4 조건문 알아보기

### if 문과 if~else 문 알아보기

- if 문이나 if~else 문을 사용하면 스크립트 안에서 조건을 체크할 수 있다.

```js
if(조건) {
  조건 결괏값이 true일 때 실행할 명령
}
- if 문은 결괏값이 true일 때만 실행하므로 true가 아닐 때 명령을 수행하려면 한계가 있다. 그래서 등장한 것이 else 문이다.
- if 조건의 결괏값이 true가 아닐 때 실행할 명령을 else 문 다음에 추가한다.
~~~js
if(조건) {
  조건 결괏값이 true일 때 실행할 명령
}
else {
  조건 결괏값이 false일 때 실행할 명령
}
```

- 하지만 프로그래밍을 할 때 하나의 if~else 문으로 해결되지 않는 상황이 더 많다.
- 이럴 때는 if~else 문 안에 또다시 if~else 문을 사용할 수 있는데, 이를 **중첩된 if~else 문**이라고 한다.

### 조건 연산자로 조건 체크하기

- 만약 조건이 하나이고 true일 때와 false일 때 실행할 명령이 각각 하나뿐이라면 조건 연산자를 사용하는 것이 더 간단하다.

```
(조건) ? true일 때 실행할 명령 : false일 때 실행할 명령
```

```js
userNumber % 3 === 0 ? alert("3의 배수입니다.") : alert("3의 배수가 아닙니다.");
```

### 논리 연산자로 조건 체크하기

- 조건을 2개 이상 체크할 경우에는 조건 연산자를 사용해 조건식을 만든다.
- 두 조건이 true일 경우와 조건 1개만 true일 경우처럼 여러 경우의 수를 따질 때는 논리 연산자를 사용한다.

#### OR 연산자

- OR 연산자 기호는 '||'을 사용하며, 피연산자 2개 중에서 true가 하나라도 있으면 결괏값은 true이다.

#### AND 연산자

- AND 연산자 기호는 '&&'를 사용하며, 피연산자 2개 중에서 false가 하나라도 있으면 결괏값은 false가 된다.

#### NOT 연산자

- NOT 연산자 기호는 '!'를 사용하며, true나 false를 반대로 뒤집는다.

### switch 문

- 처리할 명령이 많다면 if~else문 보다는 switch문이 더 편리하다.

```
switch(조건)
{
  case 값1: 명령1
    break
  case 값2: 명령2
    break
  .....
  default: 명령n
}
```

## 14-5 반복문 알아보기

### for문 사용하기

- for문은 자바스크립트에서 가장 많이 사용하는 반복문이다.
- for문은 값이 일정하게 커지면서 명령을 반복하여 실행할 때 사용한다.

```
for(초깃값; 조건; 증가식) {
  실행할 명령
}
```

### 중첩된 for문 사용하기

- for문 안에 다른 for문을 넣어서 사용할 수도 있는데 이것을 **중첩된 for 문**이라고 한다.

```js
<script>
var i, j;

for (i = 1; i <= 9; i++) {
  document.write("<div>");
  document.write("<h3>" + i + "단</h3>");
  for (j = 1; j <= 9; j++) {
    document.write(i +" X " + j + " = " + i*j + "<br>");
  }
  document.write("</div>");
}
</script>
```

### while 문과 do~while 문 사용하기

- while 문은 조건이 true인 동안 명령을 반복한다.

```
while(조건) {
  실행할 명령
}
```

- while 문과 달리 do~while 문은 조건이 맨 뒤에 붙는다.
- do 문은 일단 명령을 한 번 실행한 후 while 문에서 조건을 체크한다. 그러므로 조건이 false라 하더라도 일단 명령은 최소한 한 번 실행된다.

```
do {
  실행할 명령
} while(조건)
```

```js
<h1>while문을 사용한 팩토리얼 계산</h1>

<script>
    var n = prompt("숫자를 입력하세요.","10");
    var msg = "";

    if (n !== null) {  // '취소' 버튼을 누르지 않았는지 체크
      var nFact = 1;  // 결과 값
      var i = 1;  // 카운터

      while(i <= n) {
        nFact *= i;
        i++;
      }
      msg = n + "! = " + nFact;  // 결과 값을 표시할 문자열
    }
    else
      msg = "값을 입력하지 않았습니다.";

    document.write(msg);  // 결과 표시
</script>
```

### break 문과 continue 문 사용하기

- 반복문은 지정한 횟수만큼 명령을 반복할 때 사용한다.
- 하지만 특정 조건에서 반복문을 멈춰야하거나, 반복문 중간에서 되돌아가야 할 경우가 생긴다.
- 이럴 때 break 문과 continue 문이 필요하다.

#### 멈추는 break 문

- 반복문에서 조건의 역할은 명령이 조건에 맞는지 체크하고 명령을 반복한다.
- 기본적으로 for문과 while문 둘 다 종료 조건이 있지만, 종료 조건이 되기 전에 반복문을 빠져나와야 할 경우도 있다.

### 건너뛰는 continue 문

- continue문은 주어진 조건에 해당하는 값을 만나면 해당 반복문을 건너뛴다.
- 그리고 반복문의 맨 앞으로 돌아가 다음 과정으로 넘어가도록 한다. (쉽게 말해 한 차례 건너뜀)

# 15 함수와 이벤트

## 15-1 함수 알아보기

### 여러 동작을 묶은 덩어리, 함수

- 자바스크립트 프로그램은 단순히 동작 하나만 실행되는게 아니라 여러 가지 동작이 연결된다.
- 이렇게 동작해야 할 목적대로 묶은 명령을 \*\*함수(function)라고 한다.
- 함수를 사용하면 각 명령의 시작과 끝을 명확하게 구별할 수 있고, 묶은 기능에 이름을 붙여서 어디서든 같은 이름으로 명령을 실행할 수 있다.
  > alert() 함수와 같이 자바스크립트에 미리 만들어 놓은 함수를 내장 함수라고 한다.

### 함수는 왜 사용할까?

- 개발자는 프로그래밍을 할 때 alert() 함수처럼 자바스크립트에 들어 있는 함수를 가져다 사용하거나, 자신이 필요한 명령을 직접 함수로 만들어서 사용한다.

### 함수 선언 및 호출

- 함수가 어떤 명령을 처리할지 미리 알려주는 것을 **함수를 선언한다** 또는 **함수를 정의한다**고 한다.
- 함수를 선언할 때는 함수마다 서로 다른 이름을 붙여 나중에 사용할 때 알아보기 쉽도록 한다.

```js
function 함수명() {
  명령;
}
```

- 함수를 선언한 후에는 따로 실행하는 코드를 작성해야 한다.
- 이렇게 선언한 함수를 사용하는 것을 **함수를 호출한다** 또는 **함수를 실행한다**고 한다.

```
함수명() 또는 함수명(변순)
```

> 웹 브라우저에서 자바스크립트 소스를 해석할 때에는 함수 선언 부분을 가장 먼저 한다. 그래서 개발자가 원하는 어느 곳에 함수를 선언해 놓기만 하면 선언한 위치와 상관없이 함수를 실행할 수 있다.

## 15-2 var를 사용한 변수의 특징

### 변수의 적용 범위 스코프 알아보기

- 자바스크립트에서 변수를 선언하고 사용할 때 변수가 적용되는 범위를 **스코프(scope)** 라고 한다.
- 한 함수 안에서만 사용할 수 있는 변수를 **지역 변수** 또는 **로컬 변수** 라고 한다.
- 스크립트 소스 전체애서 사용할 수 있는 변수를 **전역 변수** 또는 **글로벌 변수** 라고 한다.

#### 함수 안에서만 쓸 수 있는 지역 변수

- 지역 변수는 함수 안에서 선언하고 함수 안에서만 사용한다.
- 지역 변수를 예약하려면 예약어 var와 함께 변수 이름을 지정해야 한다.

#### 스크립트 안에서 자유롭게 쓸 수 있는 전역 변수

- 전역 변수는 지역 변수와 달리 스크립트 소스 코드 전체에서 사용할 수 있다.
- 전역 변수로 사용하려면 함수 밖에서 선언하거나 함수 안에서는 var 예약어를 빼고 선언해야 한다.

```js
<script>
function addNumber() {
  multi = 10 * 20;
}
addNumber()
console.log(multi);
```

### var와 호이스팅

- 자바스크립트에서 변수를 사용할 때 조심해야 할 개념이 있다. 바로 **호이스팅(hoisting)** 이다.
- 호이스팅이란 '끌러올린다'를 뜻하는데, 상황에 따라 변수의 선언과 할당을 분리해서 선언 부분을 스코프의 가장 위쪽으로 끌어올린다.
- 끌어올린다고 해서 실제로 소스 코드를 끌어올리는 것은 아니고 소스를 그런 식으로 해석한다는 의미이다.
- 자바스크립트 해석기는 함수 소스를 훑어보면서 var를 사용한 변수는 따로 기억해 둔다. 즉, 변수를 실행하기 전이지만 '이런 변수가 있구나' 하고 기억해 두기 떄문에 마치 선언한 것과 같은 효과가 있다. 이것이 바로 호이스팅이다.
- 간혹 호이스팅처럼 var 예약어를 사용한 변수는 선언하기 전에 사용하면 프로그램 오류를 발생시킬 수 있다.

### 변수의 선언과 재할당

- var를 사용한 변수는 호이스팅 외에도 **재선언**과 **재할당**을 할 수 있다.

## 15-3 let와 const의 등장

### let을 사용한 변수의 특징

#### 블록 안에서만 쓸 수 있는 변수

- let 예약어로 선언한 변수는 변수를 선언한 블록({ }로 묶은 부분)에서만 유효하고 블록을 벗어나면 사용할 수 없다.
- 만약 전역 변수를 선언하고 싶다면 let 예약어를 쓰지 않고 변수 이름과 초깃값만 할당하면 된다.

#### 재할당은 가능하지만 재선언은 할 수 없는 변수

- let 예약어를 사용하여 선언한 변수는 재할당할 수는 있지만 변수를 재선언할 수는 없다.
- 만약 변수를 중복해서 선언한다면 오류 메시지가 출력된다!

#### 호이스팅이 없는 변수

- var 예약어를 사용한 변수는 선언하기 전에 실행하더라도 아직 할당되지 않은 자료형인 undefined 값을 가질 수 있다. 바로 호이스팅 때문이다.
- 하지만 let 예약어를 사용한 변수는 선언하기 전에 사용할 경우 오류 메시지를 나타낸다.

### const를 사용한 변수의 특징

- const로 선언한 변수는 상수 변수이다. 상수는 프로그램 안에서 변하지 않는 값을 뜻한다.
- const로 할당한 변수는 재선언하거나 재할당할 수 없으며, let 예약어를 사용한 변수처럼 블록 레벨의 스코프를 가진다.

- 변수 때문에 생기는 오류를 줄이려면 let과 const를 사용하는 것이 좋다.

### 자바스크립트 변수, 이렇게 사용하세요

- 자바스크립트는 유연성이 많아 편리한 언어이지만, 프로그램이 커지면 가독성이나 디버깅을 하기 어렵게 만든다.
- 자바스크립트 문법을 벗어나지 않으면서 가독성과 디버깅을 하기 쉽도록 변수 사용 방법을 정리해겠다.

#### 전역 변수는 최소한으로 사용한다

- 전역 변수가 많아지만 오류가 발생할 확률이 높아지므로 되도록 적게 사용하는게 좋다.

#### var 변수는 함수의 시작 부분에서 선언한다

- var를 사용한 변수는 어디에서 선언하든 상관없지만 내부에서 호이스팅이 생기므로 오류가 발생할 수 있다.
- 그래서 var 변수는 함수 시작 부분에 선언하는 것이 변수를 확인하기도 쉽고 오류를 줄이는 방법이다.

#### for 문에서 카운터 변수를 사용할 때는 var 예약어를 사용하지 않는다.

- for 문의 카운터 변수는 for 문 밖에서 var 변수를 선언하거나, 아예 let를 사용해서 블록 변수로 선언하는 것이 좋다.

#### ES6를 사용한다면 예약어 var보다 let을 사용하는 것이 좋다.

- var를 사용한 변수는 재선언할 수 있으므로 실수로 같은 변수를 다시 선언하더라도 오류가 발생하지 않는다. 이럴 때 재선언할 수 없는 let를 사용하는 것이 좀 더 안전하다.

## 15-4 재사용할 수 있는 함수 만들기

### 매개변수, 인수, return 알아보기

- 함수를 실행하는 데 필요한 값을 함수 밖에서 제공하면 함수를 재사용할 수 있다.
- 이렇게 하려면 함수를 선언할 때부터 외부에서 값을 받아 줄 변수를 미리 만들어야 한다.
- 이것을 **매개변수(parameter)** 라고 하고 함수를 호출할 때 괄호 안에 매개변수의 이름을 넣는다.
- 매개변수의 이름을 붙이는 방법은 일반적인 변수 이름을 붙이는 것과 같다.
- 매개변수는 선언된 함수 안에서만 사용하며, 매개변수를 여러 개 사용할 때는 매개변수 이름 사이에 쉼표(,)를 찍어 나열한다.

#### 함수 선언할 때 매개변수 지정하기

- 결괏값을 함수 밖에서 사용하려면 함수를 실행한 위치로 돌려줘야 하는데, 이러한 동작을 **값을 반환한다(return)** 이라고 한다.
- 함수의 결괏값을 반환할 때는 예약어 return을 사용해서 다음에 넘겨줄 값을 지정해 주면 된다.

```js
function addNumber(num1, num2) {
  var sum = num1 + num2;
  return sum;
}
```

- 매개변수가 있는 함수를 호출할 때 실제 값 부분을 **인수(argument)** 라고 한다.
- num1, num2를 매개변수라고 하고, addNumber(2, 3)처럼 함수를 실행할 때 괄호 안에 넣어 준 숫자 2와 3을 인수라고 한다.

```js
var result = addNumber(2, 3);
document.write("두 수를 더 한 값 : " + result);
```

### 함수를 실행하는 과정

1. 자바스크립트 해석기가 function 이라는 예약어를 만나면 함수를 선언하는 부분이라는 걸 인식하고 함수 블록({})을 해석한다. 아직 실행하지 않는다.
2. addNumber(2, 3)을 만나면 해석해 두었던 addNumber() 함수를 실행한다.
3. addNumber() 함수에서 2는 num1로, 3은 num2로 넘기고 더한 값을 sum 변수에 저장한다.
4. 함수 실행이 모두 끝나면 결괏값 sum을 함수 호출 위치, 즉 var result로 넘긴다.
5. 넘겨받은 결괏값을 result라는 변수에 저장한다.
6. result 변수에 있는 값을 화면에 표시한다.

### 매개변수 기본값 지정하기

```js
<script>
  function multiple(a, b = 5, c = 10) { 	// b = 5, c = 10으로 기본값 지정
    return a * b + c;
  }

  var result1 = multiple(5, 10, 20); // a = 5, b = 10, c = 20
  document.write("multiple(5, 10, 20)을 실행하면 결과는 " + result1 + "입니다. <br>")
  var result2 = multiple(10, 20);    // a = 10, b = 20, c = 10(기본값)
  document.write("multiple(10, 20)을 실행하면 세번째 매개변수는 기본값을 사용하고 결과는 " + result2 + "입니다.<br>")
  var result3 = multiple(30);        // a = 30, b = 5(기본값), c = 10(기본값)
  document.write("multiple(30)을 실행하면 두번째,  세번째 매개변수는 기본값을 사용하고 결과는 " + result3 + "입니다.")
</script>
```

## 15-5 함수 표현식

### 익명 함수

- **익명 함수**는 이름이 없는 함수를 말한다.
- 익명 함수는 함수 자체가 **식**이므로 함수를 변수에 할당할 수 있으며, 또한 다른 함수의 매개변수로 사용할 수도 있다.

```js
<script>
  var sum = function(a, b){
    return a + b;
  }
  document.write("함수 실행 결과 : " + sum(10, 20) );
</script>
```

### 즉시 실행 함수

- **즉시 실행 함수**는 한 번만 실행하는 함수이고, 함수를 정의하면서 동시에 실행할 수 있다.
- 즉시 실행 함수는 함수를 실행하는 순간에 자바스크립트 해석기에서 함수를 해석한다.
- 즉시 실행 함수의 기본 형식은 당므과 같다. 함수를 식 형태로 선언하므로 마지막에 세미콜론(;)을 붙인다.

```js
(function () {
  명령;
})();
```

또는

```js
(function (매개변수) {
  명령;
})(인수);
```

- 이 예제 소스들은 따로 호출하지 않았지만 바로 실행된다.

```js
<script>
  (function() {
    var userName = prompt("이름을 입력하세요.");
    document.write("안녕하세요? <span class='accent'>" + userName + "</span>님!");
  }());
</script>
```

```js
<script>
  (function(a, b){   // 함수 선언을 위한 매개변수
    sum = a + b;
  }(100, 200));       // 마지막에 함수 실행을 위한 인수
  document.write("함수 실행 결과 : " + sum);
</script>
```

### 화살표 함수

- ES6 버전부터는 => 표기법(화살표 표기법)을 사용해 함수 선언을 좀 더 간단하게 작성할 수 있다.
- 이 방법은 간단히 **화살표 함수**라고 하는데 익명 함수에서만 사용할 수 있다.

```
(매개변수) => { 함수 내용 }
```

#### 매개변수가 없을 경우

```js
const hi = function () {
  return "안녕하세요?";
};
```

```js
const hi = () => "안녕하세요?";
```

- 그리고 중괄호 안에 내용이 한 줄뿐이라면 중괄호를 생략해서 다음과 같이 작성할 수도 있다. 이때 return 문은 생략된 것으로 간주한다.

```
const hi = () => "안녕하세요?";
```

#### 매개변수가 1개인 경우

- 매개변수가 하나인 경우 매개변수의 괄호는 생략할 수 있다.

```js
let hi = function (user) {
  document.write(user + "님, 안녕하세요?");
};
```

```js
let hi = (user) => {
  document.write(user + "님, 안녕하세요?");
};
```

#### 매개변수가 2개 이상인 경우

```js
let sum = (a, b) => a + b;

document.write("두 수의 합 : " + sum(10, 20));
```

## 15-6 이벤트와 이벤트 처리기

### 이벤트 알아보기

- 이벤트는 웹 브라우저나 사용자가 행하는 어떤 동작을 말한다. (키보드를 누르거나, 웹 브라우저에서 새로운 페이지를 불러오는 것 등)
- 하지만 웹 브라우저 안에서 이루어지는 모든 동작이 이벤트는 아니다. 이벤트는 웹 페이지를 읽어 오거나 링크를 클릭하는 것처럼 웹 문서 영역 안에서 이루어지는 동작만 말한다.

#### 마우스 이벤트

- 마우스 이벤트는 마우스를 이용해서 버튼이나 휠 버튼을 조작할 때 발생한다.

| 종류      | 설명                                                                  |
| --------- | --------------------------------------------------------------------- |
| click     | 사용자가 HTML 요소를 클릭할 때 이벤트가 발생한다.                     |
| dbclick   | " 더블 클릭할 때 발생한다.                                            |
| mousedown | 사용자가 요소 위에서 마우스 버튼을 눌렀을 때 이벤트가 발생한다.       |
| mousemove | " 마우스 포인트를 움직일 때 발생한다.                                 |
| mouseover | 마우스 포인터가 요소 위로 옮겨질 때 이벤트가 발생한다.                |
| mouseout  | 마우스 포인터가 요소를 벗어날 때 이벤트가 발생한다.                   |
| mouseup   | 사용자가 요소 위에 놓인 마우스 버튼에서 손을 뗄 때 이벤트가 발생한다. |

#### 키보드 이벤트

- 키보드 이벤트는 키보드에서 특정 키를 조작할 때 발생한다.

| 종류     | 설명                                          |
| -------- | --------------------------------------------- |
| keydown  | 사용자가 키를 누르는 동안 이벤트가 발생한다.  |
| keypress | 사용자가 키를 눌렀을 때 이벤트가 발생한다.    |
| keyup    | 사용자가 키에서 손을 뗄 때 이벤트가 발생한다. |

#### 문서 로딩 이벤트

- 서버에서 웹 문서를 가져오거나 문서를 위아래로 스크롤하는 등 웹 문서를 브라우저 창에 보여주는 것과 관련된 이벤트이다.

| 종류   | 설명                                                                |
| ------ | ------------------------------------------------------------------- |
| abort  | 문서가 완전히 로딩되기 전에 불러오기를 멈췄을 때 이벤트가 발생한다. |
| error  | 문서가 정확히 로딩되지 않았을 때 이벤트가 발생한다.                 |
| load   | 문서 로딩이 끝나면 이벤트가 발생한다.                               |
| resize | 문서 화면 크기가 바뀌었을 때 이벤트가 발생한다.                     |
| scroll | 문서 화면이 스크롤되었을 때 이벤트가 발생한다.                      |
| unload | 문서에서 벗어날 때 이벤트가 발생한다.                               |

#### 폼 이벤트

- 폼은 로그인, 검색, 게시판, 설문 조사처럼 사용자가 입력하는 모든 요소를 가리킨다.

| 종류   | 설명                                                                                               |
| ------ | -------------------------------------------------------------------------------------------------- |
| blur   | 폼 요소에 포커스를 잃었을 때 이벤트가 발생한다.                                                    |
| change | 목록이나 체크 상태 등이 변경되면 이벤트가 발생한다. input, select, textarea 태그에서 사용한다.     |
| focus  | 폼 요소에 포커스가 놓였을 때 이벤트가 발생한다. label, select, textarea, button 태그에서 사용한다. |
| reset  | 폼이 리셋되었을 때 이벤트가 발생한다.                                                              |
| submit | submit 버튼을 클릭했을 때 이벤트가 발생한다.                                                       |

### 이벤트 처리기 알아보기

- 웹 문서에서 이벤트가 발생하면 처리하는 함수를 **이벤트 처리기** 또는 **이벤트 핸들러(event handler)** 라고 한다.
- 이벤트를 처리하는 가장 기본적인 방법은 이벤트가 발생한 HTML 태그에 이벤트 처리기를 직접 연결하는 것이다. 이 방법은 자바스크립트 초기 버전부터 사용했으며 지금도 많이 사용하고 있다.

```
<태그 on이벤트명 = "함수명">
```

```html
<ul>
  <li>
    <a href="#" onclick="alert('버튼을 클릭했습니다.')"> Green </a>
  </li>
  <li>
    <a href="#" onclick="alert('버튼을 클릭했습니다.')"> Orange </a>
  </li>
  <li>
    <a href="#" onclick="alert('버튼을 클릭했습니다.')"> Purple </a>
  </li>
</ul>
```

- 이벤트가 발생한 후에 여러 가지 명령을 실행해야 한다면, 그 명령을 묶어서 하나의 자바스크립트 함수로 만드는 것이 좋다. 그리고 이벤트가 발생할 때 함수 이름과 인수를 지정하여 실행한다.

```html
<ul>
  <li><a href="#" onclick="changeBg('green')">Green</a></li>
  <li><a href="#" onclick="changeBg('orange')">Orange</a></li>
  <li><a href="#" onclick="changeBg('purple')">Purple</a></li>
</ul>
<div id="result"></div>

<script>
  function changeBg(color) {
    var result = document.querySelector("#result");
    result.style.backgroundColor = color;
  }
</script>
```

## 15-7 DOM을 이용한 이벤트 처리기

- 지금까지 이벤트 처리기를 짖어하는 방법은 HTML이 주인이 되어 자바스크립트의 함수를 불러와서 사용했다.
- 하지만 DOM을 사용하면 자바스크립트가 주인이 되어 HTML의 요소를 가져와서 이벤트 처리기를 연결한다.

```
웹 요소.onclick = 함수;
```

- 자바스크립트에서는 웹 요소를 여러 방법으로 가져올 수 있는데, 그 중에서 함수 querySelector()를 사용하여 가져오는 것이 쉽다.
- querySelector()의 괄호 안에는 클래스 이름이나 id 이름 또는 다양한 선택자를 넣을 수 있다.

```html
<button id="change">글자색 바꾸기</button>
<p>Reprehenderit tempor do quis sunt eu et exercitation deserunt.</p>

<script>
  // 방법 1 : 웹 요소를 변수로 지정 & 미리 만든 함수 사용
  var changeBttn = document.querySelector("#change");
  changeBttn.onclick = changeColor;

  function changeColor() {
    document.querySelector("p").style.color = "#f00";
  }

  // 방법 2 : 웹 요소를 따로 변수로 만들지 않고 사용
    // document.querySelector("#change").onclick = changeColor;

		// function changeColor() {
    //   document.querySelector("p").style.color = "#f00";
    // }

    // 방법 3 : 직접 함수를 선언
    // document.querySelector("#change").onclick = function() {
    //   document.querySelector("p").style.color = "#f00";
    // };
```

- 상세설명 표시 닫고 열기

```html
<img src="images/flower.jpg" alt="">
  <button class="over" id="open">상세 설명 보기</button>
  <div id="desc" class="detail">
    <h4>등심붓꽃</h4>
    <p>북아메리카 원산으로 각지에서 관상초로 흔히 심고 있는 귀화식물이다. 길가나 잔디밭에서 흔히 볼 수 있다. 아주 작은 씨앗을 무수히 많이 가지고 있는데 바람을 이용해 씨앗들을 날려보내거나, 뿌리줄기를 통해 동일한 개체들을 많이 만들어 냄으로써 번식한다. </p>
    <button id="close">상세 설명 닫기</button>
  </div>
</div>

<script>
  document.querySelector('#open').onclick = function() {
    document.querySelector('#desc').style.display = "block";	// 상세 설명 부분을 화면에 표시
    document.querySelector('#open').style.display = "none";   // '상세 설명 보기' 단추를 화면에서 감춤
  }
  document.querySelector('#close').onclick = function() {
    document.querySelector('#desc').style.display = "none";	   // 상세 설명 부분을 화면에서 감춤
    document.querySelector('#open').style.display = "block";	 // '상세 설명 보기' 단추를 화면에 표시
  }
</script>
```

# 16 자바스크립트와 객체

## 16-1 객체 알아보기

### 객체란?

- 프로그래밍 언어에서 **객체(개체)** 는 여러 가지 의미로 해석할 수 있지만, 자바스크립트에서 객체는 프로그램에서 인식할 수 있는 모든 대상을 가리킨다는 정도로 이해해둬라.
- 자바스크립트는 웹 사이트나 웹 애플리케이션을 개발하는 언어이므로 웹과 관련된 대상을 모두 객체로 인식한다.
  > - 문서 개체 모델(DOM): 웹 문서 자체도 객체이고 그 안에 삽입되어 있는 이미지와 링크, 텍스트 필드 등도 모두 객체이다. 일반적으로 웹 문서에 삽입하는 요소는 document, image, link 객체 등이 있다.
  > - 브라우저 관련 객체: 웹 브라우저에서 사용하는 정보도 객체로 나타낼 수 있다. 사용하는 브라우저 정보를 담고 있는 navigator 객체를 비롯해 history, location, screen 객체 등이 있다.
  > - 내장 객체: 웹 프로그래밍을 할 때 자주 사용하는 요소는 자바스크립트 안에 미리 객체로 정의되어 있는데, 이를 내장 객체라고 한다. 예를 들어 날짜, 시간과 관련된 프로그램을 개발하려면 Date 객체를 가져와 쉽게 사용할 수 있다.

#### 객체의 인스턴스 만들기

- 자바스크립트에서 객체는 참조 형태로 사용해야 한다. 즉, 객체 자체가 아니라 **인스턴스**의 형태로 만들어서 사용해야 한다.
- 자바스크립트 안에 정의된 객체는 그대로 두고 객체와 똑같은 속성과 기능을 만들 수 있다. 자바스크립트의 객체가 틀이라면 그 틀을 기본으로 해서 계속 같은 모양으로 찍어 내는 것이 인스턴스이다.
- 그리고 그 인스턴스에 식별자를 붙여 사용한다. 객체의 인스턴스를 만들 때는 다음과 같이 new라는 예약얼르 사용한다. new 뒤에 만들려고 하는 개체 이름을 써주면 된다.

```
new 객체명
```

- 예를 들어 현재 날짜와 시간을 표시하는 프로그램을 작성한다고 생각해보자. 자바스크립트에서 날짜나 시간 정보는 Date 객체에 저장하고 관리한다.
- 그래서 날짜나 시간 관련 프로그램을 작성하려면 가장 먼저 Date 객체의 인스턴스를 만들고, 그 인스턴스를 변수에 저장해서 사용한다.

```js
<script>
  var now = new Date(); document.write("현재 시각은 " + now); // 현재 날짜와
  시간 표시하기
</script>
```

#### 프로퍼티와 매서드 이해하기

- 객체에는 **프로퍼티(property)** 와 **메서드(method)** 가 있는데, 쉽게 말해 프로퍼티는 객체의 특징이나 속성을 나타내고, 메서드는 객체에서 할 수 있는 동작을 표현한다.
- '자동차 운전'이 하나의 프로그램이라면 '자동차'는 객체가 되고, 자동차의 프로퍼티는 자동차 제조사나 모델명, 색상, 배기량 등이 된다. 또한 자동차의 메서드는 시동 걸기, 움직이기, 멈추기, 주차하기 등이 된다.

#### 마침표 표기법으로 프로퍼티와 메서드 작성하기

- 인스턴스는 객체의 프로퍼티와 메서드를 그대로 물려받아서 똑같이 사용한다.
- 프로퍼티와 메서드를 표시하려면 인스턴스명 뒤에 마침표(.)를 붙이고 객체의 프로퍼티나 메서드 이름을 작성한다.
- 이때 메서드는 함수와 같은 역할을 하므로 getHours()처럼 이름 옆에 괄호를 넣어야 한다.

```js
<script>
  var now = new Date(); document.write("현재 시각은 " + now.toLocaleString()) ;
  // 로컬 형식으로 표시하기
</script>
```

## 16-2 자바스크립트의 내장 객체

### Array 객체

- Array 객체는 자바스크립트의 여러 가지 내장 객체 중에서 **배열**을 다룬다. 배열은 자바스크립트에서 자주 사용하는 자료형이다.

#### Array 객체로 배열 만들기

```js
var numbers = new Array(); // 배열의 크기를 지정하지 않음
var numbers = new Array(4); // 배열의 크기를 지정함
```

- 초깃값이 있는 배열이라면 다음과 같이 인스턴스 선언과 요솟값을 한번에 할당해 작성할 수 있다.

```js
var numbers = ["one", "two", "three", "four"]; // 배열 선언
var numbers = Array("one", "two", "three", "four"); // Array 객체를 사용한 배열 선언
```

#### Array 객체의 length 프로퍼티 사용하기

- 배열 요소의 개수는 어떻게 알 수 있나? 바로 Array 객체에 있는 length 프로퍼티를 사용하면 된다. 이 프로퍼티에는 배열 요소의 개수가 저장되어 있다.
- 다음과 같이 마침표(.)를 사용해 length 프로퍼티를 작성한다.

```js
<script>
  var numbers = ["one", "two", "three", "four"];

  for(i = 0; i < numbers.length; i++) {
    document.write("<p>" + numbers[i] + "</p>");
  }
</script>
```

### Array 객체의 메서드

- Array 깩체에는 여러 가지 메서드가 있다. 자세한 내용은 Array 객체 mdn 참고!

#### 배열끼리 합치는 concat() 메서드

- concat() 메서드는 서로 다른 배열 2개를 합쳐 새로운 배열을 만들어 준다. 어느 배열을 먼저 쓰는가에 따라 기준이 달라지고, 결과 배열의 순서도 달라진다.

```js
var nums = [1, 2, 3];
var chars = ["a", "b", "c", "d"];

// 두 개의 배열 합치기
var numsChars = nums.concat(chars);
var charsNums = chars.concat(nums);
document.write(
  "nums에 chars 합치면 : ",
  numsChars,
  "<br> chars에 nums 합치면 : ",
  charsNums
);
```

#### 배열 안의 요소끼리 합치는 join() 메서드

- join() 메서드는 배열 요소를 연결해서 하나의 문자열로 만들어 준다.
- 이때 각 요소 사이에 원하는 구분자('/')를 넣을 수도 있는데, 따로 지정하지 않으면 요소를 쉼표(,)로 구분한다.

```js
// 배열 내의 요소 합치기
var string1 = nums.join();
document.write("구분자 없이 : ", string1);
document.write("<br>");
var string2 = chars.join("/");
document.write("/ 구분자 지정 : ", string2);
document.write("<hr>");
```

#### 새로운 요소를 추가하는 push(), unshift() 메서드

- 배열에 새로운 요소를 추가하려면 push()나 unshift() 메서드를 사용한다.
- 배열 맨 끝에 요소를 추가하려면 push() 메서드를 사용하고, 배열 맨 앞에 요소를 추가하려면 unshift() 메서드를 사용한다.
- 주의해야 할 점은 배열 맨 앞과 맨 뒤에 요소를 추가하면 원래 있던 배열이 바뀐다는 것이다.

```js
// 요소 추가 - 새로운 length 값 반환
var ret1 = nums.push(4, 5); // 배열 끝에 추가
document.write("length : ", ret1, " | 배열 : ", nums);
document.write("<br>");
var ret2 = nums.unshift(0); // 배열 앞에 추가
document.write("length : ", ret2, " | 배열 : ", nums);
document.write("<hr>");
```

#### 배열에서 요소를 꺼내는 pop(), shift() 메서드

- 배열에서 뒤에 있는 요소를 꺼낼 때는 pop() 메서드를 사용하고, 앞에 있는 요소를 꺼낼 때는 shift() 메서드를 사용한다.
- 두 메서드는 꺼낸 요솟값을 반환하며, 기본 배열은 꺼낸 요소가 빠진 상태로 변경된다.

```js
// 요소 추출 - 꺼낸 요소 반환
var popped1 = chars.pop(); // 마지막 요소 꺼냄
document.write("꺼낸 요소 : ", popped1, " | 배열 : ", chars);
document.write("<br>");
var popped2 = chars.shift(); // 첫번째 요소 꺼냄
document.write("꺼낸 요소 : ", popped2, " | 배열 : ", chars);
document.write("<hr>");
```

#### 원하는 위치에 요소를 추가, 삭제하는 splice() 메서드

- 배열 중간 부분에서 요소를 추가하거나 삭제하려면 splice() 메서드를 사용한다.

1. 인수가 1개인 경우
   - 괄호 안의 인수는 배열의 인덱스값, 즉 배열의 위치를 가리킨다.
   - splice() 메서드는 인수가 지정한 인덱스의 요소부터 배열의 맨 끝 요소까지 삭제한다.

```css
// 인수가 1개일 경우
var numbers = [1, 2, 3, 4, 5];
var newNumbers = numbers.splice(2);
document.write("반환된 배열 : " + newNumbers + "<br>" );
document.write("변경된 배열 : " + numbers );
document.write("<hr>");
```

2. 인수가 2개인 경우

   - splice() 메서드에 인수가 2개라면 첫 번째 인수는 인덱스값이고 두 번째 인수는 삭제할 요소의 개수이다.

```js
// 인수가 2개일 경우
var study = ["html", "css", "web", "jquery"];
var newStudy = study.splice(2, 1);
document.write("반환된 배열 : " + newStudy + "<br>");
document.write("변경된 배열 : " + study);
document.write("<hr>");
```

3. 인수가 3개 이상인 경우
   - splice() 메서드의 인수가 3개 이상이라면 첫 번째 인수는 배열에서 삭제할 시작 위치를 나타내고, 두 번째 인수는 삭제할 개수를 알려 준다. 그리고 세 번째 인수부터는 삭제한 위치에 새로 추가할 요소를 지정한다.

```js
// 인수가 3개 이상일 경우
var newStudy2 = study.splice(2, 1, "js");
document.write("반환된 배열 : " + newStudy2 + "<br>");
document.write("변경된 배열 : " + study);
```

#### 기존 배열을 바꾸지 않으면서 요소를 꺼내는 slice() 메서드

- 이번에 알아볼 slice() 메서드는 배열에서 요소를 꺼내는 기능을 한다. pop(), shift() 함수와 같아 보이지만, 차이점은 시작과 끝 인덱스를 지정해서 요소를 여러 개 꺼내고, 실행 결과 기존 배열이 바뀌지 않는다.

1. 인수가 1개인 경우

   - 인수를 하나만 지정하면 그 인수를 시작 인덱스로 간주하고 지정한 요소부터 마지막 요소까지 꺼내서 변환한다.

2. 인수가 2개인 경우
   - 인수 2개를 사용하면 어러 개의 요소를 꺼낼 수 있다. 즉 slice() 메서드의 인수 2개는 꺼낼 요소의 구간을 의미한다.
   - 첫 번째 인수는 배열의 시작 인덱스이고, 두 번째 인수는 끝 인덱스의 바로 직전 인덱스를 가리킨다.

```js
// 추출한 요소로 배열 만듦, 기존 배열 변경안됨
var colors = ["red", "green", "blue", "white", "black"];
var colors2 = colors.slice(2); //인덱스 2부터 끝까지
document.write(colors2);
document.write("<br>");
var colors3 = colors.slice(2, 4); // 인덱스 2,3
document.write(colors3);
```

### Date 객체

- Date 객체는 현재 날짜와 시간을 출력하거나 달력을 표시할 수도 있고, 특정일까지 얼마나 남았는지 알려 주는 등 사이트에서 여러 가지로 응용할 수 있다.

#### Date 객체 인스턴스 만들기

- 자바스크립트에서 Date 객체를 사용하려면 우선 Date 객체의 인스턴스를 만들어야 한다.
- 현재 날짜로 설정할 경우에는 다음과 같이 간단히 예약어 new를 붙여 주면 된다.

```js
new Date();
```

- 특정한 날짜를 저장한 Date 객체를 만들고 싶다면 Date 다음에 붙이는 괄호 안에 날짜 정보를 입력한다.

```js
new Date("2020-02-25");
```

- 또한 시간 정보까지 Data 객체로 나타내려면 날짜 다음에 대문자 'T'를 추가한 후 그 뒤에 시간을 입력한다.

```js
new Date("2020-02-25T18:00:00");
```

#### 자바스크립트의 날짜, 시간 입력 방식 알아보기

- Date 객체를 사용하여 날짜와 시간을 지정하려면 자바스크립트가 인식할 수 있는 날짜와 시간 형식으로 써야 한다.

1. YYYY-MM-DD 형식
2. YYYY-MM-DDTHH 형식
3. MM/DD/YYYY 형식
4. 이름 형식

#### Date 객체의 메서드

- 날짜와 시간 정보를 사용하기 위한 Date 객체를 만들었다면 Date 객체에 정의된 메서드를 사용할 수 있다.
- Date 객체의 메서드는 크게 3가지로 구분된다. 날짜/시간 정보를 가져오는 메서드, 사용자가 원하는 날짜/시간으로 설정하는 메서드, 마지막으로 날짜/시간 형식을 바꿔 주는 메서드
  > 자세한 메서드들은 mdn 검색!

### Math 객체

#### Math 객체의 프로퍼티

- Math 객체에서 자주 사용하는 프로퍼티는 다음과 같이 정리할 수 있다. Math 객체의 프로퍼티는 항상 정해진 값을 가지고 있다.

| 종류    | 설명                    |
| ------- | ----------------------- |
| E       | 오일러 상수             |
| PI      | 원주율(3.1415926535...) |
| SORT2   | 루트2(1.41421...)       |
| SORT1_2 | 1\*루트2(0.70710...)    |
| LN2     | loge^2                  |
| LOG2E   | log2^e                  |

#### Math 객체의 메서드

- Math 객체의 메서드는 주로 수학과 관련된 함수의 결괏값을 반환한다.
  > math 객체의 자세한 메서드들은 mdn 참고

## 16-3 브라우저와 관련된 객체

### 브라우저와 관련된 객체 알아보기

- 웹 브라우저가 열리면 가장 먼저 window라는 객체가 만들어지고 밑으로 하위 요소에 해당하는 객체들이 나타난다.
- 이 하위 객체는 웹 문서와 주소 표시줄처럼 브라우저 요소에 해당하며 각각 다른 하위 객체를 가진다.
- 예를 들어 window의 하위 객체는 document, history 등으로 나뉘고, 다시 document의 하위 객체는 area, image 등으로 구분된다.

| 종류      | 설명                                                                                       |
| --------- | ------------------------------------------------------------------------------------------ |
| window    | 브라우저 창이 열릴 때마다 하나씩 만들어진다. 브라우저 창 안의 요소 중에서 최상위에 있다.   |
| document  | 웹 문서마다 하나씩 있으며, \<body> 태그를 만나면 만들어진다. HTML 문서의 정보가 담겨 있다. |
| navigator | 현재 사용하는 브라우저의 정보가 담겨있다.                                                  |
| history   | 현재 창에서 사용자의 방문 기록을 저장한다.                                                 |
| location  | 현재 페이지의 URL 정보가 담겨 있다.                                                        |
| screen    | 현재 사용하는 화면 정보를 다룬다.                                                          |

### window 객체의 프로퍼티

- window 객체는 웹 브라우저의 상태를 제어하며 자바스크립트의 최상위에 있다. (자바스크립트의 모든 객체는 window 객체 안에 포함됨)
- window 객체의 프로퍼티는 주로 웹 브라우저 창의 정보를 가져오거나 값을 바꿀 때 사용한다.
- 프로퍼티를 사용하려면 window.fullScreen처럼 프로퍼티 이름 앞에 'window.'를 붙인다.

### window 객체의 메서드

- window 객체의 메서드는 대화 창을 표시하거나 브라우저 창의 크기나 위치를 알아내고 지정하는 등 웹 브라우저 창 자체와 관련된다.
- 우리가 앞에서 사용한 alert() 문이나 prompt() 문은 window 객체의 메서드이므로 원래는 window.alert()라고 해야 한다.
- 하지만 window 객체는 기본 객체이므로 'window.'를 생략할 수 있다.

#### 새 브라우저 창을 여는 open() 메서드

- 링크를 클릭하거나 웹 문서를 열 때 새 창이 자동으로 뜨게 하려면 window.open() 메서드를 사용한다. (주로 홈페이지의 팝업 창을 띄울 때 사용)
- 팝업창은 홈페이지의 이벤트, 공지사항을 전하거나 쇼핑몰에서 상품 정보를 크게 보여 주는 역할을 한다.

```
window.open(경로, 창 이름, 창 옵션)
```

1. 경로: 팝업 창에 표시할 문서나 사이트의 경로(주소)를 나타낸다.
2. 창 이름: 팝업 창의 이름을 지정하면 항상 이 창에 팝업 내용이 나타나도록 할 수 있다. 이름을 지정하지 않으면 팝업 창이 계속 새로 나타난다.
3. 창 옵션: left, top 속성을 사용해 위치를 정하거나 width, height 속성을 사용해 크기를 지정할 수 있다. 위치를 지정하지 않으면 팝업 창은 화면의 맨 왼쪽 위에 나타난다.

- 다음은 너비 500px, 높이 400px인 팝업 창을 여는 예제이다. 브라우저에서 웹 문서를 열자마자 팝업 창이 바로 나타난다.

```html
<script>
  window.open("notice.html", "", "width=500, height=400");
</script>
```

#### 창 이름 지정하기

- 똑같은 팝업 창이 여러 번 나타나서 귀찮다면 팝업창의 이름을 지정하면 된다.
- 팝업 창에 이름이 생겨서 지정한 창에만 내용이 나타난다.

```html
<script>
  window.open("notice.html", "pop", "width=500, height=400");
</script>
```

#### 팝업 창 위치 지정하기

- open() 메서드로 팝업 창을 표시하면 기본 위치는 화면의 왼쪽 위 구석에 나타난다.
- 팝업 창의 위치는 open() 메서드의 left와 top 속성으로 지정할 수 있다.

```html
<script>
  window.open("notice.html", "pop", "width=500, height=400, left=100, top=200");
</script>
```

#### 팝업 차단 고려하기

- 대부분의 최신 웹 브라우저에서는 팝업 창이 열리지 않도록 하는 것을 기본으로 설정하는 경우가 많다.
- 그래서 사이트의 공지와 같은 중요한 내용을 팝업 창으로 보여주어야 한다면 팝업 차단된 상태인지 체크하여 사용자에게 알려 주는 것이 좋다.
- 다음은 팝업 창을 여는 openPop() 함수에서 웹 브라우저의 차단 여부를 확인하는 예제이다.
- 따라서 window.open() 메서드를 실행한 후 반환값을 체크하면 팝업이 차단되었는지 알아낼 수 있다.

```html
<script>
  var blocked = false;
  function openPopup() {
    var newWin = window.open("notice.html", "pop", "width=500, height=400");
    if (newWin == null) {
      alert("팝업이 차단되어 있습니다. 팝업 차단을 해제해 주세요.");
    }
    newWin.moveBy(100, 100);
  }
</script>
```

#### 브라우저 창을 닫는 close() 메서드

- 일반적으로 팝업 창 내용을 모두 살펴본 후에 창을 닫을 수 있도록 화면 아래쪽에 [닫기] 버튼이나 링크를 포함하는 경우가 많다.

```
window.close()
```

- 다음은 간단히 링크나 버튼 태그에 window.close() 메서드를 연결한 예제이다.

```html
<button onclick="javascript:window.close();">닫기</button>
```

### navigator 객체

- navigator 객체에는 웹 브라우저의 버전을 비롯해 플러그인 설치 정보나 온오프라인 등의 여러 정보가 담겨 있다.
- 이 정보는 사용자가 수정할 수 없으며 가져와서 보여 줄 수만 있다.

#### 웹 브라우저와 렌더링 엔진

- 웹 브라우저가 점점 다양해짐에 따라 모든 사용자의 웹 브라우저에서 똑같이 동작하는 웹 문서를 개발할 필요성이 생겼다.
- 여러 웹 브라우저를 고려하여 개발하는 것은 웹 개발제에게 가장 어려운 부분이기도 하다.
- 여러 웹 브라우저를 고려할 때 가장 먼저 생각해야 할 분야는 렌더링 엔진이다. 아직 표준화되지 않은 CSS 속성 앞에는 브라우저 벤더를 의미하는 프리픽스(prefix)를 지정한다.
- 이렇게 지정하는 이유는 웹 브라우저마다 HTML이나 CSS를 해석하는 **렌더링 엔진**이 다르기 때문이다.
- 웹 브라우저는 웹 문서를 불러오면 내장된 렌더링 엔진에서 소슬르 해석한다. 이때 웹 브라우저마다 사용하는 렌더링 엔진이 다르므로 프리픽스를 붙여 브라우저를 구별하는 것이다.

- 마찬가지로 웹 브라우저마다 내장된 자바스크립트 엔진도 다르다. 그래서 똑같은 HTML5 기술을 사용해서 만든 사이트에 접속하더라도 웹 브라우저마다 보여 주는 효과와 성능은 다를 수 있다.

#### userAgent 프로퍼티 알아보기

- navigator 객체에서 가장 먼저 알아야 할 프로퍼티는 userAgent로 사용자 에이전트 문자열을 의미한다.
- userAgent는 사용자의 웹 브라우저 정보를 서버에 보낼 때 사용한다.
- userAgent에는 사용자의 웹 브라우저 버전, 자바스크립트의 엔진 종류 등 여러 정보가 들어 있다.
- 따라서 서버에서는 그 정보를 확인하여 사용자에게 맞는 웹 페이지를 보여 줄 수 있다.
- 우리가 주로 사용하는 크롬의 사용자 에이전트 문자열은 다음과 같다.

```
// 크롬 userAgent
"Mozilla/5.0 (Windows NT 10.0; Win64 x64) AppleWebkit/537.36 (KHTML, like Gecko) Chorme/81.0.4044.138 Safari/157.36"
```

- 예전에는 웹 브라우저를 식별할 때 사용자 에이전트 문자열을 많이 사용했는데, 최근에는 같은 자바스크립트 엔진을 사용하는 브라우저가 많아서 사용자 에이전트 문자열의 내용이 겹치므로 사용하지 않는 추세이다.

#### navigator 객체 정보 살펴보기

- 크롬 브라우저에서 컨트롤+쉬프트+J를 눌러 콘솔 창을 열고 navigator를 입력한 후 Enter를 누르면 navigator 객체의 모든 정보를 한 눈에 볼수 있다.
- 사용할 수 있는 브라우저가 많아지고 웹 애플리케이션이 등장하면서 navigator 객체에는 진동 감지 속성이나 배터리 상태를 체크하는 속성 등이 새롭게 추가 되고 있다.

### history 객체

- history 객체에는 브라우저에서 [뒤로]나 [앞으로] 또는 주소 표시줄에 입력해서 방문한 사이트 주소가 배열 형태로 저장된다.
- history 객체에는 방문한 URL 정보가 저장되므로 메서드는 방문했던 URL을 앞뒤로 이동하며 페이지를 불러온다.
- length, back(), forward(), go()

### location 객체

- location 객체는 이름에서도 알 수 있듯이 브라우저의 주소 표시줄과 관련된다.
- 즉, location 객체에는 현재 문서의 URL 주소 정보가 들어 있는데 이 정보를 편집하면 현재 브라우저 창에서 열어야 할 사이트나 문서를 지정할 수 있다.
- location 객체의 메서드는 브라우저의 [새로 고침]과 같은 역할을 하는 reload() 메서드와 현재 창에 다른 문서나 사이트를 보여 주는 replace() 메서드가 매우 유용하다.
- 다음 예제는 navigator 객체의 일부 프로퍼티를 가져와 보여준다. 그리고 버튼을 클릭하면 replace() 메서드를 이용해 이지스퍼블리싱 홈페이지로 이동한다.

```html
<script>
    document.write("<p><b>location.href : </b>" + location.href + "</p>");
    document.write("<p><b>location.host : </b>" + location.host + "</p>");
    document.write("<p><b>location.protocol : </b>" + location.protocol + "</p>");
  </script>
</div>
<button onclick="location.replace('http://www.easyspub.com')">이지스퍼블리싱 홈페이지로 이동하기</button>
```

### screen 객체

- 사용자의 화면 크기나 정보를 알아 낼 때 screen 객체를 사용한다.
- screen 객체에서 사용하는 메서드는 화면 방향을 잠그거나 잠근 화면의 방향을 해제하는 역할을 한다.
