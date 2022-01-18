# HTML 기본 문서 만들기

## HTML과 첫 만남

### HTML이란?

- HTML(HyperText Markup Language) = **웹 문서를 만드는 언어**
  - 하이퍼텍스트(HyperText) : 문서를 서로 연결해 주는 링크
  - 마크업(Markup) : 웹 브라우저에 내용을 보여 주는 텍스트, 이미지, 영상 등의 위치를 표시하는 것
- 태그(tag) : 웹 브라우저에서 어느 부분이 제목, 텍스트 또는 표인지 구별할 수 있도록 꼬리표를 단 것

> HTML의 기본 기능은 웹 브라우저에 보여 줄 내용에 마크업하고 문서끼리 링크하는 것이다.

> 마크업 vs 마크다운 차이<br>마크업 언어는 문서가 화면에 표시되는 형식을 나타내거나 데이터의 논리적인 구조를 명시하기 위한 규칙들을 정의한 언어의 일종이다. 데이터를 기술한 언어라는 점에서 프로그래밍 언어와는 차이가 있다.<br>마크다운 언어는 마크업 언어의 일종으로, 존 그루버(John Gruber)와 아론 스워츠(Aaron Swartz)가 만들었다. 온갖 태그로 범벅된 HTML 문서 등과 달리, 읽기도 쓰기도 쉬운 문서 양식을 지향한다.

## HTML 구조 파악하기

```HTML
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8">
    <title>웹 개발 입문</title>
  </head>
  <body>
    <h1>웹 개발 기초</h1>
    <p>HTML</p>
    <p>CSS</p>
    <p>자바스크립트</p>
  </body>
</html>
```

1. `<!DOCTYPE html>`: 현재 문서가 HTML5 언어로 작성한 웹 문서라는 뜻
2. `<html> ~ </html>` : 웹 문서의 시작과 끝을 나타내는 태그. 웹 브라우저가 \<html> 태그를 만나면 \</html>까지 소스를 읽어 화면에 표시한다.
3. `<head> ~ </head>` : 웹 브라우저가 웹 문서를 해석하는 데 필요한 정보를 입력하는 부분
4. `<body> ~ </body>` : 실제로 웹 브라우저 화면에 나타나는 내용

```html
<!DOCTYPE html>
```

### \<!DOCTYPE html> 태그 : 웹 문서의 유형을 지정하는 선언문

- 웹 문서의 첫 부분은 문서 유형을 지정하는 \<!DOCTYPE html> 태그로 시작한다. 웹 브라우저에 현재 문서가 HTML5 문서라고 알려 주는 것!

```html
<html lang="ko"></html>
```

### \<html> 태그 : 웹 문서의 시작을 알림

- \<html> 태그로 웹 문서의 시작을 알리고 \</html>로 웹 문서의 끝을 알린다. 이 사이에 웹 문서 소스를 작성한다.
  > \<html> 태그에서는 lang 속성으로 문서에서 사용할 언어를 지정할 수 있다. 검색 결과 중에서 '한국어로 된 문서'로 범위를 제한할 경우 \<html lang="ko">인 문서를 우선 검색하고, 화면 낭독기에서 웹 문서를 소리 내어 읽어 줄 때 해당 언어에 맞추어 발음이나 억양, 목소리 등을 다르게 할 수 있다.

---

### \<head> 태그 : 웹 브라우저에 문서 정보를 알려줌

- \<head> 영역의 내용은 웹 브라우저가 알야아 할 정보를 입력하는 곳이라, 대부분은 웹 브라우저 화면에는 보이지 않는다.

```html
<meta charset="UTF-8" />
```

- \<meta> 태그 : 문자 세트를 비롯해 문서 정보가 들어가있다.
  - 메타 정보 : '데이터에 관한 데이터' (ex. 책의 메타 정보는 가격, 쪽수, 지은이 등)
  - \<meta> 태그의 가장 중요한 역할은 **화면에 글자를 표시할 때 어떤 인코딩을 사용할지 지정하는 것이다.**
  - **웹 서버는 영어가 기본이므로 화면에 한글로 된 내용을 표시할 때에는 UTF-8이라는 문자 세트를 사용한다고 웹 브라우저에 알려줘야한다!**
  - 그 밖에 웹 사이트의 키워드나 간단한 설명, 제작자 등의 정보를 지정할 수 있다. (이 정보는 검색 엔진에서 사이트를 검색 할 때 참고한다.)

```html
<title>웹 개발 입문</title>
```

- \<title> 태그 : 문서 제목을 나타낸다.
  - \<title> 태그에서 지정하는 내용은 **웹 브라우저의 제목 표시줄에 표시된다.**
  - 해당 페이지의 방문자나 검색 엔진은 제목 표시줄의 제목을 보고 페이지의 전체 내용을 추측한다.

```html
<body>
  <h1>웹 개발 기초</h1>
  <p>HTML</p>
  <p>CSS</p>
  <p>자바스크립트</p>
</body>
```

### \<body> 태그 : 웹 브라우저에 내용을 표시

- \<body>와 \</body> 태그 안에는 실제 웹 브라우저 화면에서 보여 주는 내용을 작성한다.

## HTML 파일 만들기

### 라이브 서버 설치하고 웹 브라우저에서 바로 확인하기

- 비주얼 스튜디오 코드에는 확장 기능이 있어서 필요한 기능을 언제든지 추가해서 편리하게 사용할 수 있다.
- 그 중에서 **라이브 서버**는 비주얼 스튜디오 코드에서 작성한 파일을 웹 브라우저에서 바로 확인할 수 있게 해준다.
- Live Server 설치 -> 편집 창에서 마우스 우클릭 -> Open with Live Server 클릭

### HTML의 기본 구조 자동으로 만들기

- 비주얼 스튜디오 코드에는 HTML의 구조를 자동으로 만들어주는 편리한 기능이 있다.
- 첫 번째 줄에 `!`를 입력한 후 `Tab` 또는 `Enter` 누르기
- 이후, 일부 코드 바꾸고 마무리하기!

## 웹 문서 구조를 만드는 시맨틱 태그

### 시맨틱 태그 알아보기

- HTML의 태그는 그 이름만 봐도 의미를 알 수 있어 **시맨틱(semantic) 태그**라고 한다.
  - \<p> 태그 : 텍스트 단락(paragraph)을 줄임
  - \<a> 태그 : 앵커(anchor)를 줄임
- 우리가 흔히 사용하는 웹 사이트의 디자인은 서로 달라 보여도 구조는 비슷하다. 헤더에는 사이트 제목이나 로고, 본문 영역과 그 외의 내용을 나타내는 사이드 바, 푸터 영역 등이 있다. 그리고 웹 사이트에 따라 한두 영역이 추가되기도 한다.

### 시멘틱 태그가 필요한 이유

웹 문서는 시맨틱 태그를 사용하지 않더라도 만들 수 있고, 사용하든 사용하지 않든 웹 문서에 특별히 차이가 나지 않는다. 그렇다면 왜 시멘틱 태그가 필요한가?

1. 웹 브라우저가 HTML의 소스 코드만 보고도 어느 부분이 제목이고 메뉴이고 본문 내용인지 쉽게 알 수 있기 때문이다.
   - 시각 장애인이 웹 사이트를 이용할 때 쓰는 화면 낭독기 같은 보조 기기에서 사이트의 구조를 제대로 이해할 수 있다.
2. 문서 구조가 정확히 나눠지므로 PC나 모바일으 웹 브라우저와 여러 스마트기기의 다양한 화면에서 웹 문서를 표한하기가 쉬워진다.
3. 인터넷에서 웹 사이트를 검색할 때 필요한 내용을 정확히 찾을 수 있다.
   - 웹 사이트의 본문 내용을 검색해야 한다면 메뉴나 푸터 영역이 아니라 본문 영역 안에서만 검색함.

### 웹 문서 구조를 만드는 주요 시맨틱 태그

```HTML
    <header>
      <div id="logo">
        <a href="index-footer.html">
          <h1>Dream Jeju</h1>
        </a>
      </div>
      <nav>
        <ul id="topMenu">
          <li><a href="#">단체 여행</a></li>
          <li><a href="#">맞춤 여행</a></li>
          <li><a href="#">갤러리</a></li>
          <li><a href="#">문의하기</a></li>
        </ul>
      </nav>
    </header>
```

- 헤더 영역을 나타내는 \<header> 태그
  - 말 그대로 헤더 영역을 의미. 사이트에서 헤더는 주로 맨 위 쪽이나 왼쪽에 있으며, 검색 창이나 사이트 메뉴를 삽입한다.
- 내비게이션 영역을 나타내는 \<nav> 태그
  - 같은 웹 문서 안에서 다른 위치로 연결하거나 다른 웹 문서로 연결하는 링크를 만든다.
  - 웹 문서의 위치에 영향을 받지 않으므로 헤더나 푸터, 사이드 바 안에 포함할 수도 있고 독립해서 사용할 수도 있다.
  - 웹 문서에 \<nav> 태가그 여러개 일 경우 각각 id 속성을 지정하면 내비게이션마다 다른 스타일을 적용할 수 있다.

```html
(... 생략 ...)
<main class="contents">
  <section id="headling">
    <h2>몸과 마음이 치유되는 섬</h2>
    ....
  </section>
  <section id="activity">
    <h2>다양한 액티비티가 기다리는 섬</h2>
    ....
  </section>
</main>
```

- 핵심 콘텐츠를 담는 \<main> 태그
  - 웹 문서에서 핵심이 되는 내용을 넣는다.
  - 웹 문서에서 한번만 사용할 수 있다.
- 독립적인 콘텐츠를 담는 \<article> 태그
  - 웹에서 실제로 보여 주고 싶은 내용을 넣는다.
  - 예를 들어 블로그의 포스트나 뉴스 사이트의 기사처럼 독립된 웹 콘텐츠 항목을 말한다.
  - 문서 안에는 \<article> 태그를 여러 개 사용할 수 있고, 이 안에는 \<section> 태그를 넣을 수도 있다.
- 콘텐츠 영역을 나타내는 \<section> 태그
  - 웹 문서에서 콘텐츠 영역을 나타낸다.

> \<section> 태그와 \<article> 태그가 비슷해 보이기도 한다. 하지만 \<section> 태그는 몇 개의 콘텐츠를 묶는 용도로 사용하고, \<article> 태그는 블로그의 포스트처럼 독립된 콘텐츠로 쓴다. 만약, 단순히 스타일을 적용하려고 콘텐츠를 묶으려면 \<section> 태그 대신 \<div> 태그를 사용한다.

- 사이드 바 영역을 나타내는 \<aside> 태그
  - 본문 내용 외에 왼쪽이나 오른쪽, 혹은 아래쪽에 사이드 바를 만든다.
  - 웹 사이트에서 필수 요소가 아니므로 필요한 경우에만 사용한다.

```html
<footer>
  <section id="bottomMenu">
    <ul>
      <li><a href="#">회사 소개</a></li>
      <li><a href="#">개인정보처리방침</a></li>
      <li><a href="#">여행약관</a></li>
      <li><a href="#">사이트맵</a></li>
    </ul>
  </section>
</footer>
```

- 푸터 영역을 나타내는 \<footer> 태그
  - 웹 문서에서 맨 아래쪽에 있는 푸터 영역을 만든다.
  - 보통 푸터에는 사이트 제작 정보, 저작권 정보, 연락처 등을 넣는다.
  - 또한, 푸터 영역에는 \<header> 태그를 비롯하여 \<section>, \<article> 등 다른 시맨틱 태그를 모두 사용할 수 있다.

```html
<header>
  <div id="logo">
    <a href="index-footer.html">
      <h1>Dream Jeju</h1>
    </a>
  </div>
</header>
```

- 여러 소스를 묶는 \<div> 태그
  - 시맨틱 태그가 나오기 전까지는 \<div> 태그로 헤더나 내비게이션, 푸터 등을 구별했다.
  - \<div id="header">나 \<div class="detail">처럼 id나 class 속성을 사용해서 문서 구조를 만들거나 스타일을 적용할 때 사용한다.
  - 즉, 영역을 구별하거나 스타일로 문서를 꾸미는 것이다.

# 웹 문서에 다양한 내용 입력하기

## 텍스트 입력하기

```html
<h1>레드향</h1>
<h2>레드향 샐러드 레시피</h2>
<h2>상품 구성</h2>
```

### 제목을 나타내는 \<hn> 태그

- 웹 문서에서 제목은 다른 텍스트보다 크고 진하게 표시
- **자주 사용하는 제목 스타일을 미리 태그 형태로 만든 것**
  > \<hn>제목\</hn>
- h는 제목을 뜻하는 heading의 줄임말
- n의 자리에는 1~6의 숫자가 들어가고, 숫자가 작아질 수록 글자 크기가 작아진다.

### 텍스트 단락을 만드는 \<p> 태그, 줄을 바꾸는 \<br> 태그

```html
<h1>레드향</h1>
<p>껍질에 붉은 빛이 돌아 레드향이라 불린다.</p>
<p>
  레드향은 한라봉과 귤을 교배한 것으로 일반 귤보다 2~3배 크고, 과육이 붉고
  통통하다.
</p>
<p>
  비타민 C와 비타민 P가 풍부해 혈액순환, 감기예방 등에 좋은 것으로 알려져 있다.
</p>
```

> \<p>내용\<p><br>\<br>

- \<p> 태그 사이에 텍스트를 입력하면 텍스트 앞뒤로 빈 줄이 생기면서 **텍스트 단락**이 만들어진다.
- 주의할 점은 편집기에서 줄을 바꾸더라도 웹 브라우저에서는 한 줄로 표시된다는 것이다.
- 또한, 텍스트 단락의 내용이 길어서 웹 브라우저에 한 줄로 표시할 수 없을 경우 자동으로 줄이 바뀐다.

```html
<h1>레드향</h1>
<p>껍질에 붉은 빛이 돌아 레드향이라 불린다.</p>
<p>
  레드향은 한라봉과 귤을 교배한 것으로 <br />일반 귤보다 2~3배 크고, 과육이 붉고
  통통하다.
</p>
<p>
  비타민 C와 비타민 P가 풍부해<br />
  혈액순환, 감기예방 등에 좋은 것으로 알려져 있다.
</p>
```

- 원하는 위치에서 줄을 바꾸려면 \<br> 태그를 사용하면 된다.
- \<br> 태그는 단독으로 사용하므로 닫는 태그가 필요없다.

```html
<blockquote>
  비타민 C와 비타민 P가 풍부해<br />
  혈액순환, 감기예방 등에 좋은 것으로 알려져 있다.
</blockquote>
```

### 인용할 때 쓰는 \<blockquote> 태그

- 다른 사람의 말이나 책의 내용을 인용할 때 \<blockquote> 태그로 인용문을 감싸주어야 한다.
  > \<blockquote>인용문\<blockquote>
- 웹 브라우저는 태그 안의 내용을 인용문으로 알고 다른 텍스트보다 약간 들여 쓴다.
- 화면 낭독기에서 웹 문서를 읽어 내려갈 때도 태그 안의 내용을 다른 텍스트와 구분한다.

```html
<p>껍질에 붉은 빛이 돌아 <b>레드향</b>이라 불린다.</p>
<p>
  레드향은 <em>한라봉과 귤을 교배</em>한 것으로<br />일반 귤보다 2~3배 크고,
  과육이 붉고 통통하다.
</p>
<p>
  <i>비타민 C</i>와 <i>비타민 P</i>가 풍부해<br />
  <strong>혈액순환, 감기예방</strong> 등에 좋은 것으로 알려져 있다.
</p>
```

### 텍스트를 굵게 표시하려면 \<strong>, \<b> 태그

- 텍스트를 굵게 표시한다.
  > \<strong>굵게 강조할 텍스트\</strong><br>\<b>굵게 표시할 텍스트\</b>
- \<strong>과 \<b>의 차이
  - \<strong> 태그를 사용하면 화면 낭독기가 그 부분을 강조하여 읽어주고, \<b>를 사용하면 단순히 글자만 굵게 표시된다.

```html
<p>
  레드향은 <em>한라봉과 귤을 교배</em>한 것으로<br />
  일반 귤보다 2~3배 크고, 과육이 붉고 통통하다.
</p>
<p><i>비타민 C</i>와 <i>비타민 P</i>가 풍부해<br /></p>
```

### 기울인 텍스트를 입력해주는 \<em>, \<i> 태그

- 텍스트를 기울여 표시할 때 사용한다.
  > \<em>이탤릭체로 강조할 텍스트\</em><br>\<i>이탤릭체로 표시할 텍스트\</i>
- em은 강조를 뜻하는 emphasis의 줄임말이고, i는 이탤릭체, 즉 기울기체를 뜻하는 italic의 줄임말이다.
- \<em> 태그는 문장에서 흐름상 특정 부분을 강조하고 싶을 때 사용하고, \<i> 태그는 마음속의 생각이나 용어, 관용구 등에 사용한다.
- 다시 말해, \<em> 태그는 문장 중에서 특별히 강조하고 싶은 부분에 사용하고, 단순히 다른 텍스트와 구별하기 위해 기울여서 표시한다면 \<i> 태그를 사용한다.

```html
<p>
  <i>비타민 C</i>와 <i>비타민 P</i>가 풍부해<br />
  혈액순환<sup>1</sup> <ins>또는</ins> 감기예방<sub>2</sub>등에 좋<del
    >은 것으로 알려져 있</del
  >다.
</p>
```

### 그 외의 태그들

- \<abbr> : 줄임말을 표시하고 title 속성을 함께 사용
- \<cite> : 웹 문서나 포스트에서 참고한 내용을 표시
- \<code> : 컴퓨터 인식을 위한 소스 코드
- \<small> : 부가 정보처럼 작게 표시해도 되는 텍스트
- \<sub> : 아래 첨자 표시
- \<sup> : 위 첨자 표시
- \<s> : 취소선 표시
- \<u> : 밑줄 표시
- \<ins> : 공동 작업 문서에서 새로운 내용을 삽입
- \<del> : 공동 작업 문서에서 기존 내용을 삭제

## 목록 만들기

```html
<ol>
  <li>샐러드 채소를 씻고 물기를 제거한 후 준비합니다.</li>
  <li>레드향과 아보카도, 토마토를 먹기 좋은 크기를 썰어둡니다.</li>
  <li>드레싱 재료를 믹서에 갈아줍니다.</li>
  <li>
    볼에 샐러드 채소와 썰어 둔 레드향, 아보카도, 토마토를 넣고 드레싱을 뿌리면
    끝!
  </li>
</ol>
```

### 순서 있는 목록을 만드는 \<oi>, \<li> 태그

- 순서 있는 목록(ordered list)이란 말 그대로 각 항목을 순서대로 나열한 것
- ol은 ordered list의 줄임말, li는 list의 줄임말이다.

```html
<ol type="a">
  <li>샐러드 채소를 씻고 물기를 제거한 후 준비합니다.</li>
  <li>레드향과 아보카도, 토마토를 먹기 좋은 크기를 썰어둡니다.</li>
</ol>
<h4>드레싱 준비</h4>
<ol type="a" start="3">
  <li>드레싱 재료를 믹서에 갈아줍니다.</li>
</ol>
```

- \<ol> 태그의 type, start 속설
  - 순서 있는 목록은 기본적으로 숫자 1, 2, 3, ... 으로 번호를 붙인다.
  - type 속성을 사용하면 영문자나 로마 숫자 등으로 순서를 나타낼 수 있다.
    > "1" : 숫자(기본값)<br>"a" : 영어 소문자<br>"A" : 영어 대문자<br>"i" : 로마 숫자 소문자<br> "I" : 로마 숫자 대문자
  - start 속성을 사용하여 시작 번호를 바꿀 수도 있다.

```html
<ul>
  <li>샐러드 채소를 씻고 물기를 제거한 후 준비합니다.</li>
  <li>레드향과 아보카도, 토마토를 먹기 좋은 크기를 썰어둡니다.</li>
  <li>드레싱 재료를 믹서에 갈아줍니다.</li>
  <li>
    볼에 샐러드 채소와 썰어 둔 레드향, 아보카도, 토마토를 넣고 드레싱을 뿌리면
    끝!
  </li>
</ul>
```

### 순서 없는 목록을 만드는 \<ul>, \<li> 태그

- 순서 없는 목록(unordered list)은 항목의 순서가 중요하지 않을 때 사용한다.
- 순서 없는 목록은 항목 앞에 작은 원이나 사각형을 붙여서 구분하는데 이런 작은 그림을 불릿(bullet)이라 한다.

```html
<h2>상품 구성</h2>
<dl>
  <dt>선물용 3kg</dt>
  <dd>소과 13~16과</dd>
  <dd>중과 10~12과</dd>
</dl>
<dl>
  <dt>선물용 5kg</dt>
  <dd>중과 15~19과</dd>
</dl>
```

### 설명 목록을 만드는 \<dl>, \<dt>, \<dd> 태그

- 설명 목록(description list)이란 이름과 값 형태로 된 목록을 말한다. (마치 사전에서 단어명과 설명이 있는 모습!)
- 설명 목록은 이름(단어명) 부분을 지정하는 \<dt> 태그와 값(설명) 부분을 지정하는 \<dd> 태그로 구성된다.

## 표 만들기

### 표를 만드는 \<table>, \<caption> 태그

- \<table> 태그는 표의 시작과 끝을 알려준다.
- \<caption> 태그는 표 제묵을 붙인다. (표의 위쪽 중앙에 표시)

```html
<table>
  <caption>
    표 제목
  </caption>
</table>
```

### 행을 만드는 \<tr> 태그와 셀을 만드는 \<td>, \<th> 태그

```html
<h2>상품 구성</h2>
<table>
  <caption>
    선물용과 가정용 상품 구성
  </caption>
  <tr>
    <th>용도</th>
    <th>중량</th>
    <th>갯수</th>
    <th>가격</th>
  </tr>
  <tr>
    <td>선물용</td>
    <td>3kg</td>
    <td>11~16과</td>
    <td>35,000원</td>
  </tr>
</table>
```

- \<table> 태그만 작성하면 표가 만들어지지 않는다. 행이 몇 개인지, 각 행에는 셀이 몇 개인지 지정해야 한다.
- \<tr> 태그는 행을 만들고, \<td> 태그는 행 안에 있는 셀을 만든다.

```html
<table>
  <tr>
    <td>1행 1열</td>
    <td>1행 2열</td>
  </tr>
  <tr>
    <td>2행 1열</td>
    <td>2행 2열</td>
  </tr>
</table>
```

- 제목 행에 셀을 만들 때는 \<th> 태그를 사용한다. 이 태그를 사용한 내용은 진하게 표시되고 셀 안에서 중앙에 배열되므로 다른 내용에 비해 눈에 띈다.

```html
<h2>상품 구성</h2>
<table>
  <caption>
    선물용과 가정용 상품 구성
  </caption>
  <thead>
    <tr>
      <th>용도</th>
      <th>중량</th>
      <th>갯수</th>
      <th>가격</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>선물용</td>
      <td>3kg</td>
      <td>11~16과</td>
      <td>35,000원</td>
    </tr>
    ...
  </tbody>
</table>
```

### 표의 구조를 지정하는 \<thead>, \<tbody>, \<tfoot> 태그

- 일부 표에서는 제목이 표시된 셀과 자료가 표시된 셀 외에 표 아래쪽에 합계나 요약 내용을 표시하기도 한다.
- 이런 표는 제목과 본문 그리고 요약이 있는 부분으로 표의 구조를 나누어 놓는 것이 좋다.
- 이때, \<thead>, \<tbody>, \<tfoot> 태그를 사용한다.

```html
    </thead>
    <tbody>
      <tr>
        <td rowspan="2">선물용</td>
        <td>3kg</td>
        <td>11~16과</td>
        <td>35,000원</td>
      </tr>
```

### 행이나 열을 합치는 \<rowspan>, \<colspan> 속성 알아보기

- 행을 합치려면 rowspan 속성을, 열을 합치려면 colspan 속성을 사용해서 몇 개의 셀을 합칠지 지정하면 된다.

```html
<td rowspan="합칠 셀의 개수">셀의 내용</td>
<td colspan="합칠 셀의 개수">셀의 내용</td>
```

### 열을 묶어 주는 \<col>, \<colgroup> 태그

- 특정 열에 배경색을 넣거나 너비를 바꾸려면 원하는 열을 선택할 수 있어야함.
- \<col> 태그는 열을 1개만 지정할 때 사용하고, \<colgroup> 태그는 \<col> 태그를 2개 이상 묶어서 사용한다.

```html
<colgroup>
  <col />
</colgroup>
```

> \<colgroup> 태그에는 닫는 태그가 있지만 \<col> 태그는 없다는 점을 주의하세요.

- \<colgroup>, \<col> 태그는 반드시 \<caption> 태그 다음에 써야한다. 즉, 표의 내용이 시작 되기 전에 열의 상태를 알려 주는 것이다.
- 그리고 \<col> 태그로 사용할 때는 \<colgroup> 태그 안에 \<col> 태그를 포함해 표 전체 열의 개수만큼 \<col> 태그를 넣어야 한다.

```html
<table>
  <caption>
    선물용과 가정용 상품 구성
  </caption>
  <colgroup>
    <col style="background-color:#eee;" />
    <col />
    <col style="width:150px" />
    <col style="width:150px" />
  </colgroup>
  <thead></thead>
</table>
```

- 이때, 같은 스타일 속성을 사용하는 \<col> 태그가 있다면 span 속성을 사용해서 묶어 줄 수 있다.

```html
<table>
  <caption>
    선물용과 가정용 상품 구성
  </caption>
  <colgroup>
    <col style="background-color:#eee;" />
    <col />
    <col span="2" style="width:150px" />
  </colgroup>
  <thead></thead>
</table>
```

## 이미지 삽입하기

### 이미지를 삽입하는 \<img> 태그

```html
<img src="이미지 파일 경로" alt="대체용 텍스트" />
```

- src 속성은 이미지 파일의 경로를 지정하여 웹 브라우저에 알려주는 역할 -> 반드시 있어야함!
- alt 속성은 화면 낭독기 등에서 이미지를 대신하여 읽어 줄 텍스트를 입력한다.
  > 웹에서 사용하는 이미지는 인터넷으로 전송해야 하므로 파일 크기가 크지 않으면서 화질이 좋아아 한다. 주로 JPG(또는 JPEG)나 PNG 파일 형식을 사용한다. 아이콘이나 로고처럼 작은 이미지일 경우에는 GIF 파일을 사용한다.
- 이미지 파일의 경로를 정확하게 입력하지 않으면 이미지가 화면에 나타나지 않는다.

  - 경로란 현재 HTML 문서에서 이미지 파일이 있는 곳까지 어떻게 찾아가야 하는지를 알려준다.
  - 이미지 파일의 경로는 웹 문서 파일의 위치를 기준으로 정해진다.
  - 웹 문서와 이미지 파일이 같은 경로에 있다는 간단히 이미지 파일의 이름만 적으면 된다.

  ```html
  <img src="tangerines.jpg" />
  ```

  - 반면 웹 문서가 있는 폴더에 하위 폴더를 만들고 그 폴더에 이미지 파일이 있다면 src 속성에 하위 폴더와 함께 이미지 파일 이름을 적어야 한다.

  ```html
  <img src="images/tangerines.jpg>
  ```

  - alt 속성을 지정하면 화면 낭독기와 같은 보조기기에서 이미지를 대신해서 읽어줄 텍스트를 함께 넣을 수 있고, 인터넷이 불안정하거나 이미지 파일 경로를 잘못 넣었을 때처럼 이미지를 제대로 표시할 수 없을 경우에 이미지 대신 텍스트가 나타난다.
    - alt 속성에 들어 갈 텍스트는 이미지를 부연 설명하는 것이 아니라 이미지 안에 포함된 텍스트를 알려 주어야 한다. 예를 들어, 쇼핑몰 사이트의 메뉴를 이미지로 삽입할 경우 "메뉴"라고 입력해서는 안되며 "첫 화면", "신상품"처럼 해당 이미지를 클릭했을 때 보여 줄 화면이나 이미지에 적힌 내용을 입력해야 한다.
  - \<img> 태그로 이미지 파일을 삽입하면 원래 이미지 크기대로 표시된다.
    - width 속성은 이미지의 너비를, height 속성은 이미지의 높이를 지정한다.
    - 둘 중 1개만 지정해도 나머지 속성은 비율을 자동으로 계산하여 나타낸다.
    - width와 height 속성에 사용할 수 있는 단위는 퍼센트(%)와 픽셀(px)이 있다.

  ```html
  <p>원래 크기의 이미지</p>
  <img src="images/salad.jpg" alt="레드향" />
  <p>width="50%", height="50%"로 지정한 이미지</p>
  <img src="images/salad.jpg" alt="레드향" width="50%" />
  <p>width="150"으로 지정한 이미지</p>
  <img src="images/salad.jpg" alt="레드향" width="150" />
  ```

  > % : 현재 웹 브라우저 창의 너비와 높이를 기준으로 이미지 크기를 결정한다. (ex. width="50%")

  > px : 이미지의 너비나 높이를 해당 픽셀 크기만큼 표시한다. (ex. widßth="150")

## 오디오와 비디오 삽입하기

### 다양한 멀티미디어 파일을 삽입할 때 쓰는 \<object>, \<embed> 태그

- 오디오 파일 뿐만 아니라 비디오, 자바 애플릿, PDF 등 다양한 멀티미디어 파일을 삽입할 때 사용한다. 웹 문서 안에 다른 문서를 삽입할 때도 사용한다.

```html
<object width="너비" , height="높이" , data="파일"></object>
```

- data 속성에 보여줄 멀티미디어 파일을 지정하고 width, height 속성을 사용해 플레이어의 크기를 지정한다.

```html
<embed src="파일 경로" width="너비" height="높이" />
```

- \<embed> 태그는 HTML 초기 버전부터 사용해서 대부분 브라우저에서 사용할 수 있다.
- src 속성을 사용해 삽입할 멀티미디어 파일을 지정하고, 필요할 경우 width, height 속성으로 플레이어의 너비와 높이를 지정할 수 있다.
- \<embed> 태그에는 닫는 태그가 없다.

### 웹 브라우저에서 지원하는 멀티미디어 파일의 종류

- 비디오 : mp4, webm
- 오디오 : mp3, mp4, m4a

### 오디오와 비디오 파일을 삽입하는 \<audio>, \<video> 태그

- HTML에서 배경 음악이나 효과음 등 오디오 파일을 삽입할 때는 \<audio> 태그를 사용하고, 비디오 파일을 삽입할 때는 \<video> 태그를 사용한다.

```html
<audio src="medias/spring.mp3" controls></audio>
```

```html
<video src="medias/salad.mp4" controls width="700"></video>
```

- 방문자가 음악이나 영상을 재생하거나 멈출 수 있도록 컨트롤 바를 나타내는 controls 속성을 함께 사용한다.
- 비디오 파일의 너빗값을 지정하지 않으면 웹 브라우저에 가득 차게 나타나므로 너빗값을 적절히 지정하는 것이 좋다.
  > 오디오나 비디오 같은 멀티미디어 파일을 바로 재생할 수 없던 과거의 웹 브라우저에서는 플러그 인 프로그램을 사용했다. 하지만 요즘은 대부분 웹 사이트에서 사라졌고, 계속 사라지는 추세이다.

### \<audio>, \<video> 태그의 속성 알아보기

- controls : 플레이어 화면에 컨트롤 바 표시
- autoplay : 오디오나 비디오를 자동으로 실행
- loop : 오디오나 비디오를 반복 재생
- muted : 오디오나 비디오의 소리를 제거
- preload : 페이지를 불러올 때 오디오나 비디오 파일을 어떻게 로딩할 것인지 지정합니다. 사용할 수 있는 값은 auto, metadata, none이다. 기본값은 preload="auto"이다.
- width, height : 비디오 플레이어의 너비와 높이를 지정한다.
- poster="파일 이름" : \<video> 태그에서 사용하는 속성으로 비디오가 재생되기 전까지 화면에 표시될 포스터 이미지를 지정한다.

```html
<audio src="medias/spring.mp3" autoplay loop></audio>
```

```html
<video src="medias/salad.mp4" width="700" autoplay muted loop></video>
```

## 하이퍼링크 삽입하기

### 링크를 삽입하는 \<a> 태그와 href 속성

```html
<a href="링크할 주소">텍스트 또는 이미지</a>
```

- 텍스트 링크는 \<a>와 \</a> 태그 사이에 링크로 만들 텍스트를 입력하고, href 속성에는 텍스트를 클릭하면 연결할 문서의 경로와 파일명을 넣으면 된다.

```html
<div>
  <p><a href="../05/order.html">주문서 작성하기</a></p>
</div>
```

- 이미지 링크는 \<a>와 \</a> 태그 사이에 \<img> 태그를 넣으면 이미지에도 링크를 만들 수 있다.

```html
<a href="../05/order.html"><img src="images/tangerines.jpg" alt="레드향" /></a>
```

- 앞에서 만든 예제의 텍스트나 이미지 링크를 클릭하면 현재 열려 있는 웹 브라우저 창에서 새로운 문서가 나타난다.
  - target 속성에 \_blank를 지정하면 링크를 클릭했을 때 연결된 문서가 새 탭에서 열리게 된다.
    ```html
    <p><a href="../05/order.html" target="_blank">주문서 작성하기</a></p>
    ```

# 입력 양식 작성하기

## 폼 삽입하기

### 웹에서 만나는 폼

- 사용자가 웹 사이트로 정보를 보낼 수 있는 요소는 모두 '폼' 이라고 한다.
- 예를 들면, 아아디와 비밀번호를 입력하는 창이나, 로그인 버튼, 회원가입 버튼 등
- 사용자가 이이디와 비밀번호를 입력 -> 로그인 버튼 클릭 -> 웹 서버로 입력한 정보 전송 -> 서버에서 계정 일치하는지 확인 -> 결과 웹 브라우저로 전송
- 폼과 관련한 작업은 정보를 저장하거나 검색, 수정 하는 것이 대부분인데 모두 데이터베이스를 기반으로 작동한다.
- 즉, 텍스트 박스나 버튼 같은 폼 형태는 HTML 태그로 만들지만, 폼에 입력한 사용자 정보는 ASP나 PHP, JSP 같은 서버 프로그래밍을 이용해 처리한다.

### 폼을 만드는 \<form> 태그

```html
<form [속성="속성값" ]>여러 폼 요소</form>
```

- \<form> 태그의 속성
  - method : 사용자가 입력한 내용을 서버 쪽 프로그램으로 어떻게 넘겨줄 것인지 지정한다. method에서 사용할 수 있는 속성값은 get과 post이다.
    - get : 데이터를 256 ~ 4,096byte까지만 서버로 넘길 수 있다. 주소 표시줄에 사용자가 입력한 내용이 그대로 드러나는 단점이 있다.
    - post : 입력한 내용의 길이에 제한받지 않고 사용자가 입력한 내용도 드러나지 않는다.
  - name : 자바스크립트로 폼을 제어할 때 사용할 폼의 이름을 지정한다.
  - action : \<form> 태그 안의 내용을 정리해 줄 서버 프로그램을 지정한다.
    - 입력한 폼을 서버로 보내기
      ```html
      <form action="register.php">/* 여러가지 폼 요소 */</form>
      ```
  - target : action 속성에서 지정한 스크립트 파일을 현재 창이 아닌 다른 위치에서 열도록 한다.
  - autocomplete : 예전에 입력한 내용을 자동으로 표시해주는 자동 완성 기능 on/off
    ```html
    <form action="" autocomplete="off">/* 여러 폼 요소 */</form>
    ```

### 폼 요소를 그룹으로 묶는 \<fieldset>, \<legend> 태그

- 하나의 폼 안에서 여러 구역을 나누어 표시할 때 \<fieldset> 태그를 사용한다.
  - 예를 들면, 쇼핑몰 사이트의 개인 정보와 배송 정보를 나누어 표시

```html
<fieldset [속성="속성값" ]></fieldset>
```

- \<legend> 태그는 \<fieldset> 태그로 묶은 그룹에 제목을 붙인다.

```html
<fieldset>
  <legend>그룹 이름</legend>
</fieldset>
```

```html
<form action="">
  <fieldset>
    <legend>상품 선택</legend>
  </fieldset>
  <fieldset>
    <legend>배송 정보</legend>
  </fieldset>
</form>
```

### 폼 요소에 레이블을 붙이는 \<label> 태그

- label 태그는 input 태그와 같은 폼 요소에 레이블을 붙일 때 사용한다.
- 레이블(label)이란 입력란 가까이에 붙여 놓은 텍스트를 말한다. (ex. 아아디, 비밀번호)
  - 첫 번째 방법 : 태그 안에 폼 요소 넣기
    ```html
    <label>레이블명<input /></label>
    ```
    ```html
    <label>아이디(6자 이상)<input type="text" /></label>
    ```
  - 두 번째 방법 : 태그와 폼 요소 따로 사용
    - label 태그의 for 속성과 폼 요소의 id 속성을 이용해 서로 연결한다.
    ```html
    <label for="id명">레이블명<input id="id명" /></label>
    ```
    ```html
    <label for="user-id">아이디(6자 이상)</label>
    <input type="text" id="user-id" />
    ```

## 사용자 입력을 위한 input 태그

### 텍스트와 비밀번호를 나타내는 type="text"와 type="password"

- 텍스트 필드는 폼에서 가장 많이 사용하는 요소 (주로 아이디나, 이름, 주소 등 한 줄짜리 일반 텍스트를 입력할 때 사용)
- 비밀번호 필드는 입력하는 내용을 화면에 보여 주지 않아야 하므로 '\*'나 'ㅇ'로 표시한다. (이 점만 제외하면 텍스트 필드와 똑같이 동작하고 같은 속성을 사용)

```html
<input type="text" /> <input type="password" />
```

- 필드에서 사용하는 주요 속성들
  - size : 필드의 길이를 지정한다 즉, 화면에 몇 글자가 보이도록 할 것인지를 지정한다.
  - value : 텍스트 필드 요소가 화면에 표시될 때 텍스트 필드 부분에 보여 주는 내용
  - maxlength : 필드에 입력할 수 있는 최대 문자 수를 지정한다.

```html
<form>
  <fieldset>
    <label>아이디: <input type="text" id="user_id" size="10" /></label>
    <label>비밀번호: <input type="password" id="user_pw" size="10" /></label>
    <input type="submit" value="로그인" />
  </fieldset>
</form>
```

### 다양한 용도에 맞게 입력하는 type="search", type="url", type="email", type="tel"

- type="search" : 검색을 위한 텍스트 필드
- type="url" : 웹 주소를 입력하는 필드 (입력값이 지정한 형식에 맞지 않는다면 웹 브라우저에서 오류 메시지 출력)
- type="email" : 이메일 주소를 입력하는 필드 (입력값이 지정한 형식에 맞지 않는다면 웹 브라우저에서 오류 메시지 출력)
- type="tel" : 전화번호를 나타내는 필드 (전화번호는 지역마다 형식이 다르므로 사용자가 입력한 값이 전화번호인지 아닌지 체크할 수 없음)

```html
<ul id="shipping">
  <li>
    <label for="user-name">이름 </label>
    <input type="text" id="user-name" />
  </li>
  <li>
    <label for="addr">배송 주소</label>
    <input type="text" id="addr" />
  </li>
  <li>
    <label for="mail">이메일</label>
    <input type="email" id="mail" />
  </li>
  <li>
    <label for="phone">연락처</label>
    <input type="tel" id="phone" />
  </li>
</ul>
```

### 체크 박스와 라디오 버튼을 나타내는 type="checkbox", type="radio"

- 체크 박스와 라디오 버튼은 여러 항목 중에서 원하는 항목을 선택할 때 사용하는 폼 요소이다.
- 항목 1개를 선택하려면 라디오 버튼, 2개 이상 선택하려면 체크 박스를 사용한다.

```html
<input type="checkbox" /> <input type="radio" />
```

- 속성
  - value : 선택한 체크 박스나 라디오 버튼을 서버에게 알려 줄 때 넘겨줄 값을 지정한다. 이 값은 영문이거나, 숫자여야 하며 필수 속성이다.
  - checked : 체크 박스나 라디오 버튼의 항목은 처음에 아무것도 선택되지 않은 상태로 화면에 표시되는데, 여러 항목 중에서 기본으로 선택해 놓고 싶은 항목에 사용한다. 속성값은 따로 없다.

```html
<fieldset>
  <legend>상품 선택</legend>
  <p><b>주문할 상품을 선택해 주세요.</b></p>
  <ul>
    <li>
      <label><input type="checkbox" value="s_3" />선물용 3kg</label>
      <input type="number" />개
    </li>
    <li>
      <label><input type="checkbox" value="s_5" />선물용 5kg</label>
      <input type="number" />개
    </li>
    <li>
      <label><input type="checkbox" value="f_3" />가정용 3kg</label>
      <input type="number" />개
    </li>
    <li>
      <label><input type="checkbox" value="f_5" />가정용 5kg</label>
      <input type="number" />개
    </li>
  </ul>
  <p><b>포장 선택</b></p>
  <ul>
    <li>
      <label><input type="radio" name="gift" value="yes" />선물 포장</label>
    </li>
    <li>
      <label
        ><input type="radio" name="gift" value="no" />선물 포장 안 함</label
      >
    </li>
  </ul>
</fieldset>
```

> name 속성은 PHP와 같은 웹 프로그래밍에서 폼 요소를 제어할 때 자주 사용한다. 라디오 버튼에서 하나의 버튼만 선택할 수 있게 하려면 다음과 같이 모든 라디오 버튼의 name값을 똑같이 지정해야 한다.

---

### 숫자 입력 필드를 나타내는 type="number", type="range"

- type="number" : 스핀 박스 숫자 선택 <input type="number">
- type="range" : 슬라이드 막대 숫자 입력 <input type="range">
- 속성
  - min : 필드에 입력할 수 있는 최솟값 지정. 기본 최솟값은 0
  - max : 필드에 입력할 수 있는 최댓값 지정. 기본 최댓값은 100
  - step : 숫자 간격을 지정. 기본값은 1
  - value : 필드에 표시할 초깃값

```html
<ul>
  <li>
    <label><input type="checkbox" value="s_3" />선물용 3kg</label>
    <input type="number" min="0" max="5" />개 (최대 5개)
  </li>
  <li>
    <label><input type="checkbox" value="s_5" />선물용 5kg</label>
    <input type="number" min="0" max="3" value="1" />개 (최대 3개)
  </li>
</ul>
```

```html
<ul>
  <li>
    <label><input type="checkbox" value="f_3" />가정용 3kg</label>
    <input type="range" min="0" max="5" />개 (최대 5개)
  </li>
  <li>
    <label><input type="checkbox" value="f_5" />가정용 5kg</label>
    <input type="range" min="0" max="3" value="1" />개 (최대 3개)
  </li>
</ul>
```

### 날짜 입력을 나타내는 type="date", type="month", type="week"

```html
<input type="date | month | week" />
```

- type="date" : 달력에서 날짜 선택 입력 (yyyy-mm-dd 형식으로 표시)
- type="month" : 달력에서 월 입력 (yyyy-mm 형식으로 표시)
- type="week" : 달력에서 주 입력 (1월 첫째 주를 기준으로 몇 번째 주인지 표시)

### 시간 입력을 나타내는 type="time", type="datetime", type="datetime-local"

```html
<input type="time | datetime | datetime-local" />
```

- type="time" : 폼에서 시간을 입력 (오전/오후, 시, 분)
- type="datetime 또는 type="datetime-local" : 사용자가 엡 문서를 보고 있는 지역에 맞는 날짜와 시간 함께 입력 (yyyy-mm-dd 오전.오후, 시, 분)
  > 날짜나 시간의 범위 제한
  >
  > - min : 범위의 시작 날짜나 시간
  > - max : 범위의 마지막 날짜나 시간 지정
  > - step : 스핀 박스의 화살표를 클릭했을 때 증감시킬 크기 지정
  > - value : 기본적으로 표시할 날짜나 시간 지정

```html
<input type="date" min="2020-02-01" max="2020-02-15" />
```

### 전송, 리셋 버튼을 나타내는 type="submit", type="reset"

- submit은 폼에 입력한 정보를 서버로 전송하는 전송 버튼을 나타낸다.
  - 전송된 정보는 \<form> 태그의 action 속성에서 지정한 폼 처리 프로그램에 넘겨진다.
- reset 버튼은 \<input> 요소에 입력된 모든 정보를 재설정해서 사용자가 입력한 내용을 모두 지운다.
- value 속성을 사용해서 버튼에 표시할 내용을 지정한다.

```html
<input type="submit | reset" value="버튼에 표시할 내용" />
~~~html
<div>
  <input type="submit" value="주문하기" />
  <input type="reset" value="취소하기" />
</div>
```

### 이미지 버튼을 나타내는 type="image"

```html
<input type="image" src="이미지 경로" alt="대체 텍스트" />
```

```html
<fieldset>
  <label>아이디: <input type="text" id="user_id" size="10" /></label>
  <label>비밀번호: <input type="password" id="user_pw" size="10" /></label>
  <input type="image" src="images/login.png" alt="로그인" />
</fieldset>
```

### 기본 버튼을 나타내는 type="button"

- type="button"은 주로 버튼을 클릭해서 자바스크립트를 실행할 때 사용한다. 다음과 같이 value 속성을 사용해 버튼에 표시할 내용을 지정한다.

```html
<input type="button" value="버튼에 표시할 내용" />
```

- 다음 예제는 버튼을 클릭하면 자바스크립트의 window.open() 함수를 실행하는 버튼을 만드는 예제이다.

```html
<form>
  <input
    type="button"
    value="공지 창 열기"
    onclick="window.open('notice.html')"
  />
</form>
```

### 파일을 첨부할 때 사용하는 type="file"

- type="file"로 폼에 파일(사진, 문서)을 첨부할 수 있다.
  - 이 유형을 사용하여 웹 브라우저 화면에 [파일 선택]이나 [찾아보기] 버튼 등이 표시되는데, 이 버튼을 클릭하고 파일을 선택하면 파일이 첨부된다.

```html
<input type="file" />
```

### 히든 필드 만들 때 사용하는 type="hiddden"

- 히든 필드는 화면의 폼에는 보이지 않지만 사용자가 입력을 마치면 폼과 함께 서버로 전송되는 요소이다.
- 사용자에게 굳이 보여 줄 필요는 없지만 관리자가 알아야 하는 정보는 히든 필드로 입력한다.

```html
<input type="hidden" name="이름" value="서버로 넘길 값" />
```

```html
<input type="hidden" name="url" id="url" value="사이트를 통한 직접 로그인" />
<label>아이디: <input type="text" id="user_id" size="10" /></label>
<label>비밀번호: <input type="password" id="user_pw" size="10" /></label>
<input type="submit" value="로그인" />
```

## input 태그의 주요 속성

### 자동으로 입력 커서를 갖다 놓는 autofocus 속성

- autofocus 속성을 사용하면 페이지를 불러오자마자 폼에서 원하는 요소에 마우스 포인터를 표시할 수 있다.

```html
<input type="텍스트-입력-필드" autofocus required />
```

### 힌트를 표시해 주는 placeholder 속성

- 사용자가 텍스트를 입력할 때 입력란에 적당한 힌트 내용을 표시해서 그 필드를 클릭하면 내용이 사라지도록 만들 수 있다. 이렇게 하면 텍스트 필드 앞에 제목을 사용하지 않고도 사용자에게 해당 필드에 어떤 내용을 입력해야 할지 알려 줄 수 있어서 편린하다.

```html
<label for="phone">연락처</label>
<input
  type="tel"
  id="phone"
  placeholder="하이픈 빼고 입력해 주세요.(01012345678)"
  required
/>
```

### 읽기 전용 필드를 만들어 주는 readonly 속성

- 사용자가 입력하지는 못하고 읽게만 하는 읽기 전용 필드를 만든다.

```html
<input type="텍스트-입력-필드" readonly />
```

### 필수 입력 필드를 지정하는 required 속성

- 반드시 입력해야 하는 내용에는 required 속성을 지정해 필수 필드로 만든다.

```html
<label for="phone">연락처</label>
<input
  type="tel"
  id="phone"
  placeholder="하이픈 빼고 입력해 주세요.(01012345678)"
  required
/>
```

## 폼에서 사용하는 여러 가지 태그

### 여러 줄을 입력하는 텍스트 영역 \<textarea> 태그

- 텍스트 영역(textarea): 폼에서 텍스트를 여러 줄 입력하는 영역

```html
<textarea>내용</textarea>
```

- \<textarea> 태그 속성
  - cols: 텍스트 영역의 가로 너비를 문자 단위로 지정한다.
    - 글자 수는 영문자를 기준(대강 한글 1글자는 영문자 2글자)
  - rows: 텍스트 영역의 세로 길이를 줄 단위로 지정한다. 지정한 숫자보다 줄 개수가 많아지면 스크롤막대가 생긴다.

```html
<label for="memo">메모</label>
<textarea id="memo" cols="40" rows="4"></textarea>
```

### 드롭다운 목록을 만들어 주는 \<select>, \<option> 태그

- 사용자가 내용을 직접 입력하지 않고 여러 옵션 중에서 선택하게 하려면 드롭다운 목록을 사용한다.
- 드롭다운 목록은 \<select> 태그와 \<option> 태그를 이용해 표시한다.
- \<select> 태그로 드롭다운 목록의 시작과 끝을 표시하고, 그 안에 \<option> 태그를 사용해 원하는 항목을 추가한다. \<option> 태그에는 value 속성을 이용해 서버로 넘겨주는 값을 지정한다.

```html
<select>
  <option value="값1">내용1</option>
  <option value="값2">내용2</option>
</select>
```

- \<select> 태그 속성
  - size: 화면에 표시할 드롭다운 항목의 개수를 지정한다.
  - multiple: 드롭다운 목록에서 둘 이상의 항목을 선택할 때 사용한다.
- \<option> 태그 속성
  - value: 해당 항목을 선택할 때 서버로 넘겨줄 값을 지정한다.
  - selected: 드롭다운 메뉴를 삽입할 때 기본적으로 선택해서 보여 줄 항목을 지정한다.

```html
<label for="prod1">상품 선택</label>
<select id="prod1">
  <option value="special_3" selected>선물용 3kg</option>
  <option value="special_5">선물용 5kg</option>
  <option value="family_3">가정용 3kg</option>
  <option value="family_5">가정용 5kg</option>
</select>
```

### 데이터 목록 만들어 주는 \<datalist>, \<option> 태그

- 데이터 목록을 사용하면 텍스트 필드에 값을 직접 입력하지 않고 미리 만들어 놓은 값 중에서 선택할 수 있다.
- \<datalist> 태그를 이용해 데이터 목록의 시작과 끝을 표시하고 그 사이에 \<option> 태그를 사용해 각 데이터의 옵션을 표시한다.
- 이때 value 속성을 사용해서 서버로 넘겨줄 값을 지정하는데, 이 값이 텍스트 필드에도 나타난다!

```html
<input type="text" list="데이터 목록" id="" />
<datalist id="데이터 목록">
  <option value="서버로 넘길 값1">선택 옵션1</option>
  <option value="서버로 넘길 값2">선택 옵션2</option>
</datalist>
```

```html
<label for="prod2">포장 여부 </label>
<input type="text" id="prod2" list="pack" />
<datalist id="pack">
  <option value="package">선물 포장</option>
  <option value="no_package">포장 안 함</option>
</datalist>
```

### 버튼을 만들어 주는 \<button> 태그

- \<buttion> 태그를 이용하여 폼을 전송하거나 리셋하는 버튼을 삽입할 수 있다.

```html
<button type="submit">내용</button>
<button type="reset">내용</button>
<button type="button">내용</button>
```

- \<button> 태그의 type 속성
  - submit: 폼을 서버로 전송한다.
  - reset: 폼에 입력한 내용을 초기화한다.
  - button: 버튼 형태만 만들 뿐 자체 기능은 없다.
- 화면 낭독기로 웹 문서를 읽어 줄 때 \<button> 태그를 만나면 이 부분에 버튼이 있다는 것을 알고 정확히 전달한다.
- \<button> 태그에는 콘텐츠를 포함할 수 있어서 아이콘을 추가하거나 CSS를 이용해 원하는 형태로 꾸밀 수 있다.

```html
<button type="submit">주문하기</button> <button type="reset">취소하기</button>
```
