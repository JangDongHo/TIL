> 출처 : [블로그 링크](https://velog.io/@eddy_song/you-can-solve-recursion)

# 재귀가 풀리는 4단계 접근법

## 재귀적으로 생각하지 말자

- 재귀 문제를 쉽게 푸는 방법은 `재귀적으로 생각하지 말 것`
  - 머릿속에 함수 실행 순서를 그리려고 하지 마라!
  - 즉, 처음부터 큰 그림을 머릿속에 그리려고 하지 말고 재귀 함수의 중요한 부분들에만 초점을 맞춰서 문제를 풀어나간다.

## 재귀가 풀리는 4단계 접근법

> 1단계. 재귀를 꼭 써야 하는가?

> 2단계. **베이스 조건**: 답을 바로 알 수 있는 가장 간단한 상황을 생각한다.

> 3단계. **분해**: 베이스 조건에 가까워지도록 인풋값을 조작한다.

> 4단계. **조합**: 부분 답을 가지고 전체 답을 구하는 방법을 생각해본다.

### 1단계. 재귀를 꼭 써야하는가?

> 반복 대신 재귀를 써야하는 경우인지 생각해본다.

- **재귀로 풀 수 있는 문제는 반복으로도 풀 수 있다.**

  - 복잡한 문제를 더 작은 문제로 쪼갠다.
  - 작은 문제를 푸는 작업을 반복한다.
  - 작은 문제의 답을 조합해서 전체 문제를 해결한다.
  - 이게 재귀 알고리즘이다.

- 재귀를 써야하는 경우는, 간단하게 2가지만 기억하자.

#### 1. 재귀적인 자료구조나 풀이 공식이 있을 때

**재귀적인 자료구조**

- 어떤 자료 구조 안에 동일한 자료 구조가 중첩되어있는 형태를 떠올리면 된다.
- 링크드 리스트(linked list)가 대표적이다.
  - 링크드 리스트 안에 있는 포인터가 다음 링크드 리스트를 가리키고, 그 링크드 리스트의 포인터가 또 다음 링크드 리스트를 가리킨다.
- 링크드 리스트, 트리, 그리드, 중첩 배열, JSON, HTML 등이 재귀적인 자료 구조다.
- 이런 자료 구조를 다룰 때는 재귀 알고리즘이 아주 유용하다.

**재귀적인 풀이 공식**

- 답을 구하는 공식이 재귀적인 경우도 있다.

  - 팩토리얼, 피보나치 수열, 순열/조합 등이 있다.

- 이렇게 재귀적인 자료구조나 풀이 공식이 있는 문제는 재귀로 적으면 코드가 깔끔해지고, 방법이 더 명료하게 드러난다.

#### 2. 변수 선언 없이 코딩하고 싶을 때

- 함수형 프로그래밍에서는 변수 선언을 금지한다. 값은 변하지 않는 상수로 선언한다. (불변성)
- 이 경우에는 재귀가 유용하다. 재귀는 함수를 호출할 때마다 새로운 스코프를 생성하기 때문에, 변수 없이도 문제를 풀 수 있다.

문제를 보면 먼저 이 2가지 조건에 해당하는지 확인하자. (대부분은 1번에 해당)

### 2단계. 베이스 조건

> 답을 바로 알 수 있는 가장 간단한 상황을 생각한다.

#### 무조건 베이스 조건부터

- 재귀 함수를 풀 때, 가장 먼저 '베이스 조건'을 떠올려야 한다.
  - `베이스 조건`이란 더 이상 자기 자신을 호출하지 않게 하는 조건이다.
  - 베이스 조건은 재귀 함수에 반드시 있어야 한다. 베이스가 없으면 재귀 함수는 무한히 자기 자신을 호출하게 된다.
- **우리의 목표는 `최대한 재귀적으로 생각하지 않는 것`이다.**
  - 베이스 조건은 **단순한 작업으로, 바로 답을 구할 수 있는, 가장 쉬운 상황**이다.

> 바로 답을 구할 수 있는, 가장 단순한 인풋값은 무엇일까?

#### 0과 1을 활용한 인풋

- 이 때 **가장 간단한 인풋값은 0 혹은 1인 경우가 많다.**
  - 정수 타입이면 0이나 1인 상황
  - 배열이면 배열의 길이가 0인 경우(빈 배열), 1인 경우
  - 트리면 nil인 경우, 혹은 자식 노드가 nil(잎 노드)인 경우
  - m x n 그리드(이차원 배열)이라면, 둘 다 0이거나 둘 중 하나가 1이거나, 둘 다 1인 케이스
- **물론 0과 1이 항상 적절한 베이스 조건인 건 아니다.**

#### 문제에서 요구한 답의 데이터 타입

- 베이스 조건에서 무엇을 return 해야할지 헷갈린다면 **문제에서 요구한 답의 데이터 타입을 보자.**
  - 예를 들어, 트리가 주어지고 트리 안 어떤 경로의 `노드값 총합(정수)`를 구하는 문제다. 그러면 베이스 조건의 결과값은 `정수 타입`이다.
- 문제가 요구하는 데이터 타입과 조건 결과값의 데이터 타입은 같아야 한다. 너무도 당연한 말이지만, 헷갈릴 땐 은근히 좋은 힌트가 된다.

> 다시 한번 강조하지만, **무조건 `베이스 조건`부터 생각**해야 한다. 예시로 주어진 인풋값을 보고, 어떻게 이걸 답으로 만들지? 라고 생각하면 안 된다. 자꾸 함수 실행 순서를 생각하게 되기 때문이다. 최대한 재귀적으로 생각하지 않고, 마치 1차원 문제인 것처럼 푸는 게 우리 전략이다.

### 3단계. 분해

> 베이스 조건에 가까워지도록 인풋값을 조작한다.

#### 재귀적 분해 = 문제를 더 작게 만드는 것

- 재귀 함수가 잘 작동하려면, 함수를 호출할 때마다 베이스 조건에 가까워져야 한다.
  - 자기 자신을 호출할 때, 넣을 인자를 한 단계 더 간단해지도록 조작한다.
  - 예를 들어 n이라는 정수를 인자로 받았다면, 자기 자신을 호출할 때 n-1을 넣는 식이다. 그래야 **재귀를 반복하면서 인풋값이 조금씩 더 간단해진다.**
  - 이걸 영어로 재귀적 분해(Recursive Decomposition)이라고 한다.

#### 분해의 흔한 패턴

- `분해`도 재귀 문제를 많이 풀다보면 비슷한 패턴이 반복된다.
  - 정수 타입이라면 대체로 n-1 혹은 n-2.
  - 배열(문자열)이라면 앞의 숫자 하나를 떼고 길이를 줄인다.
  - 링크드 리스트라면, 포인터가 가리키는 다음 노드, 혹은 다다음 노드를 넣는다.
  - 트리라면, 자식 노드를 하나씩 넣는다. (이진 트리의 경우 재귀 호출을 2번 하는 경우가 많다.)
- 분해라고 해서 꼭 값을 줄이는 건 아니다. 하지만 **계속 분해하다보면 우리가 원하는 베이스 조건에 도달해야 한다.**
- 분해를 어떻게 해야할지 바로 떠오르지 않아도 괜찮다. 문제에 따라서 분해가 상당히 복잡할 수 있다. 일단은 단순하게 가정하고 넘어가라. 어떤 분해가 적절한지 다음 `조합` 단계에서 힌트를 얻는 경우가 많다.

### 4단계. 조합

> 부분 답을 가지고 전체 답을 구하는 방법을 생각한다.

- 조합은 재귀 호출이 베이스 조건에 걸려 멈추고 나서, 그 다음에 일어나는 작업이다.
- 베이스 조건에 도달하고, 거기서부터 마치 감았던 실타래를 풀듯이 결과값들이 차례차례 반환된다.
- 어떻게 하면 조합을 쉽게 생각할 수 있을까?
  - 조합은 부분 답을 조합해서 전체 답을 만드는 과정이다. 재귀 과정 전체의 조합을 생각하지 말고, 특정한 단계를 딱 집어서 본다.
- 그 단계에서 바로 밑의 재귀 호출로 얻은 답을 가지고, 현재 단계의 답을 어떻게 낼 것인가? 를 생각하면 된다.

#### 1) 베이스 조건 바로 위의 단계

- 베이스 조건 바로 윗 단계의 함수를 생각해본다. 분해를 하기 직전 함수가 실행되었을 때를 말한다.
  - 만약 `n==1`이 베이스 조건이고, 분해는 `fun(n-1)`이라면 베이스 조건 바로 윗단계의 함수는 `n==2`일 때다.
- 예를 들어, n부터 1까지의 합을 구하는 함수를 짠다고 해보자. n이 2일 때 어떤 답이 나와야 할까 생각해본다.
  - 손으로 풀어도 답을 알 수 있다. `f(2)`는 3이다.
  - 그 다음 베이스 조건에서 반환되는 값을 가지고, 이 답을 어떻게 만들지 생각해본다. `f(1)`은 1이었다. 이걸로 어떻게 3을 만들까? 2를 더해주면 되지 않을까? 그러면 될 거 같다.

#### 2) 베이스 조건의 3단계 위

- 보통 베이스에서 3단계 위 지점까지는 직접 풀어도 쉽게 답이 나오고, 3단계 위 지점에서 제대로 작동한다면 대부분 잘 작동할 것이다.
- **일단 믿어본다. 바로 아랫단계의 재귀 호출에서 정답을 반환해준다고 가정하는 것**이다.
- 우리는 아직 재귀함수가 잘 설계되었는지 모른다. 일단 어떤 방식을 구현했는지 몰라도 '맞다 치고' 해보는 거다. 그러면 조합을 생각하기 쉬워진다.

> 두 케이스의 공통점을 찾는다

- 이 두가지 조합을 똑같은 방식으로 일치하게 할 수 있을까? 둘 다 정확한 답이 나올 수 있는 방식을 찾았따면, 재귀 설계는 끝났다.

---

- 이제 베이스 조건, 분해, 조합의 순으로 코드를 작성하면 된다.
- 알고리즘 문제를 재귀로 풀 때 가장 중요한 점은, 코드를 치기 전에 이런 접근법을 가지고 문제를 어떻게 풀지 생각해보는 것이다.
- **코드를 치기 전에 먼저 문제를 풀어야 한다.** 내가 손으로 풀 수 없는 문제를 컴퓨터에게 시킬 수는 없다.
