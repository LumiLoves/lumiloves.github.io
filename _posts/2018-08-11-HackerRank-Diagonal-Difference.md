---
title: '[HackerRank] Diagonal Difference'
tag: [ algorithm ]
---

이제부턴 의미있는 TIL이 없는 날에는 알고리즘 한 문제라도 풀어서 올려야겠다.  
꾸준한 커밋 실천하기가 목적이니까 ~

문제: https://www.hackerrank.com/challenges/diagonal-difference/problem   
풀이: https://www.hackerrank.com/challenges/diagonal-difference/submissions/code/81070457

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
