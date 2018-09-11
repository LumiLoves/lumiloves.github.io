---
layout: post

title: '[programmers] 지형 편집'
tag: [ algorithm ]
---


> [ 문제 ]    
> 1 x 1 x 1 크기의 정육면체 블록을 쌓아 게임 속 지형을 표현,  
> 블록의 높이를 균일하게 만드는데 드는 최소 비용을 구하는 문제
> 
> 입력  
> land(블록높이) : [[1, 2], [2, 3]]  
> P(블록추가비용) : 3  
> Q(블록제거비용) : 2  
> 
> 출력  
> result : 5
>
> [ 설명 ]
> 모든 땅의 높이를 1로 맞추는 데는 블록 4개를 제거해야 하므로 8의 비용이 듭니다.  
> 모든 땅의 높이를 2로 맞추는 데는 블록 1개를 추가하고 블록 1개를 제거해야 하므로 5의 비용이 듭니다.  
> 모든 땅의 높이를 3으로 맞추는 데는 블록 4개를 추가해야 하므로 12의 비용이 듭니다.  
> 따라서 최소 비용은 5이므로 5를 return 합니다.  


```javascript
function solution(land, P, Q) {
  const flattenLand = [].concat(...land);
  const max = Math.max(...flattenLand);
  const min = Math.min(...flattenLand);
  const totalArr = [];
  
  for (let height = min; height <= max; height++) {
      const total = flattenLand.reduce((acc, elem, i) => {
          const gap = elem - height;
          const price = gap * ((gap > 0)? Q : -P);
          return acc + price;
      }, 0);

      totalArr.push(total);
  }
  
  return Math.min(...totalArr);
}
```

아무리 머리를 써서 바꿔봐도 60.3점까지 밖에 안 나온다.  
뭐가 문제니 ....
<br><br>
2차원 array를 1차원으로 펼치는 방법이 되게 여러가지다.  
```javascript
flatten array

var arrays = [["$6"], ["$12"], ["$25"], ["$25"], ["$18"], ["$22"], ["$10"]];

// 1
var flatten = [].concat.apply([], arrays);
또는 
var flatten = [].concat.call([], ...arrays);

// 2
var flatten = arr => arr.reduce((acc, arr) => acc.concat(arr), []);

// 3
var flatten = [].concat(...arrays);
```


* 문제: [https://programmers.co.kr/learn/courses/30/lessons/12984?language=javascript](https://programmers.co.kr/learn/courses/30/lessons/12984?language=javascript)


