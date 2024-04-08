## 1

### 문제 - <code>n의 배수 고르기 (120905)</code>

### 알고리즘 설계

numList를 순회하여 정수 n의 배수에 해당하는 변수를 찾아 새로운 배열에 담습니다.

1. for문

- 정수 n의 배수를 담는 새 배열 newList
- for문으로 배열 numList 순회
- push() 메서드로 true값 빈 배열에 담기

### 풀이 코드

```javascript
const solution = (n, numList) => {
  const newList = [];
  for (let i = 0; i < numList.length; i++) {
    if (numList[i] % n === 0) {
      newList.push(numList[i]);
    }
  }
  return newList;
};
```

### 개인적인 회고와 다른 풀이

2. 순회메서드 = filter()

- filter() 의 순회메서드를 사용하면 콜백함수를 한번씩 호출하며
- 호출된 값 중, 참 값만 반환하여 새 배열로 구성해 준다.

```javascript
const solution = (n, numList) => numList.filter((el) => el % n === 0);
```

### 느낀 점

filter에서 엘리먼트의 이름을 정할 때 `el`을 처음엔 `newList`라고 이름을 지었다가
여기서 콜백함수 엘리먼트는 값을 *호출하는 역할*을 하기 때문에
새로운 배열은 또 아닌것같아서 `el`로 변경하였습니다.
제가 생각한게 맞는지, 의견 부탁드립니다 🙂

아직은 문제를 풀 때, 주어진 값을 확인해야하는 경우 *for문*을 통한 순회가 익숙한데,
순회가 필요할 때는 *filter 메서드*를 이용하면 더 좋겠다는 생각이 들었습니다.

## 2

### 문제 - <code>대문자와 소문자 (120893)</code>

### 알고리즘 설계

변환할 방법이 도저히 생각이 나지 않아서 인터넷의 도움을 받았습니다..

1. for문

- myStr을 순회하며 대소문자 확인
- .toUpperCase() : 문자열을 대문자로 반환
- .toLowerCase() : 문자열을 소문자로 반환

### 풀이 코드

```javascript
const solution = (myStr) => {
  let res = [];
  for (let i = 0; i < myStr.length; i++) {
    if (myStr[i] === myStr[i].toUpperCase()) {
      res.push(myStr[i].toLowerCase());
    } else {
      res.push(myStr[i].toUpperCase());
    }
  }
  return res.join("");
};
```

### 개인적인 회고와 다른 풀이

2. 함수형

- 스프레드 연산자
- map()
- join()

```javascript
const solution = (myStr) =>
  [...myStr]
    .map((el) =>
      el === el.toUpperCase() ? el.toLowerCase() : el.toUpperCase()
    )
    .join("");
```

### 느낀 점

처음엔 사전을 다 만들어야하나...밖에 생각이 안나서 결국 인터넷을 찾아 풀었습니다.
css와 같은 대소문자로 변경해주는 메서드가 있다는걸 처음 알게 되었습니다.

## 3

### 문제 - <code>조건에 맞게 수열 변환하기 3 (181835)</code>

### 알고리즘 설계

k의 값이 짝수인지, 홀수인지를 확인해서 순회한 값에 연산을 해야겠다 생각했습니다.

1. for문

- arr를 순회
- 만약, k가 짝수일때는 더하고, 아니면 곱하라.
- res에 담아 return

### 풀이 코드

```javascript
const solution = (arr, k) => {
  let res = [];
  for (let i = 0; i < arr.length; i++) {
    if (k % 2 === 0) {
      res[i] = arr[i] + k;
    } else {
      res[i] = arr[i] * k;
    }
  }
  return res;
};
```

### 개인적인 회고와 다른 풀이

좀 더 간결한 방법은 없을지 프로그래머스 정답에서 찾아 보았습니다.

2. 함수형

- .map()

```javascript
const solution = (arr, k) => arr.map((v) => (k % 2 === 0 ? v + k : v * k));
```

### 느낀 점

프로그래머스 정답 해설 중 댓글이 가장 많은 답변은
`arr.map((v) => (k % 2  ? v * k : v + k));` 이었는데요.
저는 `k % 2 === 0` 이라는 조건이 더 읽기 쉬워서 위와 같이 풀어보았는데,
여러분의 생각은 어떠신가요?
