> 해당 문서는 [Svelete 공식 튜토리얼 문서](https://svelte.dev/tutorial/basics) 를 번역한 것입니다.

>주의: 작성자의 영어 실력을 기르기 위해 직접 번역한 부분도 있고, 파파고의 도움을 받은 부분도 있어 오역이 있을 수도 있습니다. 참고하시길 바랍니다.

# 1. 소개
##  a. 기초
Svelete 튜토리얼에 온 것을 환영합니다.
이를 통해 빠르고 작은 웹 애플리케이션을 쉽게 구축하는 데 필요한 모든 것을 배울 수 있습니다. 

또한 API 문서와 예제를 참조할 수 있으며, 로컬에서 컴퓨터 해킹(?)을 시작하기를 원하는 경우 60초 빠른 시작을 참조할 수 있습니다.

## Svelete가 무엇인가요?
Svelete는 빠르게 웹 애플리케이션을 빌딩하기 위한 도구입니다. 

리액트, 뷰와 같은 자바스크립트 프레임워크와 유사하며 매끄러운 인터렉티브 사용자 인터페이스를 쉽게 만들겠다는 목표를 공유한다.

그러나 결정적인 차이가 있습니다. Svelete는 런타임에 애플리케이션 코드를 해석하는 대신 빌드 시 이상적인 JavaScript로 앱을 변환합니다. 이는 프레임워크의 추상화에 대한 성능 비용을 지불하지 않으며, 앱을 처음 로드할 때 위약금이 발생하지 않는다는 것을 의미합니다.

Svelete를 사용하여 전체 앱을 빌드하거나 기존 코드베이스에 점진적으로 추가할 수 있습니다. 또한 기존 프레임워크에 대한 종속성의 오버헤드 없이 어디에서나 작동하는 독립 실행형 패키지로 구성 요소를 제공할 수 있습니다.

## 이 튜토리얼은 어떻게 사용하나요?
너는 Svelete를 이해하기 위해서 HTML, CSS, JavaScript에 대해서 기본적인 친숙함을 가지고 있어야만 한다. 

튜토리얼을 진행하면 새로운 기능을 설명하기 위해 고안된 미니 연습이 표시됩니다. 다음 장에서는 이전 장에서 얻은 지식을 바탕으로 하므로 처음부터 끝까지 살펴보는 것이 좋습니다. 필요한 경우 위의 드롭다운을 탐색할 수 있습니다. ('소개/기본사항' 클릭)

각 튜토리얼 챕터에는 지침에 따라 막힐 경우 클릭할 수 있는 'Show me' 버튼이 있습니다. 너무 많이 의존하지 마십시오. 제안된 각 코드 블록을 어디에 넣어야 하는지 파악하고 편집기에 수동으로 일력하면 더 빨리 배울 수 있습니다.

## 구성요소 이해
Svelete에서는, 애플리케이션이 하나 또는 하나 이상으로 구성됩니다. 구성 요소는 함께 속하는 HTML, CSS, JavaScript를 압축하는 재사용 가능한 자체 포함 코드 블록으로 .svelete 파일로 작성된다. 코드 편집기의 'hello world' 예제는 간단한 구성 요소이다.
___
## b. 데이터 추가하기
정적 마크업을 랜더링하는 구성요소는 딱히 흥미롭지 않습니다. 데이터를 한번 넣어보죠.

먼저, 구성요소에 스크립트 태그를 추가하고 이름 변수를 선언하세요.
~~~html
<script>
	let name = 'world';
</script>

<h1>Hello world!</h1>
~~~
그 후, 우리는 마크업에 이름을 참조할 수 있습니다.
~~~html
<h1>Hello {name}!</h1>
~~~
중괄호 안에 우리가 원하는 자바스크립트를 넣을 수 있습니다. 큰 소리로 인사하기 위해서 name을 name.toUpperCase()로 변경해보십시오.
___
## c. 동적 요소
중괄호를 사용하여 텍스트를 제어할 수 있는 것처럼 중괄호를 사용하여 요소 속성을 제어할 수 있습니다.

이미지에 src가 없습니다. 하나 추가해보겠습니다.
~~~html
<img src={src}>
~~~
훨씬 더 낫군요. 하지만 Svelete는 우리에게 경고를 주고 있습니다.
> A11y: <img> element should have an alt attribute<br>(A11y: <img> 요소에는 alt 속성이 있어야합니다.)

웹 앱을 만들 때 시력이나 동작이 불편한 사람, 좋은 하드웨어나 인터넷 연결이 없는 사람 등 가능한 가장 광범위한 사용자 기반에 액세스 할 수 있는지 확인하는 것이 중요합니다. 접근성(a11y로 줄임)이 항상 쉽게 얻을 수 있는 것은 아니지만, Svelete는 액세스 불가능한 마크업을 쓸 경우 경고함으로써 도움을 줄 것입니다.

이 경우 스크린리더기를 사용하는 사람이나 이미지를 다운로드 할 수 없는 인터넷 연결이 느리거나 끊긴 사람들을 위해 이미지를 설명하는 alt 속성이 누락됐습니다. 하나 추가해봅시다.
~~~html
<img src={src} alt="A man dances.">
~~~
속성 안에 중괄호를 사용할 수 있습니다. "(name) dances"로 변경해보십시오. - \<script> 블록에서 이름 변수를 선언해야 합니다.

## 속기 요소
src={src}와 같이 이름과 값이 동일한 특성을 갖는 것이 일반적입니다. Svelete는 다음과 같은 경우에 대해 편리한 속기법을 제공합니다.
~~~html
<img {src} alt="A man dances.">
~~~
## d.스타일링
HTML처럼, 너의 구성요소에 \<style> 태그를 추가할 수 있다.\<p> 요소에 스타일을 몇가지 추가해보자.
~~~html
<p>This is a paragraph.</p>

<style>
	p {
		color: purple;
		font-family: 'Comic Sans MS', cursive;
		font-size: 2em;
	}
</style>
~~~

중요한 것은, 이러한 규칙의 범위가 구성 요소로 지정 된다는 것입니다. 다음 단계에서 살펴본 바와 같이 앱의 다른곳에서 실수로 \<p> 요소의 스타일을 변경하지 않을 것입니다.
___
## e. 중첩 구성요소
당신의 전체 앱을 하나의 구성요소에 넣는 것은 비현실적일겁니다. 대신 다른 파일에서 컴포넌트를 가져와 요소를 포함한 것처럼 포함시킬 수 있습니다.

Nested.svelte를 가져오는 \<script> 태그를 추가해보자.
~~~html
<script>
	import Nested from './Nested.svelte';
</script>
~~~

그 후 마크업울 추가하자
~~~html
<p>This is a paragraph.</p>
<Nested/>
~~~

비록 Nested.svelte가 \<p>요소를 가지고 있지만, App.svelte의 스타일을 새지 않는다.

또한, Nested 구송 요소 이름은 대문자로 시작됩니다. 이 규칙은 사용자 정의 구성요소와 일반 HTML 태그를 구분할 수 있도록 하기 위해 채택되었습니다.
___
## f. HTML 태그
일반적으로, 문자열을 Plan text로 삽입되는데, 이는 < 와 > 같은 문자는 특별한 의미가 없다는 것을 의미한다.

그러나 HTML을 컴포넌트로 직접 랜더링해야하는 경우도 있다. 예를 들어, 지금 읽고 있는 단어는 HTML 블럽으로 이 페이지에 포함된 마크다운 파일에 존재한다.

Svelte에서는, 특별한 {@html ...} 태그로 할 수 있다.
~~~html
<p>{@html string}</p>
~~~

> Svelte는 DOM에 삽입되기 전에 어떠한 식 정리도 하지 않습니다. 즉, 이 기능을 사용할 경우 신뢰할 수 없는 원본에서 가져온 HTML을 수동으로 이스케이프 하는 것이 중요합니다. 그렇지 않으면 사용자가 XSS 공격에 노출될 위험이 있습니다.
___
## g. 앱 만들기
이 튜토리얼은 구성 요소 작성 프로세스를 익히기 위해 작성되었습니다. 그러나 어느 시점에서는, 자신의 텍스트 편집기에서 편안하게 컴포넌트를 작성하기 시작할 수 있습니다.

먼저, Svelte를 빌드 도구와 통합시켜야 한다. 공식적으로 유지 관리되는 Vite, Rollup, webpack 플러그인이 있습니다.

- vite-plugin-svelte
- rollup-plugin-svelte
- svelte-loader

그리고 다양한 커뮤니티-유지보수 플러그인들까지.

상대적으로 웹 개발을 처음 시작했고 이 도구를 전에 사용해본 적이 없더라도 걱정하지마라. 신규 개발자를 위한 간단한 단계별 가이드인 Svelte를 준비하여 프로세스를 안내합니다.

텍스트 편집기를 구성할 수도 있습니다. 많은 인기 편집자들을 위한 플러그인과 공식 VS 코드 확장이 있다. 편집기에 Svelte 플러그인이 없는 경우 이 안내에 따라 구문 강조 표시를 위해 .svelte 파일을 .html과 동일하게 처리하도록 텍스트 편집기를 구성할 수 있다.

그런 다음 Svelte 컴포너트를 사용함으로써 당신의 프로젝트 설치는 쉽다. 컴파일러는 각 구성요소를 일반 JavaScript 클래스로 변환합니다. 가져온 후 새롭게 인스턴스화하면 된다.
~~~c
import App from './App.svelte';

const app = new App({
	target: document.body,
	props: {
		// we'll learn about props later
		answer: 42
	}
});
~~~

그런 다음 필요하다면 API 컴포넌트를 사용함으로써 앱과 상호작용 할 수 있다.

# 2. 반응성
## a. 배치
Svelte의 중심에는 DOM을 애플리케이션 상태와 동기화하기 위한 강력한 반응성 시스템이 있다. (예: 이벤트에 대한 응답)

그것을 증명하기 위해서, 우리는 먼저 이벤트 핸들러를 연결해야 한다. 9행을 다음과 같이 바꿔봐라.
~~~html
<button on:click={incrementCount}>
~~~

incrementCount 기능 내에서 카운트의 값을 변경하기만 하면 됩니다.
~~~javascript
function incrementCount() {
	count += 1;
}
~~~

Svelte 'instruments'는 DOM을 업데이트 해야한다는 일부 코드를 사용하여 이 과제를 수행합니다.

## b. 선언문
컴포넌트의 상태가 변경되면 Svelte는 DOM을 자동으로 업데이트합니다. 종종 컴포넌트의 상태 중 일부는 다른 부분(예: 이름과 성에서 파생된 전체 이름)으로부터 계산되어야 하며 변경될 때마다 다시 게산되어야 한다.

이것들에 대해, 우리는 반응적인 선언을 한다. 모양은 다음과 같다.
~~~javascript
let count = 0;
$: doubled = count * 2;
~~~
> 이게 조금 이상해 보여도 걱정하지 마라. 유효한 자바스크립트(비관례적인 경우)이며, Svelte는 이를 '참조된 값이 바뀔 때마다 이 코드를 다시 실행'하는 것으로 해석한다. 일단 익숙해지면 되돌아갈 수 없을 것이다.

마크업에 'doubled'를 사용해보자.
~~~html
<p>{count} doubled is {doubled}</p>
~~~
물론 마크업에 {count*2}를 대신 쓰면 된다. 반응형 값은 여러 번 참조해야 하거나 다른 반응형 값에 의존하는 값이 있을 때 특히 유용하다.

## c. 상태
우리는 반응적 가치를 선언하는 데만 제한을 두지 않았으며, 임의의 문장을 반응적으로 실행할 수도 있다. 예를 들어, count의 값이 변화할 때마다 기록할 수 있다.
~~~javascript
$: console.log('the count is ' + count);
~~~
블록을 씌움으로써 문장을 쉽게 그룹화할 수 있습니다.
~~~javascript
$: {
	console.log('the count is ' + count);
	alert('I SAID THE COUNT IS ' + count);
}
~~~
%:를 다음과 같은 if문 앞에 둘 수도 있습니다.
~~~javascript
$: if (count >= 10) {
	alert('count is dangerously high!');
	count = 9;
}
~~~

## d. 배열 및 개체 업데이트
할당에 의해 Svelte의 반응성이 트리거되기 때문에 push 및 splice 같은 배열 방법을 사용해도 자동으로 업데이트 되지는 않는다. 예를 들어, 버튼을 클릭해도 아무것도 작동하지 않는다.

이 문제를 해결하는 한 가지 방법은 중복되지 않는 할당을 추가하는 것이다.

하지만 더 자연스러운 해결책이 있다.
~~~javascript
function addNumber() {
	numbers = [...numbers, numbers.length + 1];
}
~~~

유사한 패턴을 사용하여 pop, shift, unshift, splice를 대체할 수 있다.

배열 및 객체의 속성에 대한 할당(예: obj.foo += 1 또는 array[i] = x)은 값 자체에 대한 할당과 동일한 방식으로 작동한다.
~~~javascript
function addNumber() {
	numbers[numbers.length] = numbers.length + 1;
}
~~~

간단한 경험적 규칙: 업데이트된 변수의 이름이 할당 왼쪽에 표시되어야 한다. 예를 들어...
~~~javascript
const foo = obj.foo;
foo.bar = 'baz';
~~~

ojb.foo.bar에서 obj=obj로 후속 조치를 취하지 않는 한 반응성을 유발하지 않는다.

# 3. Props
## a. Props 선언하기
지금까지, 우리는 내부상태(즉, 주어진 구성요소 내에서 접근이 가능한 값)에서만 독점적으로 다루어 왔다.

실제 응용프로그램에서는 한 구성요소에서 하위 구성요소로 데이터를 전달해야한다. 그러기 위해서는 일반적으로 'props'로 줄여진 속성을 선언할 필요가 있다. Svelte에서는 export 키워드로 한다. Nested.svelte 컴포넌트를 수정해라.

~~~javascript
<script>
	export let answer;
</script>
~~~
> $: 처럼 처음에는 약간 이상하게 느껴질 수 있다. JavaScript 모듈에서는 일반적으로 그렇게 'export'가 작동하지 않는다. 지금은 그냥 가만히 있어. 곧 제2의 천성이 될 거야.

## b. 기본값
'Nested.svelte'에서 속성의 기본값을 쉽게 명시할 수 있다.
~~~javascript
<script>
	export let answer = 'a mystery';
</script>
~~~
이제 'answer' 속성 없이 두 번째 구성요소를 추가하면 해당 구성요소는 기본값으로 돌아간다.
~~~javascript
<Nested answer={42}/>
<Nested/>
~~~

## c. Props 확산
속성 개체가 있는 경우, 각 특성을 명시하는 대신에 구성요소로 확산할 수 있다.
~~~css
<Info {...pkg}/>
~~~
> 반대로, 'export'로 선언되지 않은 것을 포함하여 구성요소로 전달된 모든 요소를 참조해야 하는 경우 '$$props'에 직접 액세스하여 참조할 수 있다. Svelte가 최적화하기 어렵기 때문에 일반적으로 권장하지는 않지만, 드물게 유용하다.

# 4. 논리
## a. if문
HTML은 조건이나 루프처럼 논리를 표현하는 방법이 없다. Svelte는 가능하다.

일부 마크업을 조건부로 렌더링하기 위해, 다음과 같은 if문으로 감싼다.
~~~html
{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{/if}

{#if !user.loggedIn}
	<button on:click={toggle}>
		Log in
	</button>
{/if}
~~~
연습: 구성 요소를 업데이트하고 단추를 클릭한다.

## b. else문
'if user.loggedIn' 및 'if !user.loggdIn' 이 두 조건은 상호 배타적이므로 else문을 사용해서 이 구성요소를 약간 단순화할 수 있다.
~~~html
{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>
{:else}
	<button on:click={toggle}>
		Log in
	</button>
{/if}
~~~
> \# 문자는 항상 블록 열기 태그를 나타낸다. / 문자는 항상 블록 닫힘 태그를 나타낸다. :{:else} 같은 문자는 블록 지속 태그를 나타낸다. 걱정 마라. Svelte가 HTML에 추가하는 구문은 거의 모두 배웠다.

## c. else-if문
다수의 조건은 else if문으로 연결될 수 있다.
~~~html
{#if x > 10}
	<p>{x} is greater than 10</p>
{:else if 5 > x}
	<p>{x} is less than 5</p>
{:else}
	<p>{x} is between 5 and 10</p>
{/if}
~~~

## each문
데이터 리스트를 반복해야 하는 경우 each문을 사용한다.
~~~javascript
<ul>
	{#each cats as cat}
		<li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
			{cat.name}
		</a></li>
	{/each}
</ul>
~~~
>표현식(이 경우 cats)은 배열 또는 배열과 유사한 객체(즉, 길이 속성). 각 [...iterable]을 사용하여 일반적으로 반복 파일을 사용할 수 있다.

다음과 같이 현재 인덱스를 두 번째 인수로 가져올 수 있다.
~~~javascript
{#each cats as cat, i}
	<li><a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
		{i + 1}: {cat.name}
	</a></li>
{/each}
~~~

원하는 경우, 각 cats를 {id, name}로 소거하고 cat.id와 cat.name을 id와 이름으로 바꿀 수 있다.