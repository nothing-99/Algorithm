# 피로도

[프로그래머스 피로도 문제 확인](https://school.programmers.co.kr/learn/courses/30/lessons/87946)

## 생각

- DFS도 그래프에서 사용하는 순회방법이 아니라 하나의 추상적인 개념이다.
- DFS를 그래프, 트리로 데이터를 저장한 후에 사용해야 하는 것으로 생각하면 오산.

## 문법

- 객체나 리스트(리스트도 객체의 한 종류)를 복사할 때는 **"distructing assignment"**로 쉽게 가능하다.
- Map객체로 생성한 인스턴스로 해봤는데
  - `[...map]`의 경우 **[key, vlaue]**를 요소들이 하나의 배열에 담겼다.
  - `{...map}`의 경우 빈 객체가 리턴...

## 코드

```js
function solution(k, dungeons) {
  let answer = 0;

  const dfs = (visited, reserved, count) => {
    if (!reserved || visited.length === dungeons.length) {
      answer = Math.max(answer, count);
      return;
    }
    for (let i = 0; i < dungeons.length; i++) {
      if (!visited.includes(i)) {
        const [req, use] = dungeons[i];
        const copy = [...visited];
        copy.push(i);
        if (reserved >= req) {
          dfs([...copy], reserved - use, count + 1);
        } else {
          dfs([...copy], reserved, count);
        }
      }
    }
  };
  dfs([], k, 0);

  return answer;
}
```
