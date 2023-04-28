# Lv2 귤 고르기

- 우선 크기별로 개수를 구하자
- 상자를 채울 귤의 종류를 줄이기 위해 개수가 많은 것부터 상자에 채우자

```js
function solution(k, tangerine) {
  const obj = {};
  let count = 0;
  // 객체를 이용해 크기별 개수 구하기
  tangerine.forEach((e) => {
    obj[e] = ++obj[e] || 1;
  });
  // 개수 기준 내림차순으로 정렬
  return Object.entries(obj)
    .sort((a, b) => {
      if (a[1] - b[1] > 0) return -1;
      if (a[1] - b[1] < 0) return 1;
      if (a[1] - b[1] === 0) return 0;
    })
    .reduce((ret, e) => {
      if (count < k) {
        count += e[1];
        ret += 1;
      }
      return ret;
    }, 0);
}
```

- entries, sort, reduce 메서드 체인을 이용해서 정답을 도출한다.
- reduce 보다는 for 문을 이용하면 루프의 횟수를 줄일 수 있을 것으로 보인다. reduce 는 break 문이 불가능하기 때문에...
- `obj[e] = obj[e]++ || 1;` 은 정상작동하지 않았다. 이유가 뭘까?
