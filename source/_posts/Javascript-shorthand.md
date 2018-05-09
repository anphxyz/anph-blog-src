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

## 2. Clone object

``` JS
// shallow clone an object 
let newObj = Object.assign({}, obj);
```
or
``` JS
// deep clone an object
let newObj = JSON.parse(JSON.stringify(obj));
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
`trim()` DIY
``` JS
function trim(x) {
  return x.replace(/^\s+|\s+$/gm,'');
}
 
let str = "       Hello World!        ";
console.log(str)         // ->        Hello World!        
console.log(trim(str));  // -> Hello World!
```
## 5. Cast `arguments` to `Array`
``` JS
let args = Array.prototype.slice.call(arguments);
let args = [].slice.call(arguments);
 
// ES2015
let args = Array.from(arguments);
```

## 6. Max, min in array
``` JS
let numbers = [1, 8 , 10 , -125 , 28 , 100 , 215, -85]; 
let maxInNumbers = Math.max.apply(Math, numbers); 
let minInNumbers = Math.min.apply(Math, numbers);

console.log(maxInNumbers, minInNumbers);
// -> 215 -125
```

## 7. Reset Array
``` JS
let a = [1, 2, 3];

//a = [];//not this
a.length = 0;//use this
console.log(a); // -> []
```

## 8. Delete Array emlement

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


## 9. Use `&&` or `||` in stead of `if` and `if else`
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

## 10. Loop object
``` JS
for (let name in object) {  
    if (object.hasOwnProperty(name)) { 
        // do something with name                    
    }  
}
```
## 11. Clone Array
``` JS
let a = [1, 2, 3];
let b = a.slice();
console.log(b);       // -> [1, 2, 3]
console.log(b === a); // -> false
```

## 12. Join Array
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
## 13. Clone object and array use Spread
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
console.log(arr2); // -> [1, 2];
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
