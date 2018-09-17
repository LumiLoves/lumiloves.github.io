---
layout: post

title: '[hackerrank] Repeated String, Jumping on the Clouds, Cut the sticks'
tag: [ algorithm ]
---


[ 문제 ] Repeated String
  
> [input]  
> aba  
> 10   
>  
> [output]  
> 7  
>  
> 설명: aba를 10개까지 늘리면 abaabaabaa 가 됨.  
> 이 중에서 'a'의 갯수를 구하면 7


[ 풀이 ] 
```javascript
// Complete the repeatedString function below.
function repeatedString(str, n) {
  const aArr = str.match(/a/g);
  if (!aArr) { return 0; }
  
  const quotient = Math.floor(n / str.length);
  const remainder = n % str.length;
  
  let result = (quotient * aArr.length);
  if (remainder) { 
    const matchAs = str.slice(0, remainder).match(/a/g);
    result += matchAs? matchAs.length : 0; 
  }
  
  return result;
}
```

* 문제: https://www.hackerrank.com/challenges/repeated-string/submissions/code/84870162

 
 <br>
 <br>
 
 
[ 문제 ] Jumping on the Clouds
  
> 0 은 구름, 1 은 번개  
> 구름만 점프할 수 있고, 번개는 건너뛰어야 함  
> 만약 구름이 연속적으로 있으면 1개 또는 2개까지 한번에 점프 가능  
> 이때 총 점프한 횟수를 구하는 문제.  
>  
> [input]  
> 7  
> 0 0 1 0 0 1 0
>  
> [output]  
> 4  

[ 풀이 ] 
```javascript
// Complete the jumpingOnClouds function below.
function jumpingOnClouds(c) {
  const zeroArr = c.join('').split('1');
  let jumpingCount = 0;
  
  zeroArr.forEach((arr) => {
    let restLength = arr.length;
    jumpingCount++;
    restLength--;
    
    if (restLength) {
      jumpingCount += Math.floor(restLength / 2) + (restLength % 2);
    }
  });

  return jumpingCount - 1; // 최초 진입시 카운트 되는 1 삭제
}
```

* 문제: https://www.hackerrank.com/challenges/jumping-on-the-clouds/submissions/code/84869867

 
 <br>
 <br>
 
 
[ 문제 ] Cut the sticks
  
> [input]  
> 6  
> 5 4 4 2 2 8  
>  
> [output]  
> 6  
> 4  
> 2  
> 1   
>  
> [설명]
> sticks-length   |     length-of-cut  | sticks-cut  
> 5 4 4 2 2 8       |      2        |       6  
> 3 2 2 _ _ 6       |      2         |      4  
> 1 _ _ _ _ 4       |      1         |      2  
> _ _ _ _ _ 3       |      3         |      1   
> _ _ _ _ _ _       |    DONE        |    DONE  

[ 풀이 ] 
```javascript
// Complete the cutTheSticks function below.
function cutTheSticks(arr) {
  const stickCutArr = [];
  let cutArr = arr;
  
  while (cutArr.length > 0) {
    stickCutArr.push(cutArr.length);
    cutArr = cutArrFn(cutArr);
  }

  function cutArrFn(arr) {
    const min = Math.min(...arr);
    const result = [];
    
    arr.forEach((elem) => { 
      const decreaseElem = elem - min;
      (decreaseElem > 0) && result.push(decreaseElem);
    });

    return result; 
  }

  return stickCutArr;
}
```

* 문제: https://www.hackerrank.com/challenges/cut-the-sticks/submissions/code/84681831

