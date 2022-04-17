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
