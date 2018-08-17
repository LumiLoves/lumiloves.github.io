---
title: '[HackerRank] Time Conversion'
tag: [ algorithm ]
---

* 문제: https://www.hackerrank.com/challenges/time-conversion/problem
* 결과: https://www.hackerrank.com/challenges/time-conversion/submissions
```
[ Explanation ]
* Given a time in -hour AM/PM format, convert it to military (24-hour) time.
* Note: Midnight is 12:00:00AM on a 12-hour clock, and 00:00:00 on a 24-hour clock.
Noon is 12:00:00PM on a 12-hour clock, and 12:00:00 on a 24-hour clock.

[ Sample Input ]
07:05:45PM

[ Sample Output ]
19:05:45
```

```javascript
// Complete the timeConversion function below.
function timeConversion(timeStr) {
    const isPM = (timeStr.indexOf('PM') > -1);
    const timeStrArr = timeStr.split(':');
    let result;

    if (isPM) {
        timeStrArr[0] = (Number(timeStrArr[0]) % 12) + 12;
    } else {
        timeStrArr[0] = '0' + Number(timeStrArr[0]) % 12;
    }
    timeStrArr[2] = timeStrArr[2].replace('AM', '').replace('PM', '');
    result = timeStrArr.join(':');

    return result;
}
```
