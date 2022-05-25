# 9주차(05.14~05.20)

## Stage 9 - 재귀

### 10872번 팩토리얼

#### 전략

- 재귀함수란 어떤 범위에 있는 모든 정수를 곱하는 것이다.
- `n-1`을 곱하는 것이 반복되므로 재귀함수를 이용하여 문제를 풀면 된다.

### 10870번 피보나치 수 5

#### 전략

- 피보나치 수는 0과 1로 시작한다. 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1이다. 그 다음 2번째 부터는 바로 앞 두 피보나치 수의 합이 된다.
- 이를 식으로 써보면 Fn = Fn-1 + Fn-2 (n ≥ 2)가 된다.
- `number`가 0일 때는 `0`을 return 하고, 1일 때는 `1`을 return 하고, 그 외에 수는 `getFibonachi(number - 2) + getFibonachi(number - 1)` 로 return 해준다.

### 17478번 재귀함수가 뭔가요?

#### 전략

- 모든 질문과 답변을 변수와 배열을 이용해서 저장을 했다.
- 첫 질문(`어느 한 컴퓨터공학과 학생이 유명한 교수님을 찾아가 물었다.`)은 단독적으로 나오는 멘트기 때문에 재귀함수에 포함시키지 않고 바로 출력을 시킨다.
- 그리고 `____` 공백문자를 기준으로 출력 방법을 나눈다.
- 제일 먼저 `재귀함수가 뭔가요? 재귀함수는 자기 자신을 호출하는 함수라네 라고 답변하였지.` 를 출력시킨다.
- 그리고 number의 값을 하나씩 줄여나가면서 `재귀함수가 뭔가요?~잘 들어보게...~라고 답변하였지.` 를 출력시킨다.

#### 어려웠던 점

- 어떻게 하면 코드를 깔끔하게 짤지 고민을 많이 했다. 처음에는 무지성으로 문자열을 바로 출력시키려다가 그렇데 풀면 안되겠다 싶어서 바로 변수와 배열에 멘트를 저장해서 조금 더 코드 유지보수가 쉽도록 만들었다.

### 2447번 별 찍기 - 10

#### 전략

- 이 문제는 공백이 들어가는 칸의 패턴을 잘 파악해서 푸는 문제이다.
- 먼저, 입력값이 3일 때를 생각해보면 `(1,1)`이 공백을 출력해야 하는 위치인 것을 알 수 있는데, 이는 i, j%3의 값이 1인 곳을 찾음으로서 해결할 수 있다. 이 경우가 재귀에서 처리하는 최소범위의 값이다.
- 9로 넘어갈 경우, 우리가 공백으로 처리한 부분 이외에 추가로 공백을 칠해줘야 하는 부분이 나오는데 다음과 같다.

```
(3,3) (3,4) (3,5)

(4,3) (4,4) (4,5)

(5,4) (5,4) (5,5)
```

- 여기서 i와 j의 범위는 모두 `3^1 <= i,j < 3^1 + 3^1` 이다.
- 이 부분을 처리해주기 위해 3으로 나눈 값의 목만을 취해서 재귀로 호출한다. 그러면, 모두 공백(`n%3===1`)일 경우에 해당해서 공백이 출력된다.

#### 어려웠던 점

- 빈 칸의 규칙을 찾으려고 애썼지만, 결국 오랜 시간 고민해도 찾아내지 못했다. 정말 재귀함수 문제는 많이 풀어봐야 될 것 같다. 어떻게 이런 규칙을 찾을 수 있는지 ㅠㅠ..