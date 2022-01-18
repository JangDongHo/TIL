![CocoaTalk](https://nomadcoders.co/_next/image?url=https%3A%2F%2Fd1telmomo28umc.cloudfront.net%2Fmedia%2Fpublic%2Favatars%2FkokoaThumbnail_h8OxaLt_WUzjUct.jpg&w=3840&q=75)

> 위 문서는 [노마드코더 코코아톡 클론코딩](https://nomadcoders.co/kokoa-clone/lobby) 강의를 중요하다고 생각하는 내용들을 요약한 것입니다.

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
