## 1

### 문제 - 배열의 유사도(120903)</code>

### 알고리즘 설계

#### 1) for문 순회

s1과 s2를 순회하여 동일한 두 값을 return하는 방법으로
두 배열의 유사한 값을 찾기 위해 for문으로 순회하였다.

- s1을 순회
- s2를 순회
- 순회하며 두 값의 동일한 값은 res에 추가

### 풀이 코드

```javascript
const solution = (s1, s2) => {
  let res = 0;
  for (let i = 0; i < s1.length; i++) {
    for (let j = 0; j < s2.length; j++) {
      if (s1[i] === s2[j]) res++;
    }
  }
  return res;
};

```

### 개인적인 회고와 다른 풀이

#### 2) 함수형

다른 방법은 없는지 인터넷 서칭. filter()를 이용해 배열을 순회한 후 includes()로 유사한 값을 찾는 방법이다.

- filter() : 주어진 배열의 얕은 복사본 생성. 순회, 복사 메서드. (두 종류를 동시 사용은 지양.)
- includes() : 배열의 항목에 특정 값이 포함되어 있는지 판단하여 true/false를 반환.

> [참고사이트](https://velog.io/@rosamondkim/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4Lv.0-%EB%B0%B0%EC%97%B4%EC%9D%98%EC%9C%A0%EC%82%AC%EB%8F%84-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8)

```javascript
const solution = (s1, s2) => {
  return s1.filter((e) => s2.includes(e)).length;
};
```

### 느낀 점

생각나는게 순회방법뿐이라 for문으로 이용하여 풀었는데, 앞으로 더 메서드 공부를 많이 해야겠다는 생각이 들었다.



## 2

### 문제 - 자연수 뒤집어 배열로 만들기(12932)</code>

### 알고리즘 설계

#### 1) 배열부터 만들자. 스프레드?..

뒤집으려면 reverse를 이용해야하는데 그러려면 배열로 먼저 변환해야겠다는 생각이 들었다.
처음엔 스프레드 연산자로 풀어서 배열로 담아보려고 했는데, 안돼서 생각해보니 *n의 값이 Number*였다.
또, 스프레드 연산자가 풀어준다는 생각으로 사용하려고 했던건데 다시 찾아보니 처음부터 잘못된 생각이었다.

- 스프레드 연산자 [...변수명] 기존 배열이나 객체의 전체 또는 일부를 다른 배열이나 객체로 빠르게 복사할 수 있다.
- reverse() : 값 뒤집기

#### 2) 결국 인터넷의 도움

숫자를 배열로 변환하는 방법을 찾아보았다.

- Array.form() : 순회 또는 유사 배열 객체를 복사해 새로운 배열을 만드는 메서드.
  - 먼저 숫자를 유사배열객체로 만든다.
  - Array.from을 이용해 유사배열객체 복사 -> reverse로 뒤집기

결과값 => [ '5', '4', '3', '2', '1' ]
'문자열'을 담은 배열이 되었다.

- Array.from() 메서드 안에서 배열의 속성을 설정할 수 있다.
  - 숫자 속성을 만들어주는 함수 변수 생성(nums)
  - Array.from 두번째 칸에 값 넣기

> [참고사이트](https://hianna.tistory.com/707)

### 풀이 코드

```javascript
const solution = (n) => {
  let str = String(n);
  let nums = (e) => Number(e);
  return Array.from(str, nums).reverse();
};
```

### 개인적인 회고와 다른 풀이

함수형을 이용하지 않은 더 쉬운 방법은 없을까?

### 느낀 점

이전에 수업에서 풀었던 배열 뒤집기와 같이 생각했는데, 이번은 숫자를 배열로 만들어 뒤집어야 하는 문제로 속성 값 변경에 어려움을 겪었다.

> [이정민 님 코드리뷰](https://github.com/forStudyingJavaScript/coding-test/pull/2#discussion_r1547202293) <br>
> [리즈 님 코드리뷰](https://github.com/forStudyingJavaScript/coding-test/pull/2#issuecomment-2031245143)
