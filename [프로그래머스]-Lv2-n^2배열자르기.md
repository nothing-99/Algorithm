# n^2 배열 자르기

## 생각 1

- 순차적으로 i행 i열까지 i로 채우는 2차원 배열을 만든다.
- 1차원 배열로 만든다.
- left 에서 right 까지 요소를 리턴한다.

```js
function solution(n, left, right) {
  // [n][n] 배열 만들기
  const arr = Array.from({ length: n }, (v) => new Array(n).fill(0));
  // i행 i열까지 i로 채우기
  for (let i = 0; i < n; i++) {
    for (let j = 0; j < n; j++) {
      if (i < j) arr[i][j] = j + 1;
      else if (i > j) arr[i][j] = i + 1;
      else arr[i][j] = i + 1;
    }
  }
  // 평탄화 ( 1차원 배열로 만들기 )
  // [left] ~ [right] 만 남기기
  return arr.flat().slice(left, right + 1);
}
```

`실패 (signal: aborted (core dumped))` 수많은 에러의 행진을 만났다... 찾아보니 메모리 사용량 에러라고 한다.

## 생각 2

- 2차원 배열 만들지 말고 계산을 통해서 다이렉트로 요소의 값을 구하자
- left / n 의 정수부분은 행! left % n 은 열! 로 볼 수 있다.
- left, right 중 큰 수에 1을 더한 수를 요소로 채운다.

```js
function solution(n, left, right) {
  const result = [];
  for (let i = left; i < right + 1; i++) {
    const row = Math.floor(i / n);
    const col = i % n;
    const max = Math.max(...[row, col]) + 1;
    result.push(max);
  }
  return result;
}
```

## 문법

**Array.from()**
