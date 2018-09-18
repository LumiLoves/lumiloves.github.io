---
layout: post

title: '[hackerrank] Equalize the Array'
tag: [ algorithm ]
---


[ 문제 ] Equalize the Array
  
> [input]  
> 5  
> 3 3 2 1 3  
>  
> [output]  
> 2  
>  
> 설명: 가장 최소한으로 요소를 지워서 같은 요소만 남게 만들기. 삭제한 요소의 갯수 리턴.


[ 풀이 ] 
```javascript
// Complete the equalizeArray function below.
function equalizeArray(arr) {
  const elemCounts = {};
  let sortedElems;
  let result;
  
  // 돌면서 갯수정보 수집
  arr.forEach((elem) => {
    if (!elemCounts[elem]) { elemCounts[elem] = 0; }
    elemCounts[elem]++;
  });

  // 가장 많은 애 갯수 제외한 수 리턴.
  sortedElems = Object.entries(elemCounts).sort((a, b) => (b[1] - a[1]));
  result = arr.length - sortedElems[0][1];
  
  return result;
}
```

* 문제: https://www.hackerrank.com/challenges/equality-in-a-array/submissions/code/84944248

 
