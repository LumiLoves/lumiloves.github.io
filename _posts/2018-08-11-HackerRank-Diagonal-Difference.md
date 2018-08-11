---
title: '[HackerRank] Diagonal Difference'
tag: [ algorithm ]
---

이제부턴 의미있는 TIL이 없는 날에는 알고리즘 한 문제라도 풀어서 올려야겠다.  
꾸준한 커밋 실천하기가 목적이니까 ~

* 문제: https://www.hackerrank.com/challenges/diagonal-difference/problem
* 결과: https://www.hackerrank.com/challenges/diagonal-difference/submissions/code/81070457
```
입력이 아래와 같은 매트릭스 배열로 들어올 때, (매트릭스 크기 바뀜)
3
11 2  4
4  5  6
10 8 -12

각 대각선 값끼리의 합의 차 (절대값)을 구해라.
11
   5
      6 의 합과,
      
      4
   5
10 의 합 의 차이값
```

```javascript
// Complete the diagonalDifference function below.
function diagonalDifference(matrix) {
    const maxIndex = matrix.length - 1;
    let sumPrimaryDiagonal = 0;
    let sumSecondaryDiagonal = 0;
    
    matrix.forEach((arr, i) => {
        sumPrimaryDiagonal += arr[i];
        sumSecondaryDiagonal += arr[maxIndex - i];
    });
    
    return Math.abs(sumPrimaryDiagonal - sumSecondaryDiagonal);
}
```
