# xlsx 모듈

## 왜 쓰게 됐나?

- `homeGNU` 프로젝트에서 공공데이터포털 API를 이용하여 시외버스 시간표를 불러오려고 했으나.. 왜인지는 모르겠지만 원하는 검색 결과가 나오지 않아 다른 방법을 찾으려고 했다.
- 팀원과 상의한 결과 엑셀로 해보면 어떠냐는 말에 나도 괜찮은 생각이다 싶어서 엑셀로 하자고 결정했다.
- 그런데, 엑셀을 불러오려면 모듈이 필요했고 찾아본 결과 xlsx 모듈을 사용하기로 결정했다.

## 설치

```
npm i xlsx
```

## 모듈 사용하기

```js
const xlsx = require("xlsx");
```

## 파일 읽기

```js
const workbook = xlsx.read(data, read_opts);

const workbook = xlsx.readFile(filename, read_opts);
```

### 시트 정보 추출

```js
// 첫 번째 시트 이름
const sheetName = workbook.SheetNames[0];

// 시트 이름에 따른 정보
const sheet = workbook.Sheets[sheetName];
```

## 엑셀 시트 데이터 읽기

![sheet](https://media.vlpt.us/images/hahaha/post/20568ada-1472-403d-ac84-51842ac31453/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-11-01%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%2010.28.25.png)

```js
// json 형태로 데이터 표시
const data = xlsx.utils.sheet_to_json(sheet);

// 출력: [ { name: 'kim', age: 23 }, { name: 'park', age: 24 } ]
```

> 참고: [Node.js xlsx 모듈](https://velog.io/@hahaha/Node.js-xlsx-%EB%AA%A8%EB%93%88)
