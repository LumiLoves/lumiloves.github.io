---
layout: post

title: '[codewars] (7kyu) Simple Fun #48: Higher Version'
description: '[codewars] 알고리즘 풀기'
tag: [ algorithm ]
---


## 문제

https://www.codewars.com/kata/simple-fun-number-48-higher-version/  

Given two version strings composed of several non-negative decimal fields separated by periods ("."), both strings contain equal number of numeric fields.  
  
Return true if the first version is higher than the second version and false otherwise.  
  
  
예)  

For ver1 = "1.2.2" and ver2 = "1.2.0", the output should be true;  
For ver1 = "1.0.5" and ver2 = "1.1.0", the output should be false.  
  
<br>
<br>

## 내가 푼 것

{% highlight JavaScript linenos %}

function higherVersion(ver1, ver2) {
  const ver1Arr = ver1.split('.');
  const ver2Arr = ver2.split('.');
  const totalLength = (ver1Arr.length > ver2Arr.length)? ver1Arr.length : ver2Arr.length;
  let result = false;

  for (let i = 0; i < totalLength; i++) {
    const v1 = parseInt(ver1Arr[i], 10);
    const v2 = parseInt(ver2Arr[i], 10);
    
    if (v1 === v2) { continue; }
    if (v1 > v2) { result = true; }
    break;
  }

  return result;
}

{% endhighlight %}

<br>

## 다른 풀이들

{% highlight JavaScript linenos %}

// 1.

function higherVersion(ver1, ver2) {
  if (ver1 === ver2) return false;
  let [a1, a2] = [ver1.split('.'), ver2.split('.')];
  for (let i in a1) if (a1[i] !== a2[i]) return +a1[i] > +a2[i];
}

// 2.

function higherVersion(v1, v2) {
  [v1, v2] = [v1.split('.').map(Number), v2.split('.').map(Number)];
  for (let i = 0; i < v1.length && i < v2.length; i++) {
    if (v1[i] > v2[i]) return true;
    else if (v1[i] < v2[i]) return false;
  }
  return v1.slice(-1) > v2.slice(-1);
}

// 3.

function higherVersion(ver1, ver2) {
  return ver1.replace( /\d+/g, pad000 ) > ver2.replace( /\d+/g, pad000 );
}

const pad000 = x => ("0000"+x).slice(-5);

// 4.

function higherVersion(ver1, ver2) {
  v1 = ver1.split('.').map(Number);
  v2 = ver2.split('.').map(Number);
  return v1.reduce((res, n, i) => res || n - v2[i], 0) > 0;
}

{% endhighlight %}
