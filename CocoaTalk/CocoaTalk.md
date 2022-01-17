![CocoaTalk](https://nomadcoders.co/_next/image?url=https%3A%2F%2Fd1telmomo28umc.cloudfront.net%2Fmedia%2Fpublic%2Favatars%2FkokoaThumbnail_h8OxaLt_WUzjUct.jpg&w=3840&q=75)
> 위 문서는 [노마드코더 코코아톡 클론코딩](https://nomadcoders.co/kokoa-clone/lobby) 강의를 요약한 것입니다.
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

# 반응형 웹과 미디어 쿼리
## 반응형 웹 알아보기
### 반응형 웹 디자인이란
- 화면 크기가 다양한 모바일이 계속 쏟아져 나오는데 그때마다 사이트를 따로따로 제작하는 것은 매우 비효율적!
- 이런 점을 고려해서 화면 크기에 '반응'하는 화면 요소를 자동으로 바꾸어 사이트를 구현하는 것이 바로 **반응형 웹 디자인**이다.

### 모바일 기기를 위한 뷰포트
- PC 화면에 맞춰서 제작한 사이트를 모바일 기기에서 확인하면 원래 PC 화면 크기만큼 표시하므로 글자가 아주 작다. 혹은 모바일 기기에 적합한 사이트를 제작했더라도 정작 스마트폰 화면에서 내용을 확인하면 원래 의도한 대로 표시되지 않기도 한다.
- 이것은 웹키트(webkit)를 기반으로 한 모바일 브라우저의 기본 뷰포트 너비가 980px이기 때문이다. 다시 말해 웹 페이지 너비를 스마트폰용인 320px로 맞추어 웹 사이트를 제작하더라도 무조건 980px로 표시하려고 한다.

### 뷰포트 지정하기
- 뷰포트는 \<meta> 태그를 이용해 \<head>와 \</head> 태그 사이에 작성한다.
~~~css
<meta name="viewport" content="속성1=값1", "속성2=값2", ...>
~~~
- 뷰포트의 속성

|종류|설명|사용 가능한 값|기본값|
|:---:|:---:|:---:|:---:|
|width|뷰포트 너비|device-width 또는 크기|브라우저 기본값
|height|뷰포트 높이|device-height 또는 크기|브라우저 기본값
|user-scalable|확대/축소 가능 여부|yes 또는 no<br>(yes는 1로, device-width와 device-height값은 10으로 간주)|yes
|initial-scale|초기 확대/축소 값|1~10|1

- 다음은 가장 많이 사용하는 뷰포트 속성으로 웹 페이지 뷰포트의 너비를 스마트폰 화면 너비에 맞추고 초기 화면 배율을 1로 지정한다.
~~~html
<meta name="viewport" content="width=deice-width, initial-scale=1">
~~~

### 뷰포트 단위
- 뷰포트 개념이 등장하기 전까지는 CSS에서 크기를 지정할 때 주로 px, %의 단위를 사용했지만 이제는 다음과 같이 뷰포트를 기준으로 하는 단위를 사용할 수도 있다.
  - vw(viewport width): 1vw는 뷰포트 너비의 1%와 같다.
  - vh(viewport height): 1vh는 뷰포트 높이의 1%와 같다.
  - vmin(viewport minimum): 뷰포트의 너비와 높이 중에서 작은 값의 1%와 같다.
  - vmax(viewport maximum): 뷰포트의 너비와 높이 중에서 큰 값의 1%와 같다.
- 예를 들어 뷰포트의 너비가 1000px, 높이가 800px일 경우
  - 1vw = 10px, 1vh = 8px, 1vmin = 8px, 1vmax = 10px