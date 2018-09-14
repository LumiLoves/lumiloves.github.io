---
layout: post

title: '[hackerrank] Utopian Tree, Library Fine, Pangrams'
tag: [ algorithm ]
---

 
[ 문제 ] Utopian Tree
  
> The Utopian Tree goes through 2 cycles of growth every year. Each spring, it doubles in height. Each summer, its height increases by 1 meter.  
>  
> Laura plants a Utopian Tree sapling with a height of 1 meter at the onset of spring. How tall will her tree be after growth cycles?  
>  
> For example, if the number of growth cycles is n = 5 , the calculations are as follows:
> 
> Period  Height  
> 0          1  
> 1          2  
> 2          3  
> 3          6  
> 4          7  
> 5          14  

[ 풀이 ] 
```javascript
// Complete the utopianTree function below.
const utopianTree = (() => {
    const heights = [ 1, 2 ];

    return (n) => {
        if (heights[n]) { return heights[n]; }        
        const lastIndex = heights.length - 1;
        
        for (let i = lastIndex; i <= n; i++) {
            if (typeof heights[i] !== 'undefined') { continue; }
            heights[i] = (i % 2 === 0)? (+heights[i - 1] + 1) : (heights[i - 1] * 2);
        }

        return heights[n];
    }
})();
```

* 문제: https://www.hackerrank.com/challenges/lonely-integer/submissions/code/84469859   
 
 
 <br>
 <br>


[ 문제 ] Library Fine
  
> Your local library needs your help! Given the expected and actual return dates for a library book, create a program that calculates the fine (if any). The fee structure is as follows:  
>    
> If the book is returned on or before the expected return date, no fine will be charged (fine = 0)
> If the book is returned after the expected return day but still within the same calendar month and year as the expected return date, (fine = 15 Hackos * the number of days late)
> If the book is returned after the expected return month but still within the same calendar year as the expected return date, the (fine = 500 Hackos * the number of months late)
> If the book is returned after the calendar year in which it was expected, there is a fixed fine of (10000 Hackos)
> Charges are based only on the least precise measure of lateness. For example, whether a book is due January 1, 2017 or December 31, 2017, if it is returned January 1, 2018, that is a year late and the fine would be .
>  
> [input]  
> 9 6 2015  
> 6 6 2015  
>  
> [output]
> 45  

[ 풀이 ] 
```javascript
// Complete the libraryFine function below.
function libraryFine(d1, m1, y1, d2, m2, y2) {
    const dHackos = (d1 - d2) * 15;
    const mHackos = (m1 - m2) * 500;
    const yHackos = (y1 - y2) * 10000;
    const result = (yHackos)? yHackos : (mHackos)? mHackos : dHackos;
    
    return (result > 0)? result : 0;
}
```
  
* 문제: https://www.hackerrank.com/challenges/library-fine/submissions/code/84566108
  
<br>
<br>


[ 문제 ] Pangrams
  
> Roy wanted to increase his typing speed for programming contests. His friend suggested that he type the sentence "The quick brown fox jumps over the lazy dog" repeatedly. This sentence is known as a pangram because it contains every letter of the alphabet.  
>  
> After typing the sentence several times, Roy became bored with it so he started to look for other pangrams.  
>  
> Given a sentence, determine whether it is a pangram. Ignore case.  
>  
> [input]  
> We promptly judged antique ivory buckles for the next prize
>  
> [output]
> pangram
> 
> [input]  
> We promptly judged antique ivory buckles for the prize
>  
> [output]  
> not pangram


[ 풀이 ] 
```javascript
// Complete the pangrams function below.
function pangrams(s) {
    const sArr = s.split('');
    const strCounter = {};
    const ALPHABET_LENGTH = 26;
    let resultLength;

    for (let str of sArr) {
        const thisStr = str.toLowerCase();
        if (thisStr === ' ') { continue; }
        if (!strCounter[thisStr]) { strCounter[thisStr] = 1; }        
    }
    
    resultLength = Object.keys(strCounter).length;
    return (resultLength === ALPHABET_LENGTH)? 'pangram' : 'not pangram';
}
```
  
* 문제: https://www.hackerrank.com/challenges/pangrams/submissions/code/84579510

