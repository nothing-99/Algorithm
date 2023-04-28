# Lv2 멀리 뛰기

## 생각

- 재귀호출을 이용해 모든 경우의 수를 찾아서 해결해보자

```js
function solution(n) {
  if (n === 1 || n === 2) return n;
  let result = 0;
  const recurHelper = (remain) => {
    if (remain === 0) {
      result++;
      return;
    }
    if (remain >= 1) recurHelper(remain - 1);
    if (remain >= 2) recurHelper(remain - 2);
  };
  recurHelper(n);

  return result % 1234567;
}
```

`실패 (시간초과)` 를 무더기로 맞이했다. 생각하다가 질문하기를 보니 "피보나치수"를 이용해야 한다는 얘기를 보고 숫자 결과를 나열해봤다. 피보나치 수열이다...

## 생각

- 피보나치 수열을 이용해 풀자
- 반복문을 이용하자

```js
function solution(n) {
  // n이 1이나 2일때
  if (n === 1 || n === 2) return n;
  // 피보나치 수열
  const d = [1, 2];
  let result = 0;
  for (let i = 0; i < n - 2; i++) {
    result = (d[0] + d[1]) % 1234567;
    [d[0], d[1]] = [d[1], result];
  }
  return result;
}
```

얍
