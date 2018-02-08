---
title: '[freecodecamp] Reverse a String / Factorialize a Number / Check for Palindromes'
description: 'freecodecamp 알고리즘 풀기'
tag: [ algorithm ]
---


## Reverse a String

```javascript
function reverseString(str) {
  return str.split('').reverse().join('');
}

reverseString("hello");
```


## Factorialize a Number

`For example: 5! = 1 * 2 * 3 * 4 * 5 = 120`

```javascript
// 내가 푼 것
function factorialize(num) {
  var result = 1;
  for (var i = 2; i <= num; i++) {
    result = result * i;
  }
  return result;
}

factorialize(5);

// 다른 풀이
function factorialize(num) {
  return (num === 0) ? 1 : num * factorialize(num - 1);
}

factorialize(5);
```


## Check for Palindromes

앞, 뒤로 똑같은 영어 단어 ~  
특수문자, 공백 무시  

You'll need to remove all non-alphanumeric characters (punctuation, spaces and symbols) and turn everything lower case in order to check for palindromes.
<br>
We'll pass strings with varying formats, such as `"racecar"`, `"RaceCar"`, and `"race CAR"` among others.
<br>
We'll also pass strings with special symbols, such as `"2A3*3a2"`, `"2A3 3a2"`, and `"2_A3*3#A2"`.


```javascript
// 내가 푼 것
function palindrome(str) {
  var forwardStr = str.toLowerCase().replace(/[\W_]/g, '');
  var reverseStr = forwardStr.split('').reverse().join('');
  return forwardStr === reverseStr;
}

palindrome("eye");

// 다른 풀이
function palindrome(str) {
  str = str.toLowerCase().replace(/[\W_]/g, '');

  for (var i = 0, len = str.length - 1; i < (len/2); i++) {
    if (str[i] !== str[len - i]) { return false; }
  }
  return true;
}
```
  
`/[\W_]/g`  

`/ ... /g` It's a global regex. So it'll operate on multiple matches in the string.  
`[ ... ]` This creates a character set. Basically it'll match any single character within the listed set of characters.  
`\W_` This matches the inverse of "word characters" and underscores. Any non-word character.  
<br>
Then you have a few one off replacements for comma and period. Honestly, if that's the complete code, `/[\W_,.]/g`, omitting the two other replaces, would work just as well.  
