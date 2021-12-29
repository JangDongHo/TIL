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

# 텍스트를 표한하는 다양한 스타일
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