---
title: 'ES6: Destructuring'
date: 2018-05-22 09:27:01
tags:
---
Tìm hiểu Destructuring nested Objects trong Javascripts

``` JS
    function _getSampleObject() {
      return {
      data: {
    "_id": 13252,
  "FO100": 14548,
  "NV101": "tx_Thanh262",
  "NN112": 0,
  "NA126": [ 14523, 14509, 14521  ],
  "myFriendLst": {
    "14333": {
      "TYPE": "N100",
      "NV102": "/VK6/LgruY2fFKlWe81j2jheW0AfW",
      "NV106": "Thần Nông",
      "FO100": 14333,
      "PF600": 21550,
      "OKEY": "6Wm5tz7TKnUCRVeX"
    },
    "14523": {
      "TYPE": "N100",
      "NV102": "4q+x2nPQ3UNGQBomA3PsYqZQdzV4L",
      "NV106": "Witch",
      "FO100": 14523,
      "PF600": 21540,
      "OKEY": "/hrEaR7Fe3Otb0MM"
    },
    "length": 5
  },
  "myAffiliateList": [],
  "myBranchList": -1,
  "MKEY": "BuKphUV4yF6hGw1d"
}
    }
```
1. Destructuring Objects
  
    a. old style
``` JS
const res = _getSampleObject();
const data = res.data;
const myFriendLst = res.myFriendLst;

console.log({data, possibility});
// -> {data: {_id {...}}, myFriendLst: {1443:}}
```
    b. new style
``` JS
const { data, possibility } = _getSampleObject();
```
Curly bracket ở đây không phải là một block, đó là cấu trúc của destructuring. Kết quả trả về của 2 cách trên là như nhau.

Tiếp đến giả sử ta cần đào sâu hơn với planTwo trong nested Ojbect
``` JS
const { data, myFriendLst } = coolWaysToKillThanos();
console.log(data.planTwo, possibility);
// -> {method: 'Call John Wick', rate: '8/10'}  '60%'
```
Ta có thế destructuring planTwo trực tiếp như sau:
``` JS
const { data: { planTwo }, possibility } = coolWaysToKillThanos();
console.log(data.planTwo);
// -> Error!
```
Ngay lập tức Console trên sẽ báo lỗi, đơn giản lúc này data không còn là variable được destructed

Lúc này đơn giản chỉ cần:
``` JS
console.log(planTwo, possibility);
```
Ta có 2 biến được destructed là planTwo và possibility. Mọi việc có vẻ sáng sủa rồi đó...

...Ta tiếp tục tới biến 'method' và 'rate'
``` JS
const { data: { planTwo: { method, rate } }, possibility } = coolWaysToKillThanos();

console.log(method, rate);
// -> 'Call John Wick', '7/10'
```
2. Destructuring && Renaming
``` JS
const { data: { planTwo: { method: cool, rate: notCool } }, possibility } = coolWaysToKillThanos();
console.log(cool, notCool);
// -> 'Call John Wick', '7/10'
```
3. Destructuring Array
``` JS
const { data: { plans: [plan1, plan2] } } = bestWaysToKillThanos();

console.log(plan1, plan2)
// -> { method: 'Send Ant-man', rate: '9/10'}
// -> { method: "Blow Star-lord's head", rate: '10/10'}
```
Như vậy ta chỉ cần đặt các var của array trong một square bracket '[]' là tất cả sẽ ngăn nắp.

Kết lại, với ví dụ tí hon và fun fun này, mình hi vọng nó dễ hiểu đễ các bạn có thể tiếp thu một khái niệm nhỏ mà hữu dụng trong JS. Chúc các bạn thành công!

[Nguồn](https://viblo.asia/p/tim-hieu-destructuring-nested-objects-trong-javascripts-gAm5ypq8ldb)