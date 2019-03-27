---
title: Subtraction big number from string
date: 2019-03-26 14:36:35
tags: javascript
category: javascript
---
# Vấn đề:
Có phép Cộng rồi giờ muốn trừ thì sao? :palmface:
# Code
```JS

const subtractStrings = (a, b) => {
  const aStr = a.split('').reverse(),
    bStr = b.split('').reverse(),
    alen = a.length, blen = b.length,
    len = alen > blen ? alen : blen
  let rs = [],
    remember = 0
  for (let i = 0; i <= len; i++) {
    const bi = (+bStr[i] || 0);
    let ai = (+aStr[i] || 0) - remember;
    if(ai < 1){
      
    }
    if (bi > ai) {
      ai = ai + 10;
  
      console.log(ai, bi, remember)
    }
    const subi = ai - bi;
    rs.push(subi)
        remember = +(ai>10);
  }
  return rs.reverse().join('')
}


console.log(
  subtractStrings('222', '15')

)
```
EX:
```JS
subtractStrings('','')//
subtractStrings('','')//
subtractStrings('','')//
subtractStrings('','')//
subtractStrings('','')//
```