# 할인 행사

[할인 행사 문제](https://school.programmers.co.kr/learn/courses/30/lessons/131127)

## 생각

- 10일 단위로 검사하자
  - object 나 map 으로 want를 key로, number를 value로 객체를 만들자
  - 매일 할인하는 품목을 보고 객체를 수정한다.

```js
function solution(want, number, discount) {
  const map = new Map();
  let result = 0;

  // 데이터 세팅
  for (let i = 0; i < want.length; i++) {
    map.set(want[i], number[i]);
  }
  for (let i = 0; i < discount.length - 9; i++) {
    let temp = new Map(map);
    let ok = true;
    // 10일 단위로 검사
    for (let j = 0; j < 10; j++) {
      const idx = i + j;
      // 원하는 할인 품목에 있을 경우
      if (temp.has(discount[idx])) {
        const key = discount[idx];
        const value = temp.get(key) - 1;
        temp.set(key, value);
      }
    }
    // 원하는 개수만큼 할인하는지 확인
    for (let value of temp.values()) {
      if (value > 0) ok = false;
    }
    if (ok) result += 1;
  }
  return result;
}
```
