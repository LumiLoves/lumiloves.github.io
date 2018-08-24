---
layout: post

title: '[HackerRank] Plus Minus'
tag: [ algorithm ]
---


>[ Explanation ]
>* There are 3 positive numbers, 2 negative numbers, and 1 zero in the array. 
>* The proportions of occurrence are 
  positive: 3/6 = 0.500000, negative: 2/6 = 0.333333  and zeros: 1/6 = 0.166667.
>* Complete the plusMinus function in the editor below.  
  It should print out the ratio of positive, negative and zero items in the array,
  each on a separate line rounded to six decimals.
>
>[ Sample Input ]  
>6  
>-4 3 -9 0 4 1
>
>[ Sample Output ]   
>0.500000   
>0.333333  
>0.166667  

```javascript
// Complete the plusMinus function below.
function plusMinus(arr) {
    const totalLength = arr.length;
    let positiveNumbers = 0;
    let negativeNumbers = 0;
    let zeros = 0;
    let result = null;

    arr.forEach((elem) => {
        if (elem > 0) {
            positiveNumbers++;
        } else if (elem < 0) {
            negativeNumbers++;
        } else {
            zeros++;
        }
    });

    const toFixed = (num, length) => {
        return num.toFixed(length);
    }

    result =`${toFixed(positiveNumbers/totalLength, 6)}
${toFixed(negativeNumbers/totalLength, 6)}
${toFixed(zeros/totalLength, 6)}`;

    console.log(result);
}
```


* 문제: https://www.hackerrank.com/challenges/plus-minus/problem
* 결과: https://www.hackerrank.com/challenges/plus-minus/submissions/code/81145913

