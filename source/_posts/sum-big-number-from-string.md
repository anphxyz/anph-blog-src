---
title: Sum big number from string
date: 2019-03-14 13:48:10
tags:
---

```JS
const sumStrings = (a, b) => {
  const aStr = a.split('').reverse(),
    bStr = b.split('').reverse(),
    alen = a.length,
    blen = b.length,
    len = alen > blen ? alen : blen
  let rs = [],
    remember = 0
  for (let i = 0; i <= len; i++) {
    const rsi = (+aStr[i] || 0) + (+bStr[i] || 0) + remember,
      rss = (rsi < 10 ? '0' : '') + rsi,
      [r, sum] = rss.split('')
    remember = +r
    rs.push(sum)
  }
  return rmvLeadZero(rs.reverse().join(''))
}
const rmvLeadZero = s => {
  while (s.charAt(0) === '0')
    s = s.substr(1)
  return s
}
```
EX:
```JS
sumStrings('123', '321')//444
sumStrings('8797927323', '3232321')//"8801159644"
```