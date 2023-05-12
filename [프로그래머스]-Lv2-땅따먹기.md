# 땅따먹기

[문제](https://school.programmers.co.kr/learn/courses/30/lessons/12913)

```js
// 행 100,000 이하
// 열 4
function solution(land) {
  for (let i = 1; i < land.length; i++) {
    land[i][0] += Math.max(...land[i - 1].filter((e, i) => i !== 0));
    land[i][1] += Math.max(...land[i - 1].filter((e, i) => i !== 1));
    land[i][2] += Math.max(...land[i - 1].filter((e, i) => i !== 2));
    land[i][3] += Math.max(...land[i - 1].filter((e, i) => i !== 3));
  }
  return Math.max(...land[land.length - 1]);
}
```
