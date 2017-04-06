#### 1.概述

* new Object \(\) 与 o = {} 等价
* 构造函数的方法

```js
Object.print = function(o){ console.log(o) };

var o = new Object();

Object.print(o) //Object
```

* 实例对象的方法

```js
Object.prototype.print = function(){ console.log(this)};

var o = new Object();

o.print() // Object
```

* Object\(\) 将任意值转为对象，如果是对象则返回原对象

#### 2.静态方法

* **Object.keys\(\) ** **Object.getOwnPropertyNames\(\)**  遍历对象的属性，参数都是一个对象，返回一个数组。前者返回可枚举的属性，后者返回不可枚举

```js
var o = {
  p1: 123,
  p2: 456
};

Object.keys(o)
// ["p1", "p2"]

Object.getOwnPropertyNames(o)
// ["p1", "p2"]

var a = ["Hello", "World"];

Object.keys(a)
// ["0", "1"]

Object.getOwnPropertyNames(a)
// ["0", "1", "length"]
```

#### 3.实例方法

* **Object.prototype.valueOf\(\)  **返回一个对象的值

* **Object.prototype.toString\(\)  **返回对象的字符串形式

```js
//来判断类型，比typeof更准确
Object.prototype.toString.call(2);
var type = function (o){
  var s = Object.prototype.toString.call(o);
  return s.match(/\[object (.*?)\]/)[1].toLowerCase();
};

type({}); // "object"
type([]); // "array"
type(5); // "number"
type(null); // "null"
type(); // "undefined"
type(/abcd/); // "regex"
type(new Date()); // "date"
```



