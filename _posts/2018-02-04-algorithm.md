---
layout: post

title: '[codewars] (7kyu) Simple Fun #215: Properly Closed Bracket Word'
description: '[codewars] 알고리즘 풀기'
tag: [ algorithm ]
---


## 문제

https://www.codewars.com/kata/simple-fun-number-215-properly-closed-bracket-word/train/javascript

### Task

We call letter x a counterpart of letter y, if x is the ith letter of the English alphabet, and y is the (27 - i)th for each valid i (1-based). For example, 'z' is the counterpart of 'a' and vice versa, 'y' is the counterpart of 'b', and so on.  

A properly closed bracket word (PCBW) is such a word that its first letter is the counterpart of its last letter, its second letter is the counterpart of its last by one letter, and so on.  

Determine if the given word is a PCBW or not.  

### Input/Output

* [input] string word  
A string consisting of lowercase letters.  
0 < word.length ≤ 30

* [output] a boolean value  
true if word is a PCBW, false otherwise.  

### Example

For word = "abiryz", the output should be true.  
'a' is the counterpart of 'z';  

'b' <-> 'y'  
'i' <-> 'r'  

For word = "aibryz", the output should be false.  
For word = "abitryz", the output should be false.  

### Sample Test

{% highlight JavaScript linenos %}

describe("Basic Tests", function() {
  it("It should works for basic tests.", function() {

    Test.assertEquals(closedBracketWord("abiryz"),true)

    Test.assertEquals(closedBracketWord("aibryz"),false)

    Test.assertEquals(closedBracketWord("abitryz"),false)

    Test.assertEquals(closedBracketWord("zhuazfsa"),true)

    Test.assertEquals(closedBracketWord("baby"),false)

    Test.assertEquals(closedBracketWord("grit"),true)

    Test.assertEquals(closedBracketWord("foul"),false)
  });
});

{% endhighlight %}

<br>
<br>

## 내가 푼 것

```javascript

function closedBracketWord(word) {
  const wordLength = word.length;
  const maxCount = wordLength / 2;
  const wordMap = {
    a: 1, b: 2, c: 3, d: 4, e: 5,
    f: 6, g: 7, h: 8, i: 9, j: 10,
    k: 11, l: 12, m: 13, n: 14, o: 15,
    p: 16, q: 17, r: 18, s: 19, t: 20,
    u: 21, v: 22, w: 23, x: 24, y: 25, z: 26
  };

  if ((maxCount % 1) !== 0) return false;

  for (let i = 0; i < maxCount; i++) {
    let w1 = word[i];
    let w2 = word[wordLength - i - 1];
    let counterpart = wordMap[w1] + wordMap[w2];
    if (counterpart !== 27) return false;
  }

  return true;
}

```

<br>

## 다른 풀이들 (Best Practice, Clever)

```javascript

// 1.
function closedBracketWord(s) {
  return s === s.split("").reverse().map(c => "abcdefghijklmnopqrstuvwxyz"["zyxwvutsrqponmlkjihgfedcba".indexOf(c)]).join("");
}
// 헐.. 맞네.. indexOf 쓰면 되지....


// 2.
function closedBracketWord(word) {
   if (word.length&1) return false;
   for (var i=0;i<word.length>>1;i++) if(word.charCodeAt(i)+word.charCodeAt(word.length-i-1)!=219) return false;
   return true
}


// 3.
const closedBracketWord = word =>
  word === String.fromCharCode(...[...word].reverse().map(char => (219 - char.charCodeAt())))


```
