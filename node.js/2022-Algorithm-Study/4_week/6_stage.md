# 4주차(04.08~04.15)

## Stage 6 - 문자열

### 11654번 아스키 코드

#### 전략

- 문자열 중 하나를 선택하여 아스키코드 번호로 변환해주는 함수인 `charCodeAt()` 함수를 이용하는 문제

#### 새로 알게된 것

```
str.charCodeAt(index)
```

- index에 해당하는 문자의 unicode 값을 리턴한다.

### 11720번 숫자의 합

#### 전략

- 주어진 숫자 문자열을 배열로 만들어버린 후 `forEach`문을 사용하여 다 더해준 뒤 출력

### 10809번 알파벳 찾기

#### 전략

1. 주어진 단어(문자열)을 문자열 배열로 변환
2. a부터 z까지 알파벳이 저장 된 배열을 생성
3. a부터 시작하여 단어에 알파벳이 존재하는지 확인
   - 알파벳이 존재할 경우, 해당 인덱스 값 출력
   - 알파벳이 없을 경우, -1 출력

#### 실수

1. 단어 부분을 돌리는 for문을 `forEach`문으로 이용하려 했다가 `break`를 못써서 그냥 일반적인 for문으로 사용했다.
2. 일반적인 `console.log()` 함수와는 다르게 `process.stdout.write()` 함수에 그냥 변수값만 넣어두면 아래와 같이 오류가 뜬다. 그래서, `${변수}`를 이용해서 출력하게 고쳤다.

```
TypeError [ERR_INVALID_ARG_TYPE]: The "chunk" argument must be of type string or an instance of Buffer or Uint8Array. Received type number (0)
```

3. 출력값에 문제가 없어서 백준에 제출을 했는데 런타임 에러가 떴다. 원인을 찾아보니, 출력값 맨 마지막에 공백문자가 들어가서 그랬다. 그래서 `process.stdout.write()` 함수를 사용하는 대신 `output`이라는 문자열에 값들을 차곡차곡 쌓아준 뒤 마지막에 `trim()` 함수를 이용하여 공백문자를 제거해준 후 출력을 해주었더니 해결되었다.

#### 개선

```js
const input = require("fs").readFileSync("/dev/stdin").toString();

const result = [];

for (let i = 97; i <= 122; i++) {
  result.push(input.indexOf(String.fromCharCode(i)));
}

console.log(result.join(" "));
```

- 정말 좋은 코드인 것 같다. 아스키코드를 이용해서 풀 생각은 전혀 못했는데 아스키코드를 사용하면 더 간단하게 풀 수 있었다.

#### 새로 알게된 것

```js
String.fromCharCode(num1[, ...[, numN]])
```

- 매개변수의 유니코드 값을 String형으로 변환한다.

```js
arr.join([separator]);
```

- 배열의 값들을 `separator`를 사용해서 구분해서 이어 붙여서 문자열로 변환한다. 빈 문자열이면 모든 요소들 사이에 아무 문자도 없이 연결된다.
