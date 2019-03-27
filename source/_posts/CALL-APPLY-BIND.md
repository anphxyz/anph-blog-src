---
title: 'CALL, APPLY & BIND'
date: 2018-06-01 09:53:32
tags: javascript
category: javascript

---
## CALL
  1. Call invokes the function and allows you to pass in arguments one by one.
  2. Gọi hàm và cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy (Comma)
``` JS
  var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
  var person2 = {firstName: 'Kelly', lastName: 'King'};

  function say(greeting1, greeting2) {
  console.log(greeting1 + ',' + greeting2 + ' ' + this.firstName + ' ' + this.lastName);
  }

  say.call(person1, 'Hello', 'Good morning'); // => Hello,Good morning Jon Kuperman
  say.call(person2, 'Hello', 'Good morning'); // => Hello,Good morning Kelly King
```
## APPLY
  1. Apply invokes the function and allows you to pass in arguments as an array.
  2. Gọi hàm và cho phép bạn truyền vào một object và các đối số thông qua mảng (Array)
``` JS
  var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
  var person2 = {firstName: 'Kelly', lastName: 'King'};

  function say(greeting0, greeting1) {
  console.log(greeting0 + ',' + greeting1 + ' ' + this.firstName + ' ' + this.lastName);
  }

  say.apply(person1, ['Hello', 'Good moring']); // => Hello,Good moring Jon Kuperman
  say.apply(person2, ['Hello', 'Good moring']); // => Hello,Good moring Kelly King
```
## BIND
  1. Bind returns a new function, allowing you to pass in a this array and any number of arguments.
  2. Trả về một hàm số mới, cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy.
``` JS
var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
var person2 = {firstName: 'Kelly', lastName: 'King'};

function say(greeting0, greeting1) {
 console.log(greeting0 + ',' + greeting1 + ' ' + this.firstName + ' ' + this.lastName);
}

var sayHelloJon = say.bind(person1, 'Hello', 'Good morning');
var sayHelloKelly = say.bind(person2, 'Hello', 'Good morning');

sayHelloJon(); // => Hello,Good morning Jon Kuperman
sayHelloKelly(); // => Hello,Good morning Kelly King
```

[https://codeplanet.io/javascript-apply-vs-call-vs-bind/](https://codeplanet.io/javascript-apply-vs-call-vs-bind/)