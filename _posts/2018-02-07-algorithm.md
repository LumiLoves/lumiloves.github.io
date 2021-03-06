---
layout: post

title: '[codewars] (7kyu) T.T.T.26: How many students have finished all the homework'
description: '[codewars] 알고리즘 풀기'
tag: [ algorithm ]
---


## 문제

https://www.codewars.com/kata/t-dot-t-t-dot-26-how-many-students-have-finished-all-the-homework/train/javascript


### Problem

For example: There are 60 students in a class. The teacher assigned two homework, 40 students finished the first homework, 31 students finished second homework, 4 students did not finish any homework. Please calculate: how many students have finished all the homework?

### Task

Complete function `howMany()` that accepts three arguments:  

`students`: Total number of students  

`finished`: An array. It's a list of the number of students who finish each homework. The array always contains 2 elements.  

`unfinish`: The number of students who did not finish any homework.  

The result should be a number that is the number of students who have finished all the homework.  

If it is not possible to get the correct result, please return `-1`  

### Sample Test

```javascript
Test.assertSimilar(howMany(60,[40,31],4) , 15)
Test.assertSimilar(howMany(60,[33,44],3) , 20)
Test.assertSimilar(howMany(60,[40,20],0) , 0)
Test.assertSimilar(howMany(60,[22,11],6) , -1)
```

<br>
<br>

## 내가 푼 것

```javascript
function howMany(students, finishedEach, unfinish) {
  const finishedTotal = students - unfinish;
  const finishedBoth = finishedEach[0] + finishedEach[1] - finishedTotal;

  return (finishedBoth >= 0)? finishedBoth : -1;
}
```

<br>

## 다른 풀이들 (Best Practice, Clever)

```javascript

// 1.
howMany=(S,[A,B],U)=>Math.max(A+B+U-S,-1)


// 2.
function howMany(students,finished,unfinish){
  let a = finished[0] + finished[1] - (students - unfinish);
  return a < 0? -1 : a;
}

```
