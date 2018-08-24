---
layout: post

title: '[codewars] Reversed sequence'
description: '[codewars] 알고리즘 풀기'
tag: [ algorithm ]
---


## 문제

Get the number n to return the reversed sequence from n to 1.

Example : n=5 >> [5,4,3,2,1]



## 내가 푼 것

{% highlight JavaScript linenos %}

const reverseSeq = n => {
  let result = [];

  for (let i = 0; i < n; i++) {
    result.push(n - i);
  }

  return result;
};

{% endhighlight %}



## 다른 풀이들

{% highlight JavaScript linenos %}

// 1.

const reverseSeq = n => {
  let arr = [];
  for  (let i=n; i > 0; i--) {
    arr.push(i);
  }
  return arr;
};

// 2.

const reverseSeq = length => Array.from({length}, () => length--);

function reverseSeq(length) {
  return Array.from({length}, function() {
    return length--;
  });
}


{% endhighlight %}
