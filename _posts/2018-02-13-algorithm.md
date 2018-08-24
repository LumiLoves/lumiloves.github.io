---
layout: post

title: '[programmers] 다음 큰 숫자 (Level 3)'
description: 'programmers 알고리즘 풀기'
tag: [ algorithm ]
---

## 문제

[링크](https://programmers.co.kr/learn/challenge_codes/174)  
<br>
어떤 수 `N(1≤N≤1,000,000)` 이 주어졌을 때, N의 다음 큰 숫자는 다음과 같습니다.  
<br>
N의 다음 큰 숫자는 N을 2진수로 바꾸었을 때의 1의 개수와 같은 개수로 이루어진 수입니다.  
1번째 조건을 만족하는 숫자들 중 N보다 큰 수 중에서 가장 작은 숫자를 찾아야 합니다.  
예를 들어, 78을 2진수로 바꾸면 `1001110` 이며, 78의 다음 큰 숫자는 83으로 2진수는 `1010011` 입니다.  
N이 주어질 때, N의 다음 큰 숫자를 찾는 `nextBigNumber 함수`를 완성하세요.  
<br>
<br>

```javascript
// 내가 푼 것
function nextBigNumber(origin, nxt) {
  var next = nxt || origin + 1;
  var originBinary = origin.toString(2);
  var originBinaryCount =  ( originBinary.match(/1/g) || [] ).length;
  var nextBinary = next.toString(2);
  var nextBinaryCount =  ( nextBinary.match(/1/g) || [] ).length;

  if (originBinaryCount === nextBinaryCount) {
		return next;
  } else {
    return nextBigNumber(origin, next + 1);
  }
}
console.log(nextBigNumber(78));

// 다른 좋은 풀이 1
function nextBigNumber(n) {
  var size = n.toString(2).match(/1/g).length;

  while (n++) {
    if (size === n.toString(2).match(/1/g).length) return n;
  }
}

// 다른 좋은 풀이 2
/** 알고리즘 시간 복잡도 O(log n) 이지만 사실상 O(a)에 가까움.
** 655395 입력후 1억번 실행에 소요 시간450ms 미만 */
function nextBigNumber(n) {
  var i, j;
  
  for (i = 0; !(n & 1); i++) {n = n >> 1; } // 1을 찾을때까지 우로 쉬프트, 쉬프트 횟수 = i
  for (j = 0; n & 1; i++, j++) {n = n >> 1; } // 0을 찾을때까지 우로 쉬프트, 1의 갯수 = j
  for (j--, n++; i !== j; i--) {n = n << 1; } // 0자리에 1대입, 1의 갯수 -1, i === j 가 될때까지 죄로 쉬프트하면서 쉬프트 횟수 -1
  for (i; i; i--, n++) {n = n << 1; } // i === 0 될때까지 좌로 쉬프트 하면서 쉬프트 횟수 -1, 0자리에 1대입
  return n;
}
```
