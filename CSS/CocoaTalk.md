![CocoaTalk](https://nomadcoders.co/_next/image?url=https%3A%2F%2Fd1telmomo28umc.cloudfront.net%2Fmedia%2Fpublic%2Favatars%2FkokoaThumbnail_h8OxaLt_WUzjUct.jpg&w=3840&q=75)

> 위 문서는 [노마드코더 코코아톡 클론코딩](https://nomadcoders.co/kokoa-clone/lobby) 강의에서 중요하다고 생각하는 내용들을 요약한 것입니다.

# #1 INTRODUCTION

## #1.5 What Makes a Website?

- 웹사이트는 단지 텍스트 파일이다. → 간단한 웹사이트든, 복잡한 웹사이트든!
- 브라우저는 개발자가 준 텍스트 파일을 이해해서 웹사이트를 구현한다.
- 개잘자로써 우리가 해야할 일은 어떤 종류의 text를 써야하고, text 중 어디에 써야하는지 배워야한다.

## #1.6 What is HTML

- 웹사이트를 만들기 위해서는 세가지 언어만 배우면 된다. (HTML, CSS, Javascript)
- HTML → 매우 간단!
- CSS → 간단, 하지만 계속 연습해야함
- Javascript → 간단하진 않지만 마지막 언어이니 너무 걱정할 필요 X

### HTML(HyperText Markup Language)

- 브라우저는 인간들이 쓰는 언어를 이해하지 못한다.
- 개발자가 해야할 일은 브라우저에게 content가 무엇인지 알려주는 것!<br>→HTML으로 브라우저에게 content 구조가 어떤지를 설명해주는 것

## #1.7 What is CSS

### CSS(Cascading Style Sheet)

- CSS는 항상 HTML과 같이 사용한다.
- CSS는 브라우저에게 웹사이트가 어떻게 보여야 하는지에 대해 알려준다.
- HTML이 웹사이트의 뼈대라면, CSS는 근육을 담당

## #1.8 What is Javascript

- Javascript는 웹사이트의 뇌 같은 존재
- 무언가 클릭할 때 어떤 일이 생기는 것 = 동적 상호작용성(interactivity)
- 모든 웹사이트에서 Javascript가 필요한 것은 아님

# #2 LEARNING HTML

## #2.0 Our First HTML File

- 브라우저는 HTML 파일에 에러가 있다고 말해주지 않고, 늘 컨텐츠를 보여주려 하려는 성질이 있다.

## #2.2 Our First HTML Tag

- 태그는 시작 태그, content, 종료 태그로 나뉜다.
- 종료 태그에는 '/'가 붙는다.
- 모든 태그를 전부 기억하고 외울 필요없다. 어떻게 작동하는지를 이해하면 됨!
- 우리가 코드를 제대로 된 위치에 넣고 이 tag들을 기억한다면 작성돼있는 tag에 맞춰 브라우저가 변경해서 보여준다.

## #2.3 More Tags and Prettier

### List Tag

1. ordered list (순서가 있는 목록)
2. unordered list (순서가 없는 목록)

- 두 태그 다 안에 li (list item) 를 붙여줘야 한다.

## #2.4 Tag Attributes

### A Tag

- a = anchor(닻) = 다른 웹사이트로 이동하는 방법
- 이 태그를 적용하려면 어디로 갈지 말해주는 링크 주소가 필요하다.
  - 이렇게 tag에 추가하는 부가적인 정보를 **attributes(속성)** 이라고 한다.
- A tag의 속성들
  - href(HTTP reference OR hyperlink reference)
    ```html
    <a href="http://google.com">링크</a>
    ```
  - target 속성
    - \_self: 현재 탭에서 열기
    - \_blank: 새 탭에서 열기
    ```html
    <a href="http://google.com" target="_blank">링크</a>
    ```
  - 여기서 주의할 점은 두 속성 모두 a 태그에만 사용할 수 있다.
  - 이처럼 정말 많은 tag에 대해 정말 많은 attribute 들이 있다.

### img Tag

- img 태그는 다른 태그들과 다르게 'self-closing tag(자체 닫기 태그)'여서 닫는 태그가 필요 없다.
  - 태그 사이에 content가 필요없기 때문이다. → 이미지는 이미지일 뿐
- img 태그 속성
  - src
  ```html
  <img src="이미지경로" />
  ```

## #2.5 More Tags and Head

### img Tag

- img 태그 파일 경로를 적을 때 파일의 확장자까지 명시해야 함.
- 이미지 파일이 폴더 안에 있을 경우 폴더 이름도 명시해야 함.
  - 이렇게 적는걸 'path notation(경로 표기법)' 이라고 함.

### HTML 문서 구조 작성법

1. \<!DOCTYPE html>

- 브라우저에게 "이건 html 문서야"라고 알려주는 역할.
- 모든 html 파일 첫번째 줄에 들어감.

2. HTML 태그 열기
3. Head 태그 열기 - 웹사이트의 환경 설정
4. Body 태그 열기 - 우리가 볼 수 있는 content 보여줌

## #2.6 Its All About the Head

### head 태그

- \<html lang="kr">
  - 우리 사이트에서 사용되는 언어가 무엇인지 알려줌으로써 구글, 네이버, bing 같은 검색엔진들에 도움을 준다.
- title 태그: 타이틀
- meta 태그: 부가적인 정보
  - content
  - name
  - 구글이 검색할 때 찾는 태그이므로 중요함
- charset: 브라우저에게 text를 어떻게 그려달라는지 말해준다.
  - 꼭 meta charset="utf-8"을 잊지말고 넣어라. 그렇지 않으면 글자가 깨진다.

## #2.7 More Tags

- html, css, js에 관한 정보를 구글에 검색할 때는 mdn 이라는 키워드를 포함시켜서 검색하면 좋다. (ex. html tags mdn)
- **모든 태그를 암기하려 하지말고 직접 구글링해서 태그의 이름과 속성들이 어떻게 쓰이는지 보고, 이해하고, 참고해라.**

## #2.8~.2.9 Form Tags and IDs.

- label Tag
  - label은 input과 함께 작동해야함
  - label에는 'for' 속성, input에는 'id' 속성을 사용한다. (두 개의 값이 동일해야함)
- id는 body 안에 어떤 태그에든 넣을 수 있는 attibute다.
  - id가 중요한 이유는 unique identifier(고유 식별자)기 때문이다
  - element당 하나의 id만 가질 수 있다.
  - scripting이나 css를 식별하려는 목적을 가진게 id이다.

## #2.10 Semantic HTML

- 문서를 보기만해도 그 의미를 짐작할 수 있는 태그를 **시맨틱(semantic) 태그** 라고 한다.

1. 의미가 없는 논시맨틱 태그 (Non-Semantic Tag)
   - div 태그
     - div는 division(분할, 구분, 경계선) 이라는 단어에서 나옴
     - div = 박스
2. 의미가 있는 시맨틱 태그 (Semantic Tag)
   - header
   - main
   - footer

- 옛날에는 div를 떡칠해서 웹페이지를 구성했지만, 요즘에는 시맨틱 태그를 이용하여 웹페이지를 만든다.
  - 시맨틱 태그를 이용하면 코드 이해가 더 빨라져서 좋다. (검색엔진, 프로그래머 모두 이해 가능)
- **항상 시맨틱 태그로 작성하려고 노력하자!!**

# #3 LEARNING CSS

## #3.0 How to Add CSS to HTML

- CSS를 적용하는 두 가지 방법

1. 같은 HTML 파일에 HTML 코드와 CSS 코드를 놓는 방법
   - style 태그 사용
     - style 태그는 head 태그 안에 있어야 한다.
2. CSS와 HTML을 분리하는 것 (추천!)
   - style.css 파일 생성
     - head에 link 태그를 이용해 파일을 연결하고, html과 css의 파일 관계를 rel 속성으로 명시한다.
     ```html
     <link href="style.css" rel="stylesheet" />
     ```

## #3.1 Writing Our First CSS Lines

- CSS는 HTML을 가리키는 것 → 가리키는 것을 selector 라고 부른다.
- 선택자의 글씨체, 색깔, 글자 크기 등을 가리키는걸 "속성" 이라고 한다.
- 속성들을 묶어주기 위해서 curly bracket(중괄호) 를 사용

## #3.2 What Does Cascading Mean

- CSS에서 C는 'Cascading'을 뜻한다.
- Cascading Style Sheet 란 브라우저가 CSS 코드를 읽을 때 위에 있는 코드부터 차례차례 읽힌다는 것!
- 즉, 나중에 적힌 코드의 스타일을 적용한다.

## #3.3 Blocks and Inlines

### Block 개념

- 모든 웹사이트들은 Box로 이루어짐.
- 박스 옆에는 다른 요소가 올 수 없음
- ex) div, header, main, section, footer, article 등

### inline 개념

- 옆에 다른 요소가 올 수 있음
- ex) span, link, image

## #3.4 Margin Part One

- display 속성을 이용하면 block과 inline 전환이 가능하다.
  - inline
  - block
- inline은 높이와 너비가 없다 → 박스가 아니다!
- block은 높이와 너비가 있다.
- block만 가지고 있는 특성

  - block은 박스고 세가지 특성이 있다.
    - margin
    - padding
    - border

- 브라우저는 요소들에게 많은 style 속성을 준다. (원하지 않아도!)
  - ex. h1 태그, 요소와 요소 사이의 빈 공간
    > 크롬에서 확인 가능하다. (user agent stylesheet)

### margin

- margin은 box의 border(경계)의 바깥에 있는 공간

## #3.5 Margin Part Two

- margin: 크기1 크기2 크기3 크기4
  - 위, 오른쪽, 아래, 왼쪽 순으로 마진을 부여 → 시계 방향!!

### Collapsing margins

- Collapsing margins는 마진 상쇄 현상이라고 부른다.
  - box와 box의 경계가 같다면 두 마진은 하나로 취급한다.
  - 단, 위 아래에서만 일어나고 왼쪽, 오른쪽에서는 일어나지 않는다.

## #3.6 Paddings and IDs

### Padding

- box의 경계로부터 '안쪽'에 있는 공간
- id 속성을 사용하면 같은 태그에 다른 스타일을 줄 수 있다.
  - id를 선택하려면 '#' 뒤에 id명을 쓰면 된다.

## #3.7 Border

### border

- box의 경계(border)
- border 선 종류는 'solid'를 가장 많이 쓴다.
  > 그 외의 선 종류는 'border-style mdn' 검색
- border은 inline과 block 모두에 적용된다.
  > '\*'는 전체 태그를 선택하는 선택자이다.

## #3.8 Classes

- inline에서 padding은 사방에 다 가질수 있는데, 예외로 margin은 좌우로만 가질 수 있다.
  - 만약 위 아래 margin을 적용하고 싶다면 inline 요소들을 block으로 바꿔야 한다.

### class

- 각 selector 간에 쉼표를 넣을 수 있다.
- id는 유니크한 값을 가져야 하는데 불필요하게 값이 반복 될 경우 class를 사용한다.
- class는 여러 요소들에서 쓸 수 있다.
- class selector은 앞에 온점(.)을 붙여준다.
- id는 한 요소에만 스타일을 적용시키는데, style은 여러 개 지정이 가능하다.

## #3.9 Inline Block

- inline은 너비랑 높이를 가질 수 없다.
- 이럴 땐 inline-block을 사용하면 된다.
- 근데 inline-block은 구리다
  - 정체를 알 수 없는 여백, 정해진 형식이 존재하지 않음
- inline-blcok은 Responsive Design(반응형 디자인)을 지원하지 않는다!

## #3.10 Flexbox Part One

- Flex box는 2d(2차원) 레이아웃에서 아주 잘 작동한다.

### 중요한 규칙

1. 자식 요소에는 어떤 것도 적지 말아야한다. (부모 요소에만 명시한다)
2. 주축(main axis)
3. 교차축(cross axis)

![flex](https://i.imgur.com/uOqaswk.png)

- justify-content: 주축 정렬
- align-items: 교차축 정렬

> vh: viewport height<br>
> viewport = screen, 100vh = 화면 전체에 해당

## #3.11 Flexbox Part Two

### flex-direction

- flex 박스의 진행방향
- row(기본값)
- row-reverse
- column
- column-reverse
  - 만약 flex-direction이 column이면 주축은 수직이 되고 교차축은 수평이 된다.

### flex wrap

- flex 박스의 줄 바꿈 여부
- nowrap: 줄 바꿈X(기본값)
- flexbox는 width의 값을 초기값으로만 보고, 모든 요소는 같은 줄에 있게 하기 위해 width를 변경할 수 있다.
- wrap: 줄 바꿈
- wrap-reverse: 줄 바꿈(반대)

> 아주 멋있게 레이아웃을 만들고싶다면 'CSS 마스터클래스' 검색

## #3.12 Fixed

### Fixed

- 요소의 위치를 고정시킨다.
- fixed의 특징은 레이어를 부수고 다른 레이어에 위치 하려한다. (모든 것의 위에 있으려고 한다.)

## #3.13 Relative Absolute

- static: 레이아웃이 박스를 처음 위치하는 곳에 두는 것을 말한다. (기본값)
- relative: element가 처음 위치하는 곳을 기준으로 수정한다.
- absolute: 가장 가까운 relative 부모를 기준으로 이동한다. (만약 없으면, body를 기준으로 옮긴다.)

## #3.14 Pseudo Selectors Part One

### pseudo selectors

- 좀 더 세부적으로 element를 선택해준다.
- last-child: 마지막 자식 선택
- first-child: 첫번째 자식 선택
- nth-child(n): n번째 자식 선택
  - nth-child(even) or nth-child(2n): 짝수 자식 선택
  - nth-child(odd) or nth-child(2n+1): 홀수 자식 선택

## #3.15 Combinators

- 부모 자식: 부모 요소 안에 있는 자식 요소를 선택
- 부모 > 자식: 부모 요소 아래의 자식 요소들을 선택
- 형제1 + 형제2: 형제1과 형제 요소인 바로 다음에 있는 형제2만 선택

## #3.16 Pseudo Selectors Part Two

- 형제1 ~ 형제2: 만약 형제2가 형제1의 형제인데 바로 뒤에 오지 않을 때 사용한다.
- optional, required
- 태그[속성 = "값"]: 속성이 "값"인 태그 선택
- 태그[속성 ~= "값"]: 속성에 "값"이라는 단어를 포함한 태그 선택

## #3.17 States

- :active : 마우스로 클릭했을 때
- :focus : 키보드로 선택되었을 때
- :hover over: 마우스가 대상 위에 있을 때
- :visited: 링크를 클릭할 때
- :focus-within : focused인 자식을 가진 부모 요소에 적용
- state는 태그와 혼합해서 사용 가능하다.

```
태그1:state 태그2 {
  ...
}
```

= 태그1이 state가 되면 태그2 작동

```
태그1:state 태그2:state {
  ...
}
```

- state와 state가 결합하면 두 개 모두 만족해야 두번째 태그가 작동된다.

## #3.18 Recap

- ::placeholder: placeholder 스타일 지정
- ::selection: 요소를 드래그 했을 때 스타일 지정
- ::first-letter: 첫 번째 문자 스타일 지정
- ::first-line: 첫 번째 라인 스타일 지정

## #3.19 Colors and Variables

1. hexadecimal color (16진수 컬러)
2. RGB

### Custom Property

- :root: 모든 document의 뿌리

```css
:root {
  --main-color: #fcce00;
}
```

```css
var(--main-color)
```

# #4 ADVANCED CSS

## #4.0 Transitions part One

- 어떤 상태에서 다른 상태로의 "변화"를 애니메이션으로 만드는 방법
- transition은 state가 없는 요소에 붙어야한다.
- 대상이 무조건 state에도 있어야 한다!

```
transition: 속성 시간 속도
```

## #4.1 Transitions part Two

### ease-in function

- 브라우저에게 애니메이션이 어떻게 변할지 말해준다.
- linear, ease-in, ease-out, ease-in-out, ease

## #4.2 Transformations

- 한 요소를 transform(변형)시킬 수 있다.
- rotate(회전), scale(크기 변경), translate(옮기기), skew(비스듬히 기울기기)
- transform은 box element를 변형시키지 않는다. (margin이나 padding 변화 X)
- transform에 시간을 적용하고 싶으면 transition을 사용하면 된다.

### #4.3 Animations part One

- 애니메이션은 우리가 원하는 만큼 애니메이션을 만들고 재생시킬 수 있다.

```css
@keyframes 이름 {
  from {
    ...;
  }
  to {
    ...;
  }
}
```

```css
@keyframes 이름 {
  0% {
    ...;
  }
  50% {
    ...;
  }
  100% {
    ...;
  }
}
```

### #4.5 Media Queries

- Media query: 오직 CSS만을 이용해서 스크린의 사이즈를 알 수 있는 방법

```css
@media screen and (max-width: 400px) {
  ...
}
- 스크린의 크기가 400px보다 작을 때 CSS 적용
```

- orientation: landscape (가로)
- orientation: portrait (세로)

### #4.6 Media Quries Recap

- min-device-width: 오직 핸드폰에만 적용
- screen, print(프린터)

# #5 GIT AND GITHUB

- git은 어떤 파일이든 수정된 내역을 알 수 있다.
- git은 파일을 계속 추적(Tracking) 하는 것이다.
- github에는 기본적으로 변경 내역을 업로드한다.
- git은 파일 변경내역을 계속해서 추적하는 version control system이고, github는 파일 내역과 파일들을 올려주는 공간이다.

# #5.1 What is Github

- repository: 히스토리를 저장할 저장소
- commit: 시점
- github를 이용해서 파일의 변경사항을 탐색함.
- git은 파일들을 주시하면서 관리해주는 도구, github는 git의 변경내역을 볼 수 있는 사이트

# #6 CLONING TIME

## #6.0 Introduction

- gitignore: 무시하고 싶은 파일 이름을 기록하는 파일

## #6.1 Sign Up Screen Part One

- 기본 파일을 'index.html'로 하는 이유는 대부분의 웹서버가 디폴트로 index.html을 찾아보도록 설정 돼있기 때문이다.
- 클래스 이름을 지정할 때는 흔한 이름 말고 부모와 자식을 같이 명시하도록 지어라.
  - 그렇지 않으면, 나중에 코드를 볼 때 힘들다.
- 주석은 프로그래머만 볼 수 있는 코드를 말한다.

```css
<!-- 아아 -->
```

## #6.2 BEM

### BEM(Block Element Modifier)

- 좀 더 쉽게 읽히는 CSS를 가지는 것 (규칙)
- id와 class를 섞어서 쓰면 나중에 헷갈리기 때문에 오랜 시간 문제를 겪은 프로그래머들이 모든 부분에 class를 작성하기로 함.
- --: 색깔, 크기 등
- \_\_(언더바): 정보

## #6.3 Font Awesome

- 아이콘 사이트 추천: [링크](https://fontawesome.com/)

## #6.5 Status Bar CSS

- justify-content 대신 컨테이너 하나를 중심에 놓는 CSS hack(기술) = '레시피 같은 것'
  - 이상하지만 잘 되는 방법을 찾아서 사람들이 공유한 것

1. 먼저 justify-content를 center로 몰아 넣는다.
2. 모든 column에 width: 33%를 부여한다.
3. 두번째 column에 flex를 넣고 justify-content를 center로 설정
4. 마지막 column에 flex를 넣고
   justify-content를 flex-end로 설정한다.

## #6.6 Sign Up Screen Part Two

- 우리가 원하든 원하지 않든 브라우저가 주는 CSS가 있다.
  - 그래서 reset.css를 작성해서 따로 컨트롤 해주는게 좋다.
- 상단바 같이 모든 페이지에 있는 요소는 따로 파일을 분리시켜서 import 해주는게 더 낫다.
- div 같은 요소가 아니라 p나 span 같은 간단한 텍스트 요소는 text-algin으로 중앙정렬 하는게 좋다.

## #6.8 Log In Form Part Two

### CSS Not 속성

### cursor 속성

- pointer, not allowed, progress 등

### color: inherit;

- 색상을 부모로부터 상속 받는다.

## #6.9 Recap and Forms

- 조금 더 organization하게 CSS 파일들을 관리하고싶으면 Screens 폴더, Components 폴더 등으로 나눠라.
- 그 외에는 reset.css, styles.css, variables,css 등으로 나눈다.

### Form의 아주 중요한 2가지 속성

1. action: 어떤 페이지로 data를 보낼건지 정할 수 있다.
2. method
   - POST: 백엔드 서버에 정보를 전송하는 방식 (강의와는 맞지 않음.)
   - GET: 보안에 취약, 이름과 pw를 GET 방식으로 내보내면 안된다. URL에 포함되어도 상관없는 정보들을 GET 방식으로 내보낸다.

## #6.10 Navigation Bar Part One

- 새로운 스크린을 만들 때 처음부터 다시 만들 필요 없다. 앞에꺼 먼저 복사해서 필요없는걸 지워나간다.
- 코드를 작성할 때 단축키를 이용해라. (ex. nav>ul>li\*4>a)
- styles.css에 import할 때 순서 중요하다.

## #6.16 User Component part One

- 비슷한 구성의 스타일들은 컴포넌트 파일로 만든다.

## #6.23 Find Screen Part Three

- 디자인(보여지는 것) 때문에 대문자가 필요하다면 HTML 코드에서는 소문자로 작성하고 CSS 코드에서 대문자로 바꿔준다.
  - text-transform: uppercase (대문자 변환)
- 독립적인 곳에서는 class 쓸 필요 X, 여러 곳에 지정해야한다? class 사용!

## #6.27 Settings Screen part One

- 아이콘과 글자가 있는 리스트는 ul를 활용해라!

## #6.29 Chat Screen Part Two

- fixed로 고정할 때 항상 width값의 %를 확인하고, top이나 bottom 값을 신경써라!
- 요소가 다른 요소에 겹쳤을 경우 z-index로 해결한다. 클수록 우선순위가 높아진다. (기본값: 0)

## #6.34 Splash Screen Part One

### splash 화면

1. position을 absoulute로 설정한다. (이때, 부모는 body)
2. width, height를 각각 100vh, 100vw로 만든다.
3. top값을 0으로 설정한다.

## #6.35 Splash Screen Part Two

- 애니메이션은 애니메이션 종료 후 디폴트 값으로 돌아가려 한다.

### forwards 속성

- 애니메이션의 마지막 속성값을 유지한다.

### visibility 속성

- 마우스에 걸리지 않게 빠져버린다. (단, html에는 그대로 존재한다. 아예 없애려면 js가 필요하다.)

## #6.37 More Animations

### will-change 속성

- 브라우저에게 렌더링 힌트를 주고 element에 실행되길 기대하는 변화를 명시한다.
- 애니메이션이 불안정할 때 사용한다. (브라우저가 컴퓨터의 그래픽 카드를 이용해서 애니메이션을 가속화 시킨다.)

## #6.38 Animating Chats screen

- focus-within: 내부적으로 focus된 element가 있는지 알 수 있도록 해준다.

## 심도있게 공부해볼 것

- box-sizing
- position
- fixed
- animation
- BEM
- 코드 단축키
