---
layout: post

title: '[hackerrank] Staircase'
tag: [ algorithm ]
---


[ 문제 ]    
> Consider a staircase of size :  
>  
> &nbsp;&nbsp;&nbsp;\#  
> &nbsp;&nbsp;\#\#  
> &nbsp;\#\#\#  
>\#\#\#\#  
> Observe that its base and height are both equal to , and the image is drawn using # symbols and spaces. The last line is not preceded by any spaces.  
>   
> Write a program that prints a staircase of size .  
> Note: The last line must have  spaces in it.  

[ 풀이 ] 
```javascript

// Complete the staircase function below.
function staircase(n) {
    let str = '';

    for (let i = 1; i <= n; i++) {
        str += makeString(' ', n-i) + makeString('#', i);
        if (i !== n) { str += '\n';  } 
    }

    function makeString(char, n) {
        let result = '';
        if (!n) { return result; };
        while (n--) {
            result += char;    
        }
        return result;
    }

    console.log(str);
}
```

* 문제: https://www.hackerrank.com/challenges/staircase/submissions/code/84370021   
   
 <br>
 <br>
 
   
그리고 간단한 제너레이터 구구단 문제도..!  

```javascript

/* 문제 1 : oneToN 함수 구현하기 */

for (const f of oneToN(9)) {
  for (const b of oneToN(9)) {
    console.log(`${f} x ${b} = ${f * b}`);
  }
}

// 풀이 
function* oneToN(num) {
  let i = 1;
  while (i <= num) {
    yield i++;
  }
}

// 풀이 하나더 (클로저 버전) ==> for of 는 이터레이터를 다룬다. 배열을 반환해도 됨
const oneToN = (function() {
  let i = 1;
  const arr = [];

  function oneToN(num) {
    if (i > num) { return arr; }
    arr.push(i++);
    return oneToN(num);
  }

  return oneToN;
})();


/* 문제 2 : generator 함수 구현하기 */

for (const [i, j, k] of generator(9, 9)) {
  console.log(`${i} x ${j} = ${k}`);
}

// 풀이
function* generator(num1, num2) {
  let [i, j] = [1, 1];

  while (i++ <= num1) {
    while (j <= num2) {
      yield [ i, j++, i*j ];
    }
    j = 1;
  }
}


```









