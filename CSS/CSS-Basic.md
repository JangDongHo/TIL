# CSS의 기본
## 웹 문서에 디자인 입히기
### 왜 스타일을 사용할까?
- 웹 문서에서 스타일이란 HTML 문서에서 자주 사용하는 글꼴이나 색상, 정렬, 각 요소의 배치 방법과 같이 문서의 겉모습을 결정짓는 것을 가리킴.
- 웹 문서의 내용과 상관없이 디자인만 바꿀 수 있다.
- 다양한 기기에 맞게 탄력적으로 바뀌는 문서를 만들 수 있다.
> 크롬 Web Developer 확장 기능을 이용하면 웹페이지의 스타일은 비활성화 시킬 수 있다!

## 스타일과 스타일 시트
### 스타일 형식 알아보기
~~~css
선택자 { 속성1: 속성값1; 속성2: 속성값2 }
~~~
- 선택자: 스타일을 어느 태그에 적용할 것인지 알려주는 것
- 중괄호({}) 사이: 스타일 정보
- 속성과 값이 하나의 쌍으로 이루어진 것을 **스타일 규칙**이라고 함.
- 세미콜론(;)으로 구분해서 스타일 규칙을 여러 개 지정
~~~css
p {
  text-align: center;
  color: blue;
}
~~~
- 스타일을 텍스트 단락에 적용할 것이므로 선택자를 p로 지정
- 중괄호({}) 사이에 텍스트 정렬을 지정하는 text-align 속성과 글자색을 지정하는 color 속성을 사용해서 2개의 스타일 규칙을 만들었다.
- 스타일 속성이 여러 개일 경우 한 줄에 속성을 하나만 적는 것이 이해하기도 편하다.
- 주석 표기: \/* 주!석! */
> CSS 소스는 네트워크를 이용해 파일로 내려받으므로 되도록이면 파일 크기가 작은 것이 좋다. 그래서 CSS 소스가 길면 주석이나 줄 바꿈, 공백 등을 제거하고 꼭 필요한 정보만 남겨서 파일을 작게 만들어 사용하는데 이를 'CSS 소스 경량화(minify)'라고 한다.

### 스타일 시트 알아보기
- 웹 문서 안에서는 스타일 규칙을 여러개 사용하는데, 이런 스타일 규칙을 한눈에 확인하고 필요할 때마다 수정하기도 쉽도록 한군데 묶어 놓은 것을 **스타일 시트**라고 한다.
- 스타일 시트는 크게 웹 브라우저에 기본으로 만들어져 있는 **브라우저 기본 스타일**과 사이트 제작자가 만든 **사용자 스타일**로 나뉜다.
- 사용자 스타일은 다시 **인라인 스타일**과 **내부 스타일 시트**, **외부 스타일 시트**로 나뉜다.

<브라우저 기본 스타일>
- CSS를 사용하지 않은 웹 문서라 하더라도 웹 브라우저에 표시할 때는 기본 스타일을 사용하는데, 이를 **브라우저 기본 스타일**이라고 한다.
- ex) \<h1>, \<p> 등

<간단한 스타일 정보를 적용하는 인라인 스타일>
- 간단한 스타일 정보라면 스타일 시트를 사용하지 않고 스타일을 적용할 대상에 직접 표시하는데, 이를 **인라인 스타일**이라고 한다.
- 적용시키고 싶은 태그에 style 속성을 사용해 **style="속성: 속성값;" 형태로 스타일을 바꿀 수 있다.
~~~html
<p style="color:blue;">껍질에 붉은 빛이 돌아 레드향이라 불린다.</p>
~~~
<스타일을 여러 곳에 적용할 때 쓰는 내부 스타일 시트>
- 웹 문서 안에서 사용할 스타일을 같은 문서 안에 정리한 것은 **내부 스타일 시트**라고 한다.
- 스타일 정보는 웹 문서를 브라우저 화면에 표시하기 전에 결정해야 하므로 모든 스타일 정보는 \<head> 태그 안에서 정의하고 \<style>과 \<style> 태그 사이에 작성한다.
~~~html
<head>
  <meta charset="UTF-8">
  <title>상품 소개 페이지</title>
  <style>
    h1 {      
      padding:10px;
      background-color:#222;
      color:#fff;
    }
  </style>
</head>
~~~

<스타일 정보를 따로 저장해 놓은 외부 스타일 시트>
- 웹 사이트를 만들 때 하나의 웹 문서로 끝나는 경우는 거의 없다. 그래서 여러 웹 문서에서 사용할 스타일을 별도 파일로 저장해 놓고 필요할 때마다 가져와서 사용하는 것이 일반적이다. 이렇게 저장해 놓은 스타일 정보를 **외부 스타일 시트**라고 하고 *.css라는 파일 확장자를 사용한다.
- 외부 스타일 시트 파일에 스타일을 작성할 때는 \<style> 태그를 사용하지 않는다.
- 이렇게 만든 외부 스타일 시트는 웹 문서에 연결해야 스타일이 문서에 적용된다. 외부 스타일 시트를 연결할 때 사용하는 태그는 \<link> 태그이다.
~~~html
<link rel="stylesheet" href="외부 스타일 시트 파일 경로">
~~~
~~~html
<link rel="stylesheet" href="css/style.css">
~~~

## CSS 기본 선택자 알아보기
### 전체 요소에 스타일을 적용하는 전체 선택자
- **전체 선택자**는 말 그대로 스타일을 문서의 모든 요소에 적용할 때 사용한다. 주로 모든 하위 요소에 스타일을 한꺼번에 적용할 때 사용한다.
~~~html
* { 속성: 값; .... }
~~~
- 전체 선택자는 웹 브라우저의 기본 스타일을 초기화할 때 자주 사용한다. (ex. 웹 문서 전체에 마진과 패딩 여백을 0으로 지정한다.)
~~~html
  <style>
    * {
      margin:0;
      padding:0;
    }
~~~
> 태그(tag) vs 요소(element)<br>
\<p>텍스트 단락 지정하기\</p><br>
\<p>: 태그<br>
'텍스트 단락 지정하기': p 요소<br>
\<p> 태그를 적용한 스타일(x), p 요소에 적용하는 스타일(o)

### 특정 요소에 스타일을 적용하는 타입 선택자
- **타입 선택자**는 특정 태그를 사용한 모든 요소에 스타일을 적용한다.
~~~html
태그명 { 스타일 규칙 }
~~~
~~~css
<style>
  p {
    font-style: italic;
  }
</style>
~~~

### 특정 부분에 스타일 적용하는 클래스 선택자
- 같은 태그라도 일부는 다른 스타일을 적용하고 싶다면 **클래스 선택자**를 사용한다.
- 클래스 선택자는 클래스 이름을 사용해서 다른 선택자와 구별하는데, 이때 클래스 이름 앞에 마침표(.)를 반드시 붙인다.
~~~html
.클래스명 { 스타일 규칙 }
~~~
- 클래스 선택자를 사용해 만든 스타일을 **클래스 스타일**이라고 한다.
- 이미 만들어 둔 클래스 스타일을 적용할 때는 태그 안에 class="클래스명"처럼 class 속성을 사용해서 지정한다.
- 클래스 스타일을 2개 이상 적용할 떄는 공백으로 구분해서 스타일 이름을 적으면 된다.
~~~html
<h1 class="accent bg">레드향</h1>
<p>껍질에 붉은 빛이 돌아 <span class="accent">레드향</span>이라 불린다.</p>
~~~

### 특정 부분에 스타일을 한 번만 적용할 수 있는 id 선택자
- **id 선택자**도 클래스 선택자와 마찬가지로 웹 문서의 특정 부분을 선택해서 스타일을 지정할 때 사용한다.
- id 스타일을 웹 요소에 적용할 때는 id="아이디명"처럼 사용한다.
~~~html
#아이디명 { 스타일 규칙 }
~~~
- 클래스 선택자와 id 선택자의 가장 큰 차이는 **클래스 선택자가 문서에서 여러 번 적용할 수 있는 반면, id 선택자는 문서에서 한 번만 적용 할 수 있다는 것**이다.
- id 선택자는 주로 문서의 레이아웃과 관련된 스타일을 지정하거나 웹 요소에서 자바스크립트 프로그램을 사용하면서 요소를 구별할 때 사용한다.
~~~html
<div id="container">
  <h1>레드향</h1>
~~~

### 같은 스타일 규칙을 사용하는 요소들을 묶어주는 그룹 선택자
- 여러 선택자에서 같은 스타일 규칙을 사용하는 경우가 있는데, 이럴 때 쉼표(,)로 구분해 여러 선택자를 나열한 후 스타일 규칙을 한 번만 정의하면 된다.
~~~css
h1, p {
  text-align: center;
}
~~~

## 캐스케이딩 스타일 시트 알아보기
### 캐스케이딩의 의미
- CSS에서 'C'는 캐스케이딩(cascading)의 줄임말이며 스타일 시트에서는 우선순위가 위에서 아래, 즉 계단식으로 적용된다는 의미로 사용한다.
- **CSS에서는 웹 요소에 둘 이상의 스타일을 적용할 때 우선순위에 따라 적용할 스타일을 결정한다.**
- 캐스케이딩은 스타일끼리 충돌하지 않도록 막아 주는 중요한 개념이다.
> 스타일 우선순위: 스타일 규칙의 중요도와 적용 범위에 따라 우선순위가 결정되고, 그 우선순위에 따라 위에서 아래로 스타일을 적용한다.<br>
스타일 상속: 태그의 포함 관계에 따라 부모 요소의 스타일을 자식 요소로, 위에서 아래로 전달한다.

### 스타일 우선순위
- 첫 번째 원칙인 **스타일 우선순위**는 캐스케이딩에서 가장 중요하다.
- 얼마나 중요한가?
  1. 사용자 스타일
  2. 제작자 스타일
  3. 웹 브라우저 기본 스타일
- 적용 범위는 어디까지인가?
  - 중요도가 같은 스타일이라면 스타일 적용 범위에 따라 우선순위를 정함
  1. !important - 어떤 스타일보다 우선 적용하는 스타일
  2. 인라인 스타일
  3. id 스타일
  4. 클래스 스타일
  5. 타입 스타일
- 소스 코드의 작성 순서는 어떠한가?
  - 중요도와 적용 범위가 같다면 스타일을 정의한 소스 순서로 결정
  - 소스에서 나중에 작성한 스타일이 먼저 작성한 스타일을 덮어쓴다.

### 스타일 상속
- 웹 문서에서 사용하는 여러 태그는 서로 포함 관계가 있다.
- 포함하는 태그를 부모 요소, 포함된 태그를 자식 요소라고 한다.
- 스타일 시트에서는 자식 요소에서 별도로 스타일을 지정하지 않으면 부모 요소의 스타일 속성들이 자식 요소로 전달되는데, 이것을 **스타일 상속**이라고 한다.

# 텍스트를 표현하는 다양한 스타일
## 글꼴 관련 스타일
### 글꼴을 지정하는 font-family 속성
- 웹 문서에서 사용할 글꼴은 font-family 속성으로 지정한다.
~~~css
font-family:<글꼴 이름> | [<글꼴 이름>, <글꼴 이름>]
~~~
- 웹 문서에서 지정한 글꼴이 사용자 시스템에 설치되어 있지 않다면 표시X -> 따라서, 글꼴이 없을 경우를 대비해서 두 번째, 세 번째 글꼴까지 생각해야 한다.
  - 글꼴 이름을 2개 이상 지정할 때는 두 글꼴 이름 사이에 쉼표(,)를 넣어 구분한다.
~~~css
body { font-family: "맑은 고딕", 돋움, 굴림 }
~~~
> 텍스트 글꼴을 지정할 때 "맑은 고딕"과 같이 두 단어 이상으로 된 글꼴 이름은 큰따옴표로 묶는다!

### 글자 크기를 지정하는 font-size 속성
- 글자 크기는 font-size 속성을 사용하여 조절할 수 있다. 글자 크기의 단위는 px(픽셀)이나 pt(포인트)등오로 지정할 수 있고 백분율을 사용할 수도 있다.
- 글자 크기의 단위: px(픽셀), pt(포인트), 백분율
~~~css
font-size: <절대 크기> | <상대 크기> | <크기> | <백분율>
~~~
1. 절대 크기: 브라우저에 지정한 글자 크기
2. 상대 크기: 부모 요소의 글자 크기를 기준으로 상대적인 크기를 지정
3. 크기: 브라우저와 상관없이 글자 크기를 직접 지정
4. 백분율: 부모 요소의 글자 크기를 기준으로 백분율(%)로 표시
- <키워드를 사용하여 글자 크기 지정하기>
  - 글자 크기로 사용하도록 미리 약속해 놓은 키워드 중에서 하나를 사용할 수 있다.
  > xx-small < x-small < small < medium < large < x-large < xx-large
  
- <단위를 사용하여 글자 크기 지정하기>
  - CSS에서는 키워드보다 단위를 사용해서 글자 크기를 직접 지정한다.
  - 사용하는 단위는 px(픽셀), pt(포인트), em 등이며 음수값을 사용할 수 없다.
  - 모바일 기기까지 고려해야 하는 요즘에는 em이나 rem을 더 많이 사용! (1em = 16px, 12pt)
    1. em: 부모 요소에서 지정한 글꼴의 대문자 M의 너비를 기준(1em)으로 한 후 비율값 지정
    2. rem: 문서 시작 부분(root)에서 지정한 크기를 기준(1em)으로 한 후 비율값 지정
    3. ex: 해당 글꼴의 소문자 x의 높이를 기준(1ex)으로 한 후 비율값 지정
    4. px: 모니터의 1픽셀을 기준(1px)으로 한 후 비율값 지정
    5. pt: 포인트라고 하며, 일반 문서에서 많이 사용

- <백분율을 사용하여 글자 크기 지정하기
  - 백분율은 부모 요소의 글자 크기를 기준으로 계산하여 지정하는 방법이다.
  - 단, 이때 부모 요소의 글꼴 크기가 font-size 16px처럼 표현되어 있어야 한다!

### 이탤릭체로 글자를 표시하는 font-style 속성
~~~css
font-style: normal | italic | oblique
~~~
- 웹에서는 주로 italic 사용

### 글자 굵기를 지정하는 font-weight 속성
- 미리 만들어진 예약어(normal, bold, bolder)나 숫자값을 사용해 굵기를 지정
~~~html
font-weight: normal | bold | bolder | lighter | 100 | 200 | ...
~~~
- 400: normal, 700: bold (예약어 대신 숫잣값을 사용하면 좀 더 세밀하기 조정 가능)
~~~css
<style>
  body{
    font-size: 20px;   /* 전체 글자 크기 */
  }
  h1 { 
    font-family: 바탕;  /* 글꼴 */
    font-size: 3em;  /* 글자 크기 */
  } 
  .accent {
    font-size:150%;  /* 글자 크기 */
    font-weight: 800;  /* 글자 굵기 */ 
  }
  .italic{
    font-style: italic;  /* 글자 스타일 */
  }
</style>
~~~

## 웹 폰트 사용하기
### 웹 폰트란
- CSS3가 웹 폰트(web font)를 표준으로 채택한 덕분에 사용자 시스템에 없는 글꼴도 사용할 수 있게 됐다.
- 웹 폰트를 사용하려면 웹 문서를 작성할 때 글꼴 정보를 함께 저장해야 한다. 즉, 기존에 가지고 있던 웹 폰트를 사용했다면 서버에 올릴 때 웹 폰트 파일도 함께 업로드 해야한다.
- 웹 폰트를 사용한 사이트에 사용자가 접속하면 웹 문서를 내려받으면서 웹 폰트도 사용자 시스템으로 다운로드 된다.

### 웹 폰트 업로드하고 사용하기
- 컴퓨터에서 사용하는 글꼴은 트루타입(TrueType)이고 파일 확장자는 *.tft이다.
- 트루타입 글꼴은 파일 크기가 커서 웹에 적합X -> 웹에 적합한 글꼴 EOT, WOFF, WOFF2 파일 등장
> 웹 폰트를 변환하는 사이트: [Transfonter](https://transfonter.org)
~~~css
@font-face {
  font-family: <글꼴 이름>;
  src: <글꼴 파일>[<글꼴 파일>, <글꼴 파일>, ...];
}
~~~
- font family 속성: 글꼴 이름 설정 (되도록이면 글꼴 파일 이름과 동일하게!)
- src 속성: 사용할 글꼴 파일의 경로 지정
  - local() 문을 사용해서 사용자 시스템에 글꼴이 있는지 먼저 확인!
  - 만약 없다면 대부분의 모던 브라우저에서 지원하는 WOFF 포맷을 선언한다.
  - TTF 포맷은 다른 파일 형식보다 용량이 커서 TTF 포맷을 그 후에 선언한다.
~~~css
<style>
  @font-face {
    font-family: 'Ostrich';  /* 폰트 이름 */
    src: local('Ostrich Sans'), 
          url('fonts/ostrich-sans-bold.woff') format('woff'), 
          url('fonts/ostrich-sans-bold.ttf') format('truetype'), 
          url('fonts/ostrich-sans-bold.svg') format('svg');
  }
  .wfont {
    font-family:'Ostrich', sans-serif; /* 웹 폰트 지정 */
~~~

## 텍스트 관련 스타일
### 글자색을 지정하는 color 속성
- 제목 등의 텍스트에서 글자색을 바꿀 때는 color 속성을 사용한다.
- color를 사용할 수 있는 속성값은 16진수나 rgb(rgba), hsl(hsla) 또는 색상 이름이다.
~~~css
color: <색상>
~~~
- <16진수로 표현하는 방법>
  - #ffff00처럼 6자리의 16진수로 표현!
  - 앞에서부터 두 자리씩 묶어 #RRGGBB로 표시 (Red, Green, Blue)
  - 00: 색상이 하나도 섞이지 않음 / ff: 해당 색이 가득 섞임
  - #000000(검은색) / #ffffff(흰색)
  - 색상값이 두 자리씩 중복될 경우 생략 가능 (ex. #0000ff = #00f)


- <hsl과 hsla로 표현하는 방법> [참고하면 좋을듯!](http://jun.hansung.ac.kr/CWP/htmls/html%20hsl%20colors.html)
  - hsl은 hue(색상), saturation(채도), lightness(명도)의 줄임말
  - hsal는 hsl에 alpha(불투명도)를 추가한 것
  - 색상은 0도~360도 사이의 색상환으로 표시한다. 0도와 360도는 빨간색, 120도는 초록색, 240도에는 파란색이 배치된다. 그 사이사이에 나머지 색이 배치된다.
  - 채도는 퍼센트(%)로 표시하는데 아무것도 섞이지 않으면 채도가 가장 높은 상태이다.
    - 채도에서는 0%는 회색 톤, 100%는 원래 색으로 표시
  - 명도 또한 퍼센트(%)로 표시하는데 0%는 가장 어둡고 50%는 원래 색으로, 100%는 흰색으로 나타난다.
~~~css
hsl(0, 100%, 50%) = 온전한 빨간색
hsla(0, 100%, 50%, 0.5) = 반쯤 투명한 빨간색
~~~

- <색상을 영문명으로 표기하는 방법>
  - white, black, red와 같이 자주 사용하는 색상일 경우 색상 이름 그대로 사용한다.

~~~css
  <style>
    h1 { 
      color:#0000ff;   /* 16진수 표기법 */
    } 
    p {
      color:green;  /* 색상 이름 */
    }
    .accent {
      color:hsl(0, 100%, 50%);  /* hsl 표기법 */
      font-weight:bold;
    }
  </style>
  ~~~

- <rgb와 rgba로 표현하는 방법>
  - rgb는 red, green, blue의 줄임말
  - 하나도 섞이지 않았을 때는 0으로 표시, 가득 섞였을 때는 255로 표시, 그 사이의 값으로 각 색상의 양을 나타낸다.
  ~~~css
  h1 { color: rgb(0, 0, 255); }
  ~~~
  - rgba에서 a는 불투명도의 값을 나타내고, 0~1의 값 중에서 사용
    - 1은 완전히 불투명한 것, 0.5는 반투명, 0은 완전 투명
  ~~~css
  h1 { color: rgba(0, 0, 255, 0.5); }
  ~~~
  
### 텍스트를 정렬하는 text-align 속성
- text-align 속성은 문단의 텍스트 정렬 방법을 지정한다.
~~~css
text-align: start | end | left | right | center | justify | match-parent
~~~
- start: 현재 텍스트 줄의 시작 위치에 맞추어 문단 정렬
- end: 현재 텍스트 줄의 끝 위치에 맞추어 문단 정렬
- left: 왼쪽에 맞추어 문단 정렬
- right: 오른쪽에 맞추어 문단 정렬
- center: 가운데에 맞추어 문단 정렬
- justify: 양쪽에 맞추어 문단 정렬
- match-parent: 부모 요소를 따라 문단 정렬

### 줄 간격을 조정하는 line-height 속성
- line-height 속상을 이용하여 줄 간격을 원하는 만큼 조절할 수 있다.
- 줄 간격은 정확한 단위로 크깃값을 지정하거나 문단의 글자 크기를 기준으로 몇 배수인지 백분율로 지정할 수도 있다.
- 보통 줄 간격은 글자 크기의 1.5~2배면 적당하다.
~~~css
p { font-size: 12px; line-height: 24px; }
p { font-size: 12px; line-height: 2.0; }
p { font-size: 12px; line-height: 200%; }
~~~
- 텍스트를 세로 정렬할 때에도 line-height 속성을 사용한다.

### 텍스트의 줄을 표시하거나 없애 주는 text-decoration 속성
- text-decoration 속성은 텍스트에 밑줄을 긋거나 취소선을 표시한다.
- 텍스트에 하이퍼링크를 적용하면 기본적으로 밑줄이 생기는데 text-decoration 속성을 사용하면 없앨 수 있다.
~~~css
text-decoration: none | underline | overline | line-through
~~~
- underline: 밑줄 / overline: 윗줄 / line-through: 취소선

### 텍스트에 그림자 효과를 추가하는 text-shadow 속성
- text-shadow 속성은 텍스트에 그림자 효과를 추가해 텍스트를 조금 더 입체감 나게 보여 줄 수 있다.
~~~css
text-shadow: none | <가로 거리> <세로 거리> <번짐 정도> <색상>
~~~
- <가로 거리>: 텍스트로부터 그림자까지의 가로 거리이다. 필수 속성이며, 양숫값은 글자의 오른쪽, 음숫값은 글자의 왼쪽에 그림자를 만든다.
- <세로 거리>: 텍스트로부터 그림자까지의 세로 거리이다. 필수 속성이며, 양숫값은 글자의 아래쪽, 음숫값은 글자의 위쪽에 그림자를 만든다.
- <번짐 정도>: 그림자가 번지는 정도이다. 양숫값을 사용하면 그림자가 모든 방향으로 퍼져 나가므로 그림자가 크게 표시된다. 반대로 음숫값은 그림자가 모든 방향으로 축소되어 보인다. 기본값은 0이다.
- <색상>: 그림자 색상을 지정한다. 한 가지만 지정할 수도 있고 공백으로 구분해 여러 색상을 지정할 수도 있다. 기본값은 현재 글자색이다.
~~~css
  .shadow1 {
    color:red;
    text-shadow:1px 1px black;
  }
  .shadow2 {
    text-shadow:5px 5px 3px #ffa500;
  }
  .shadow3 {
    color:#fff;
    text-shadow:7px -7px 20px #000;
  }
</style>
~~~

### 텍스트의 대소 문자를 변환하는 text-transform 속성
- text-transform 속성은 텍스트를 대소 문자 또는 전각 문자로 변환한다.
- 이 속성은 한글에는 영향을 미치지 않고 영문자에만 적용된다.
- none: 줄을 표시하지 않는다.
- capitalize: 첫 번째 글자를 대문자로 변환
- uppercase: 모든 글자 대문자로 변환
- lowercase: 모든 글자 소문자로 변환
- full-width: 가능한 한 모든 문자를 전각 문자로 변환
> '전각 문자'란 가로와 세로의 길이 비율이 같은 글자를 말한다. '반각 문자'는 가로와 세로의 길이 비율이 1:2인 글자를 말한다.

### 글자 간격을 조절하는 letter-spacing, word-spacing 속성
- letter-spacing 속성은 글자와 글자 사이의 간격을 조절한다.
- word-spacing 속성은 단어와 단어 사이의 간격을 조절한다.
- 이 2가지 속성은 px, em과 같은 단위나 퍼센트(%)로 크깃값을 조절한다.
~~~css
  .spacing1 {
    letter-spacing:0.2em;  /* 글자 간격 0.2em */
  }
  .spacing2 {
    letter-spacing:0.5em;  /* 글자 간격 0.5em */
  }      
</style>
~~~

## 목록 스타일
### 불릿 모양과 번호 스타일을 지정하는 list-style-type 속성
- disc: 채운 원 모양
- circle: 빈 원 모양
- square: 채운 사각형 모양
- decimal: 1부터 시작하는 10진수 (1, 2, 3, ...)
- decimal-leading-zero: 앞에 0이 붙는 10진수 (01, 02, ...)
- lower-roman: 로마 숫자 소문자 (i, ii, iii, ...)
- upper-roman: 로마 숫자 대문자 (I, II, III, ...)
- lower-alpha (또는 lower-latin): 알파벳 소문자 (a, b, c, ...)
- upper-alpha (또는 upper-latin): 알파벳 대문자 (A, B, C, ...)
- none: 불릿이나 숫자를 없앰
~~~css
.book1 {
  list-style-type:none;  /* 불릿 없앰 */
}
.book2 {
  list-style-type: upper-alpha;  /* 알파벳 대문자 */
} 
~~~

### 불릿 대신 이미지를 사용하는 list-style-image 속성
- list-style-image 속성을 이용하면 불릿을 원하는 이미지로 바꿀 수 있다.
- 불릿에 들어갈 이미지는 불릿 크기만큼 작아야 좋다.
~~~css
list-style-image: <url(이미지 파일 경로)> | none
~~~
~~~css
ul {
  list-style-image: url('images/dot.png') /* 불릿으로 사용할 이미지 */
}
~~~

### 목록에 들여 쓰는 list-style-position 속성
- list-style-position 속성을 사용하면 불릿이나 번호의 위치를 들여 쓸 수 있다.
~~~css
list-style-position: inside | outside;
~~~
- inside: 불릿이나 번호를 기본 위치보다 안으로 들여 쓴다.
- outside: 기본값
~~~css
<style>
  .inside { list-style-position: inside; }  /* 목록 들여쓰기 */
</style>
~~~

### 목록 속성을 한꺼번에 표시하는 list-style 속성
- list-style 속성을 사용하면 속성들을 한꺼번에 표시할 수 있다.
~~~css
ul { list-style-type: none; } -> ul { list-style: none; }
ol { list-style-type: lower-alpha; list-style-position: insde; } -> ol { list-style: lower-alpha insde; }
~~~

## 표 스타일
### 표 제목의 위치를 정해 주는 caption-side 속성
~~~css
caption-side: top | bottom
~~~
- top: 캡션을 표 윗부분에 표시. 기본값
- bottom: 캡션을 표 아랫부분에 표

### 표에 테두리를 그려 주는 border 속성
~~~css
border: 크기 solid|dotted 색상
~~~
- solid: 실선
- dotted: 점선
~~~css
<style>
  table {
    caption-side: bottom;  /* 표 캡션 위치 */
    border:1px solid black;  /* 표 테두리는 검은 색 실선으로 */
  }
  td, th {
    border:1px dotted black;  /* 셀 테두리는 검은 색 점선으로 */
    padding:10px;  /* 셀 테두리와 내용 사이의 여백 */
    text-align:center;  /* 셀 내용 가운데 정렬 */
  }
</style>
~~~

### 셀 사이의 여백을 지정하는 border-spacing 속성
- 표와 셀에 따로 테두리를 지정하면 셀과 셀 사이에 여백이 생긴다.
- border-spacing 속성을 사용하면 셀과 셀 사이의 여백을 조절할 수 있다.
~~~css
border-spacing: 수평거리 수직거리
~~~
- 수평 거리의 값과 수직 거리의 값을 공백으로 구분해서 나타내는데, 두 값이 같다면 1개만 지정해도 된다.
> border-spacing은 border-collapse의 값이 separate일 때만 적용된다.

### 표와 셀 테두리를 합쳐 주는 border-collapse 속성
- 표와 셀에 테두리를 지정하면 셀과 셀 사이에 여백이 생긴다.
- collapse: 표와 셀의 테두리를 합쳐 하나로 표시
- separate: 표와 셀의 테두리를 따로 표시. 기본값
- 이 속성은 \<table> 태그에 적용되는 스타일에만 지정하면 된다.
~~~css
<style>
  table {
    caption-side: bottom;  /* 표 캡션 위치 */
    border:1px solid black;  /* 표 테두리는 검은 색 실선으로 */
    border-collapse: collapse;  /* 테두리 한줄로 표시 */
  }
  td, th {
    border:1px dotted black;  /* 셀 테두리는 검은 색 점선으로 */
    padding:10px;  /* 셀 테두리와 내용 사이의 여백 */
    text-align:center;  /* 셀 내용 가운데 정렬 */
  }
</style>
~~~

# 레이아웃을 구성하는 CSS 박스 모델
## CSS와 박스 모델
- CSS 박스 모델이란 웹 문서의 내용을 박스 형태로 정의하는 방법이다.
### 블록 레벨 요소와 인라인 레벨 요소
- 블록 레벨(block-level) 요소: 태그를 사용해 요소를 삽입했을 때 혼자 한 줄을 차지
  - 해당 요소의 너비가 100%라는 뜻
  - 대표적인 태그: \<h1>, \<div>, \<p>
- 인라인 레벨(inline-level) 요소: 콘텐츠만큼만 영역을 차지
  - 대표적인 태그: \<span>, \<img>, \<strong>

### 박스 모델의 기본 구성
- 블록 레벨 요소 = 박스 형태
- 박스 형태인 요소 = **박스 모델(box model) 요소**
- 웹 문서 안에서 여러 요소를 원하는 위치에 배치하려면 CSS 박스 모델을 잘 알고 있어야함
- 박스 모델은 **콘텐츠 영역**, 박스와 콘텐츠 영역 사이의 여백인 **패딩(padding)**, 박스의 **테두리(border)**, 여러 박스 모델 사이의 여백인 **마진(margin)** 등의 요소로 구성된다.

![box-model](https://blog.kakaocdn.net/dn/2c3JM/btqDkAv2s3h/ruswQmTfhWkHhN4rDLCPtK/img.png)

### 콘텐츠 영역의 크기를 지정하는 width, height 속성
- 박스 모델에서 콘텐츠 영역의 크기를 지정할 때 너비는 width, 높이는 height 속성을 사용한다.
- width와 height의 속성값
  - \<크기>: 너비나 높이의 값을 px이나 em 단위로 지정
  - \<백분율>: 박스 모델을 포함하는 부모 요소를 기준으로 너빗값이나 높잇값을 백분율(%)로 지정
  - auto: 박스 모델의 너빗값이나 높잇값이 콘텐츠 양에 따라 자동으로 결정된다. 기본값!

### 박스 모델의 크기를 계산하는 box-sizing 속성
- 실제 박스 모델이 차지하는 크기 = 콘텐츠 영역 + 패딩 + 테두리 두께
- 매번 패딩과 테두리의 값을 계산해서 박스 모델의 크기를 넣어야 한다면 매우 복잡해짐. 그래서 필요한 것이 box-sizing 속성!
  - border-box: 테두리까지 포함해서 너비값을 지정
  - content-box: 콘텐츠 영역만 너빗값을 지정 (기본값)
- 요소의 크기를 쉽게 계산하려면 box-sizing 속성을 border-box로 지정해 놓는 것이 좋다.

### 박스 모델에 그림자 효과를 주는 box-shadow 속성
- 그림자는 이미지 또는 \<div>와 같이 전체 영역에 쩡하여 넣을 수 있다.
~~~css
box-shadow: <수평 거리> <수직 거리> <흐림 정도> <번짐 정도> <색상> inset
~~~
- \<수평 거리>: 그림자가 가로로 얼마나 떨어져 있는지를 나타냄. 필수값이며, 양숫값은 요소의 오른쪽에, 음숫값은 요소의 왼쪽에 그림자를 만든다.
- \<수직 거리>: 그림자가 세로로 얼마나 떨어져 있는지를 나타냄. 필수값이며, 양숫값은 요소의 아래쪽에, 음숫값은 요소의 위쪽에 그림자를 만든다.
- \<흐림 정도>: 0(진한 그림자) / 이 값이 커질수록 부드러운 그림자
- \<번짐 정도>: 양숫값을 사용하면 모든 방향으로 그림자가 퍼짐. 음숫값은 모든 방향으로 그림자가 축소. 기본값은 0
- \<색상>: 한 개 이상의 색상을 지정할 수 있다. 기본값은 검정색
- inset: 안쪽 그림자로 그린다.
~~~css
.box1{ box-shadow:2px -2px 5px 0px;}  /* 오른쪽 윗부분에 그림자 */
.box2{ box-shadow:5px 5px 15px 5px blue;}  /* 오른쪽 아랫부분에 파란색 그림자 */
~~~

## 테두리 스타일 지정하기
### 박스 모델의 방향 살펴보기
- 박스 모델의 방향
  - 맨 윗부분은 top, 오른쪽 right, 아래 bottom, 왼쪽 left
  - top -> right -> bottom -> left 시계 방향!

### 테두리 스타일을 지정하는 border-style 속성
- 테두리 스타일을 지정하는 border-style 속성의 기본값은 none이라, 화면에 표시X
- 따라서, 테두리를 그리려면 가장 먼저 테두리 스타일의 속성값을 지정해야 한다.
  - none: 테두리가 없다. (기본값)
  - hidden: 테두리를 감춘다.
  - solid: 실선
  - dotted: 점섬
  - dashed: 짧은 직선
  - double: 이중선. 두 선 사이의 간격이 border-width값
  - groove, inset, outset, ridge: 테두리를 창에 조각한 것처럼 표시.

### 테두리 두께를 지정하는 border-width 속성
~~~css
border-width: <크기> | thin | medium | thick
~~~
~~~css
#box1 {
  border-width:2px;  /* 네 방향 모두 2px */ 
}
#box2 {
  border-width:thick thin;  /* top & bottom - thick, left & right - thin */
}
#box3 {
  border-width:thick thin thin;  /* top - thick, right - thin, bottom - thin, left - thin */ 
}
#box4 {
  border-width:10px 5px 5px 10px;  /* top - 10px, right - 5px, bottom - 5px, left - 10px */
}
~~~
1. 속성값이 한개. 이 경우에는 4개의 방향 모두 같은 값 적용
2. 속성값이 두개. 첫 번째 값이 위아래 테두리 값, 두번째 값이 좌우 테두리 값 적용
3. 속성값이 세개. top->right->bottom순으로 속성 값 적용. 없는 left는 right 속성과 똑같이 적용.
4. 속성값이 네개. top->right->bottom->left순으로 속성 값 적용.

### 테두리 색상을 지정하는 border-color 속성
~~~css
#box1 { border-color:red;	}  /* 전체 테두리 - 빨강 */
#box2 { 
  border-top-color:blue; /* 위쪽 테두리 - 파랑 */
  border-left-color:red;  /* 왼쪽 테두리 - 빨강 */
~~~

### 테두리 스타일 묶어 지정하는 border 속성
- borer 속성으로 테두리의 스타일과 두께, 색상을 한꺼번에 표현할 수 있다.
~~~css
h1 {
  padding-bottom: 5px;
  border-bottom: 3px solid rgb(75, 70, 70); /* 아래쪽 테두리만 3px짜리 회색 실선*/
}
p {
  padding: 10px;
  border: 3px dotted blue; /* 모든 테두리를 3px짜리 파란 점선 */
}
~~~

### 둥근 테두리를 만드는 border-radius 속성
- border-radius 속성을 사용하면 박스 모델의 테두리를 둥글게 만들 수 있다.
~~~css
border-radius: <크기> | <백분율>
~~~
- 크기: 반지름 크기를 px, em의 단위와 함께 수치로 표현
- 백분율: 현재 요소의 크기를 기준으로 비율(%)로 지정

### 꼭짓점마다 따로 둥글게 처리하기
- 박스 모델에서 꼭짓점 4개를 모두 다르게 지정하고 싶다면 border와 radius 사이에 위치를 나타내는 예약어를 넣어 사용한다.
~~~css
border-top-left-radius:20px;  /* 왼쪽 위 꼭짓점만 둥글게 */
border-top-right-radius:20px;  /* 오른쪽 위 꼭짓점만 둥글제 */
~~~
> border-radius 속성을 사용해서 꼭짓점을 타원 형태로 만들 수도 있다. 이 경우에는 꼭짓점에 원 대신 타원이 있다고 생각한다.<br>
border-radius: \<가로 반지름> / \<세로 반지름>;<br>
border-위치-radius: \<가로 반지름> / \<세로 반지름>;

## 여백을 조절하는 속성
### 요소 주변의 여백을 설정하는 margin 속성
- 마진(margin): 요소 주변의 여백을 의미
~~~css
margin: <크기> | <백분율> | auto
~~~
- 크기: 너빗값이나 높잇값을 px이나 em 같은 단위와 함께 수치로 지정
- 백분율: 박스 모델을 포함한 부모 요소를 기준으로 너빗값이나 높잇값을 퍼센트(%)로 지정
- auto: display 속성에서 지정한 값에 맞게 적절한 값을 자동으로 지정

### margin 속성을 사용하여 웹 문서를 가운데 정렬하기
- margin 속성을 사용해 웹 문서의 내용을 화면의 중앙에 배치하려면 우선적으로 배치할 요소의 너빗값이 정해져 있어야함.
- 그리고 margin-left와 margin-right의 속성값을 auto로 지정 -> CSS는 웹 브라우저 화면의 너비에서 요소 너빗값을 뺀 나머지 영역을 좌우 마진으로 자동 계산한다.
~~~css
#container {
  background-color:#fff;
  width:600px;
  margin:20px auto;
  padding:20px;
}
~~~

### 마진 중첩 이해하기
- 요소를 세로로 배치할 경우에 각 요소의 마진과 마진이 서로 만나면 마진값이 큰 쪽으로 겹쳐지는 문제인데, 이런 현상을 **마진 중첩(margin overlap)** 또는 마진 상쇄(margin collapse)라고 한다.
- 이렇게 된 이유는 여러 요소를 세로로 배치할 때 맨 위의 마진과 맨 아래 마진에 비해 중간에 있는 마진이 지나치게 커지는 것을 방지하기 위한 것이다.
- 마진 중첩은 아래 마진과 위 마진이 서로 만날 때 큰 마진값으로 합쳐지는 것이고, 오른쪽 마진과 왼쪽 마진이 만날 경우에는 중첩되지 않는다.

### 콘텐츠와 테두리 사이의 여백을 설정하는 padding 속성
- 패딩(padding): 콘텐츠 영역과 테두리 사이의 여백
- 패딩을 지정하는 방법은 마진과 거의 같다.

## 웹 문서의 레이아웃 만들기
### 배치 방법 결정하는 display 속성
- display 속성을 사용하면 블록 레벨 요소와 인라인 레벨 여소를 서로 바꿔서 사용할 수 있다.
- 주로 웹 문서의 내비게이션을 만들면서 메뉴 항목을 가로로 배치할 때 많이 사용하고, 이미지를 표 형태로 배치할 수도 있다.
- display 속성값
  - block: 인라인 레벨 요소를 블록 요소로 만든다.
  - inline: 블록 레벨 요소를 인라인 레벨 요소로 만든다.
  - inline-block: 인라인 레벨 요소와 블록 레벨 요소의 속성을 모두 가지고 있고, 마진과 패딩을 지정할 수 있다.
  - none: 해당 요소를 화면에 표시 X
~~~css
  <style>
    * {
      box-sizing: border-box;
    }
    nav ul {
      list-style:none;      
    }
    nav ul li {
      display:inline-block;      
      padding:20px;
      margin:0 20px;
      border:1px solid #222;
    }
  </style>
~~~

## 왼쪽이나 오른쪽으로 배치하는 float 속성
- float 속성은 웹 요소를 문서 위에 떠 있게 만든다.
  - '떠 있다'의 의미는 요소가 왼쪽 구석이나 오른쪽 구석에 배치된다는 것을 말한다.
- float 속성값
  - left: 요소를 문서의 왼쪽에 배치
  - right: 요소를 문서의 오른쪽에 배치
  - none: 좌우 어느 쪽에도 배치 X (기본값)

### float 속성을 해제하는 clear 속성
- float 속성을 사용해 웹의 요소를 왼쪽이나 오른쪽에 배치하면 그다음에 넣는 요소에도 똑같은 속성이 전달된다.
- 따라서 float 속성이 더 이상 유용하지 않다고 알려 주는 속성이 필요한데, 그것이 바로 clear 속성이다.
- clear 속성값
  - left: float left 값을 해제한다.
  - right: float right 값을 해제한다.
  - both: float left, float right 값을 해제한다.

> display : inline-block은 가로로 배치하면서도 기본 마진과 패딩을 가지고 있지만, float: left로 배치하면 가로로 배치될 때 요소에 기본 마진과 패딩이 없다. 그래서 필요하다면 요소마다 마진과 패딩을 지정해주어야 하고, clear 속성으로 플로팅을 해제해야 한다.

## 웹 요소의 위치 지정하기
### 웹 요소의 위치를 정하는 left, right, top, bottom 속성
- 웹 문서에서 요소를 원하는 곳에 갖다 놓을 수 있게 위치를 지정한다.
- 즉, position 속성으로 기준 위치를 정한 뒤 요소의 위치를 left, right, top, bottom 속성에서 선택하고 속성값을 지정하면 된다.
- left: 기준 위치와 요소 사이에 왼쪽으로 얼마나 떨어져 있는지 지정한다.
- right: 기준 위치와 요소 사이에 오른쪽으로 얼마나 떨어져 있는지 지정한다.
- top: 기준 위치와 요소 사이에 위쪽으로 얼마나 떨어져 있는지 지정한다.
- bottom: 기준 위치와 요소 사이에 아래쪽으로 얼마나 떨어져 있는지 지정한다.
~~~css
    #pos1{
      position:absolute;  /* 포지셔닝 - absolute */
      left:50px;  /* 왼쪽에서 50px 떨어지게 */
      top:50px;   /* 위쪽에서 50px 떨어지게 */
    }
    #pos2 {
      position:absolute;  /* 포지셔닝 - absolute */
      right:100px;  /* 오른쪽에서 100px 떨어지게 */
      top:100px;  /* 위쪽에서 100px 떨어지게 */
    }
    #pos3 {
      position: absolute;  /* 포지셔닝 - absolute */
      left:100px;   /* 왼쪽에서 50px 떨어지게 */
      bottom:100px;  /* 아래쪽에서 100px 떨어지게 */
    }
~~~

### 배치 방법을 지정하는 position 속성
- postion 속성을 이용하면 텍스트나 이미지 요소를 나란히 배치할 수도 있고 원하는 위치를 선택할 수 있다.
- position 속성값
  - static: 문서의 흐름에 맞춰 배치한다. (기본값)
  - relative: 위칫값을 지정할 수 있다는 점을 제외하면 static과 같다.
  - absolute: relative값을 사용한 상위 요소를 기준으로 위치를 지정해 배치한다.
  - fixed: 브라우저 창을 기준으로 위치를 지정해 배치한다.
~~~css
  #static {
    position:static;
  }
  #relative-1{
    position:relative;
  }
  #relative-2 {
    position:relative;   /* 포지셔닝 - relative */
    left:100px;  /* 왼쪽에서 100px 떨어지게 */
    top:-50px;   /* 위쪽에서 -50px 떨어지게 (위로 이동) */
  }
  #fixed {
    width:100px;
    height:100px;
    background-color:#222;
    position:fixed;  /* 포지셔닝 - fixed */
    right:30px;  /* 오른쪽에서 30px 떨어지게 */
    top:30px;  /* 위쪽에서 30px 떨어지게 */
  }
</style>
~~~
- 어떤 요소에 position: absolute를 사용하려면 부모 요소에는 position: relative라고 지정해야 원하는 대로 배치할 수 있다.

# 이미지와 그러데이션 효과로 배경 꾸미기
## 배경색과 배경 범위 지정하기
### 배경색을 지정하는 background-color 속성
- 배경색을 지정하려면 배경을 넣고 싶은 요소의 스타일 규칙을 만들 때 backgroud-color 속성을 사용한다.
- 앞에서 설명한 16진수나 rgb값 또는 색상 이름을 사용해서 지정한다.
~~~css
background-color: #008000;
background-color: rgb(0,128,0);
background-color: green;
~~~
- 예외로 background-color값은 하위 요소에 스타일이 상속되지 않는다.

### 배경색의 적용 범위를 조절하는 background-clip 속성
- 박스 모델 관점에서 배경의 적용 범위를 조절할 수 있다.
- background-clip 속성값
  - border-box: 박스 모델의 가장 외곽인 테두리까지 적용한다. (기본값)
  - padding-box: 박스 모델에서 테두리를 뺀 패딩 범위까지 적용한다.
  - content-box: 박스 모델에서 내용(콘텐츠) 부분에만 적용한다.

## 배경 이미지 지정하기
### 웹 요소에 배경 이미지를 넣는 background-image 속성
- 웹 요소에 배경 이미지를 넣을 때 가장 기본으로 알아 둘 속성은 background-image이다.
- 다음 기본형과 같이 url()에 이미지 파일 경로를 넣어서 사용한다.
~~~css
background-image: url('이미지 파일 경로')
~~~
- 이미지 파일은 jpg, gif, png 형식을 사용하며 파일 경로에는 작은따옴표('')나 큰따옴표("")를 붙인다.
- 파일 경로는 현재 웹 문서를 기준으로 상대 경로를 지정할 수도 있고 http:// 로 시작하는 절대 경로를 사용할 수도 있다.
- 배경을 넣을 때 요소보다 이미지 크기가 작으면 이미지가 가로와 세로로 반복되면서 요소의 배경을 가득 채운다.

### 배경 이미지의 반복 방법을 지정하는 background-repeat 속성
- background-repeat 속성을 사용하면 배경 이미지를 가로와 세로 중에서 어떤 방향으로 반복할지 지정하거나, 반복하지 않고 한 번만 나타나게 할 수도 있다.
- background-repeat 속성값
  - repeat: 브라우저 화면에 가득 찰 때까지 가로와 세로로 반복한다. (기본값)
  - repeat-x: 브라우저 화면 너비에 가득 찰 때까지 가로로 반복한다.
  - repeat-y: 브라우저 화면 너비에 가득 찰 때까지 세로로 반복한다.
  - no-repeat: 한 번만 표시하고 반복하지 않는다.

### 배경 이미지의 위치를 조절하는 background-position 속성
- background-position 속성을 이용하면 배경 이미지의 수평 위치 또는 수직 위치의 값을 지정할 수 있다.
~~~css
background-position: <수평 위치> <수직 위치>;
수평 위치: left | center | right | <백분율> | <길이 값>
수직 위치: top | center | bottom | <백분율> | <길이 값>
~~~
- 키워드
  - 배경 이미지의 위치를 지정할 때 가장 많이 사용하는 속성값은 키워드이다.
  - 수평 위치는 left, center, right 중에서 선택할 수 있고 수직 위치는 top, bottom, center 중에서 선택한다.
- 백분율(%)
  - 위치 속성값을 백분율로 표시한다는 것은 요소가 있는 해당 위치에 배경 이미지의 위치를 백분율로 계산하여 맞춘다는 뜻이다.
  - 예를 들어 background-position: 30% 60%; 라면 배경 이미지를 넣을 요소의 왼쪽 모서리로부터 가로 30%, 세로 60%의 위치에 배경 이미지의 가로 세로가 각각 30%, 60%인 위치를 맞춘다.

- 크기
  - 배경 이미지의 위치를 길이로 직접 지정할 수도 있다.
  - 예를 들어 background-image: 30px 20px;이라고 지정하면 가로 30픽셀, 세로 20픽셀의 위치에 배경 이미지의 왼쪽 상단 모서리를 맞춘다.

- 다음 예제는 불릿 대신 배경 이미지 사용하기입니다.
~~~css
<style>
  ul {
    list-style:none;   /* 불릿 없앰 */
    margin-left:-30px;  /* 왼쪽 여백 줄임 */
  }
  li {
    background-image:url('images/book-icon.png');  /* 배경 이미지 파일 */
    background-repeat:no-repeat;  /* 배경 이미지 반복 안함 */
    background-position:left center;  /* 배경 이미지 위치 */
    padding-left:50px;  /* 왼쪽 패딩 (박스 모델) */
    line-height:40px;  /* 줄간격 */
  }
</style>
~~~

### 배경 이미지의 적용 범위를 조절하는 background-origin 속성
- 박스 모델에 패딩이나 테두리가 있다면 배경 이미지를 패딩까지 표시하거나 테두리까지 포함해서 표시할 수도 있다.
- background-origin 속성값
  - content-box: 박스 모델에서 내용 부분에만 배경 이미지를 표시한다. (기본값)
  - padding-box: 박스 모델에서 패딩까지 배경 이미지를 표시한다.
  - border-box: 박스 모델에서 테두리까지 배경 이미지를 표시한다.

### 배경 이미지를 고정하는 background-attachment 속성
- background-attachment 속성을 사용하면 배경 이미지를 고정할 수 있다.
  - scroll: 화면을 스크롤하면 배경 이미지도 스크롤된다. (기본값)
  - fixed: 화면을 스크롤하면 배경 이미지는 고정되고 내용만 스크롤된다.

### background 속성 하나로 배경 이미지 제어하기
- 지금까지 배경 이미지 관련 속성을 background라는 하나의 속성으로 줄여 사용할 수 있다.
~~~css
background: url('images/bg4.png') no-repeat center bottom fixed;
~~~

### 배경 이미지 크기를 조절하는 background-size 속성
- background-size 속성을 사용하여 배경 이미지의 크기를 조절할 수 있다.
- 속성값이 하나라면 그 값은 너비로 인식하고 높이는 원래 이미지의 너비와 높이 비율에 따라 자동 계산한다.
- background-size의 속성값
  - auto: 원래 배경 이미지 크기만큼 표시한다. (기본값)
  - contain: 요소 안에 배경 이미지가 다 들어오도록 이미지를 확대, 축소한다.
  - cover: 배경 이미지로 요소를 모두 덮도록 이미지를 확대, 축소한다.
  - <크기>: 이미지의 너비와 높이를 지정한다. 값이 하나만 주어질 경우 너빗값으로 인식되며, 높잇값은 자동 계산한다.
  - <백분율>: 배경 이미지가 들어갈 요소의 크기를 기준으로 값을 백분율로 지정하고 그 크기에 맞도록 배경 이미지를 확대, 축소한다.