---
layout: post

title: '[hackerrank] Lonely Integer, Mini-Max Sum'
tag: [ algorithm ]
---


[ 문제 ] Lonely Integer
  
> You will be given an array of integers.   
> All of the integers except one occur twice. That one is unique in the array.  
>  
> Given an array of integers, find and print the unique element.  
>  
> For example, a = [ 1, 2, 3, 4, 3, 2, 1 ], the unique element is 4.    


[ 풀이 ] 
```javascript
// Complete the lonelyinteger function below.
function lonelyinteger(arr) {
    const countArr = [];
    let result;

    arr.forEach((elem) => {
        const thisNum = Number(elem);
        const isUndefined = (typeof countArr[thisNum] === 'undefined'); 

        isUndefined && (countArr[thisNum] = 0);
        countArr[thisNum] += 1;
    });

    result = countArr.indexOf(1);
    return result;
}
```

* 문제: https://www.hackerrank.com/challenges/lonely-integer/submissions/code/84469859   
   
 <br>
 <br>
 

[ 문제 ] Mini-Max Sum
  
> Given five positive integers,   
> find the minimum and maximum values that can be calculated by summing exactly four of the five integers.   
> Then print the respective minimum and maximum values as a single line of two space-separated long integers.   
>   
> For example, a = [ 1, 3, 5, 7, 9 ].   
> Our minimum sum is 1 + 3 + 5 + 7 = 16 and our maximum sum is 3 + 5 + 7 + 9 = 24.  
> We would print `16 24`


[ 풀이 ] 
```javascript
// Complete the miniMaxSum function below.
function miniMaxSum(arr) {
    const total = arr.reduce((acc, elem, i) => {
        return acc + elem;
    }, 0);
    const max = Math.max(...arr);
    const min = Math.min(...arr);

    console.log(total - max, total - min);
}
```

* 문제: https://www.hackerrank.com/challenges/mini-max-sum/submissions/code/84459005
 
 
 
 
 
 
 
