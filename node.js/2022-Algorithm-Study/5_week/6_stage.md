# 5주차(04.16~04.22)

## Stage 6 - 문자열

### 5622번 다이얼

#### 전략

- A~Z 문자열을 10진수로 변환한 후 3을 나눠주고 2를 더해주면 각 알파벳에 해당하는 다이얼 넘버를 뽑아올 수 있다.
- 단, 예외적으로 다이얼 넘버 7부터 규칙성이 바뀌므로 예외적으로 기존의 값과 달라지는 "S", "V", "Y", "Z"는 따로 if문으로 처리해주었다.

#### 실수

- 처음에 다이얼 넘버 7에 알파벳이 4개가 들어가는줄 모르고 풀었다가 혼쭐났다..

#### 개선방안

```js
let fs = require("fs");
let input = fs.readFileSync("/dev/stdin").toString().trim();
let phone = {
  2: "ABC",
  3: "DEF",
  4: "GHI",
  5: "JKL",
  6: "MNO",
  7: "PQRS",
  8: "TUV",
  9: "WXYZ",
};
let result = 0;

for (let i = 0; i < input.length; i++) {
  for (let j = 2; j <= 9; j++) {
    if (phone[j].includes(input[i])) {
      result += j + 1;
      break;
    }
  }
}

console.log(result);
```

- 객체와 `includes` 함수를 사용해서 푸는 방법도 괜찮은 것 같다. 앞으로는 객체도 자주 써봐야겠다.

---

### 2941번 크로아티아 알파벳

#### 전략

- 특수 문자를 결과에 영향을 미치지 않는 다른 문자로 바꾸고 개수를 센다.

#### 실수

1. 1시간 넘게 문제를 풀다가 결국에는 포기했다. 오류를 하나 해결하면 다른 오류가 터지는 식이었다. 아예 안 풀리면 모르겠는데 나한테 "넌 풀수있다" 라는 희망고문을 해서 오래 고민을 했다.
2. 내 코드로는 `c=c=` 같이 같은 문자열이 여러 개 있을 경우를 잡아내지 못했다.
3. 그래서, 다른 사람들이 어떻게 풀었는지 봤는데 어이가 없었다. 그냥 목록에 있는 알파벳을 결과에 영향을 미치지 않는 다른 문자로 바꾸고 개수를 셌다.
4. 아니면, 정규 문자식을 사용했는데 지금 여기서 다루기에는 글이 길어지니 따로 TIL에 정리를 해야겠다.

---

### 1316번 그룹 단어 체크

#### 전략

- `split()` 함수를 이용해서 `a~z` 문자를 기준으로 나눠서, 배열의 길이가 `2`보다 클 경우 연속되지 않는 경우이니 count를 하지 않는다.
- 단, 예외 처리를 두 가지 해주어야 한다.
  1. 같은 알파벳이 여러 개 나오면 빈 문자열(`""`)이 생기니, 빈 문자열을 `filter()` 함수로 걸러줘야 한다.
  2. 문자열 끝쪽에 있는 알파벳을 기준으로 `split`할 경우, 빈 문자열이 생기는데 이때 이 값을 지워버리면 결과값에 영향을 미치게 된다. 그래서, 문자열 양 옆에 결과값에 영향을 미치지 않는 문자(`*`)를 집어넣어줬다.

#### 개선 방안

- 꽤 괜찮은 코드를 들고왔다.

```js
const caseCount = Number(input[0]);
let countGroupWord = 0;

for (let i = 1; i <= caseCount; i++) {
  const word = input[i];
  const letter = [];
  let isGroupWord = true;

  for (let j = 0; j < word.length; j++) {
    if (letter.indexOf(word[j]) === -1) {
      letter.push(word[j]);
    } else {
      if (letter.indexOf(word[j]) !== letter.length - 1) {
        isGroupWord = false;
        break;
      }
    }
  }

  if (isGroupWord) {
    countGroupWord += 1;
  }
}

console.log(countGroupWord);
```

- 새로운 알파벳이 보이면 `letter` 배열에 추가하고, 만약 이전에 발견된 알파벳을 만나면 그 알파벳의 `index` 값과 `letter.length - 1` 값을 비교해본다. 만약 둘이 다르다면, 연속되지 아니한 경우이니 그룹 단어에서 제외해버린다.
