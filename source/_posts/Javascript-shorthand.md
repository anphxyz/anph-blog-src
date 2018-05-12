---
title: Javascript shorthand
date: 2018-05-08 13:47:49
tags:
---
## 1. Play with `.bind()`
``` JS
// document.querySelector
let $ = document.querySelector.bind(document);
// 1. Usage
let ele1 = $("#id1");
let ele2 = $(".class2");
let ele3 = $("div.user-panel.main input[name='login']");

// 2. console.log
let log = console.log.bind(document);
log('hello'); // -> hello
```

## 2. Clone object, array
a. Object
``` JS
// shallow clone an object 
let newObj = Object.assign({}, obj);
```
or
``` JS
// deep clone an object
let newObj = JSON.parse(JSON.stringify(obj));
```
b. Array
``` JS
  let a = [1, 2, 3];
  let b = a.slice();
  console.log(b);       // -> [1, 2, 3]
  console.log(b === a); // -> false
```
## 3. Swap value

``` JS
let x = 1, y = 2;
console.log(x, y); // 1, 2

[x, y] = [y, x];
console.log(x, y); // 2, 1
```

## 4. Random with range
``` JS
let random = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;
 
// Usage
let a = random(1, 100);
```
## 5. `trim()` DIY
``` JS
function trim(x) {
  return x.replace(/^\s+|\s+$/gm,'');
}
 
let str = "       Hello World!        ";
console.log(str)         // ->        Hello World!        
console.log(trim(str));  // -> Hello World!
```
## 6. Cast `arguments` to `Array`
``` JS
let args = Array.prototype.slice.call(arguments);
let args = [].slice.call(arguments);
 
// ES2015
let args = Array.from(arguments);
```

## 7. Max, min in array
``` JS
let numbers = [1, 8 , 10 , -125 , 28 , 100 , 215, -85]; 
let maxInNumbers = Math.max.apply(Math, numbers); 
let minInNumbers = Math.min.apply(Math, numbers);

console.log(maxInNumbers, minInNumbers);
// -> 215 -125
```

## 8. Reset Array
``` JS
let a = [1, 2, 3];

//a = [];//not this
a.length = 0;//use this
console.log(a); // -> []
```

## 9. Delete Array emlement

a. Wrong way
```JS
let arr = ["a", 1, -5, "cde"];
console.log(arr);        // -> ["a", 1, -5, "cde"]
 
delete arr[2];
console.log(arr);        // -> ["a", 1, undefined, "cde"]
console.log(arr.length); // -> 4
```
b. Right way
```JS
let arr = ["a", 1, -5, "cde"];
console.log(arr);        // -> ["a", 1, -5, "cde"]
 
arr.splice(2, 1);
console.log(arr);        // -> ["a", 1, "cde"]
console.log(arr.length); // -> 3
```


## 10. Use `&&` or `||` instead of `if` and `if else`
a. `if`
``` JS
let a = 10;
if (a === 10) console.log("a === 10"); // -> a === 10
if (a !== 5) console.log("a !== 5"); // -> a !== 5
```
->
``` JS
let a = 10;
a === 10 && console.log("a === 10"); // -> a === 10
a === 5 || console.log("a !== 5");   // -> a !== 5
```
b. `if else`
``` JS
let a = 10;
if (a === 5) console.log("a === 5");
else console.log("a !== 5");
```
->
``` JS
let a = 10;
a === 5 && console.log("a === 5") || console.log("a !== 5");
```

## 11. Loop object
``` JS
for (let name in object) {  
    if (object.hasOwnProperty(name)) { 
        // do something with name                    
    }  
}
```
## 12. Clone object and array use Spread
  a. Clone object:
  ``` JS
  let obj = {a: 1, b: 2};
  let obj2 = {...obj};
  console.log(obj2); // -> {a: 1, b: 2};
  ```
  b. Clone array:
  ``` JS
  let arr = [1, 2];
  let arr2 = [...arr];
  console.log(arr2); // => [1, 2];
  ```
## 13. Join Array
``` JS
let one = ['a', 'b', 'c']
let two = ['d', 'e', 'f']
let three = ['g', 'h', 'i']

// Old way #1
const result1 = one.concat(two, three);
console.log(result1);
// -> ["a", "b", "c", "d", "e", "f", "g", "h", "i"]

// Old way #2
const result2 = [].concat(one, two, three);
console.log(result2);
// -> ["a", "b", "c", "d", "e", "f", "g", "h", "i"]

// New
const result3 = [...one, ...two, ...three];
console.log(result3);
// -> ["a", "b", "c", "d", "e", "f", "g", "h", "i"]
```
## 14. Set key from variable
``` JS
let myKey = 'key3';
let obj = {
    key1: 'One',
    key2: 'Two'
};
obj[myKey] = 'Three';
console.log(obj); // -> {key1: "One", key2: "Two", key3: "Three"}
```
->
``` JS
let myKey = 'key3';
let obj = {
    key1: 'One',
    key2: 'Two',
    [myKey]: 'Three'
};
console.log(obj); // -> {key1: "One", key2: "Two", key3: "Three"}
```

## 15. Cast value
``` JS
if (variable1 !== null || variable1 !== undefined || variable1 !== '') {
     let variable2 = variable1;
}
```
->
``` JS
const variable2 = variable1  || 'new';
```
## 16. Object Property
``` JS
const obj = { x:x, y:y };
```
->
``` JS
const obj = { x, y };
```

## 17. Method
``` JS
var obj = {
  foo: function() {
    /* code */
  },
  bar: function() {
    /* code */
  }
};
```
->
``` JS
var obj = {
  foo() {
    /* code */
  },
  bar() {
    /* code */
  }
};
```

## 18. Parse Int (*) be careful
``` JS
let a = '123', b = '123a';
// Normal
console.log(parseInt(a), parseInt(b));//-> 123 123

//Advance
console.log(+a, +b);//-> 123 NaN

```
## 19. Verify variable (cast to boolean)
6 fasly value: `false, null, 0, '', undefined, NaN` will cast to `false` else cast to `true`
``` JS
if(typeof a !== 'undefined' && a !== null){
  //
}
```
->
``` JS
if(!!a){

}
```
## 20. Rest và spread

Rest – phần còn lại – là một bổ sung của phân rã biến mảng ở trên. Bạn dùng ba dấu chấm ... để biểu thị rest.
``` JS
const [first, second, ...others] = [1, 2, 3, 4, 5]

console.log(first, second, others)
// 1
// 2
// [3, 4, 5]
```

Rest cũng được dùng khi khai báo hàm có thể nhận nhiều tham số
``` JS
const foo = (...args) => console.log('You passed', args)
console.log(foo(1, 2, 3)) // You passed[ 1, 2, 3 ]
const bar = (x, y, ...rest) => console.log(rest, x, y)
```
Bạn lưu ý biến args ở trên khác với biến đặc biệt arguments vốn có sẵn bên trong hàm. `arguments` là một đối tượng giống Array, với những thuộc tính đặc biệt như `callee`, trong khi `args` chỉ là một mảng bình thường.

Spread – rải – là thao tác ngược lại với rest, giúp bạn kết hợp một mảng đã có sẵn thành mảng mới.
``` JS
const arr = [3, 4, 5]
const newArr = [1, 2, ...arr, 6]
console.log(newArr) // [1, 2, 3, 4, 5, 6]
Spread rất hữu ích để thay thế các thao tác thên mảng, như .concat().

const head = [1, 2]
const tail = [3, 4, 5]
console.log([...head, ...tail]) // [1, 2, 3, 4, 5]
Spread cũng rất ngon khi thay thế cho Function.prototype.apply.

const mul = (x, y, z) => x * y * z
const params = [1, 2, 3]

// Thay thế cho
// mul.prototype.apply(null, params)
mul(...params)
```

Rest/spread cũng có thể hoạt động trên object, tương tự như `Object.assign()`, nhưng bạn lưu ý tính năng vẫn đang được đề xuất (proposal). Về phía trình duyệt, có Firefox và Chrome là hỗ trợ, trong khi Edge và Safari hoàn toàn không hoạt động.
```JS
const user = { name: 'John' }

// ES5
const userWithAgeEs5 = Object.assign({}, user, { age: 21 })

// Thời đại mới với spread
const userWithAge = { ...user, age: 21 }
console.log(userWithAge) // { name: 'John', age: 21 }

// Và rest
const { name, ...others } = userWithAge
console.log(others) // { age: 21 }
```

## 21. Create & set key by variable
``` JS
const attr = 'foo'
const year = 2017
const obj = { [attr]: 1, ['now' + year]: 'wow' }
console.log(obj) // { foo: 1, now2017: 'wow' }
```