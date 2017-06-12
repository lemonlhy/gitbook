#### 1.概述

* Object本身是构造函数，直接通过它生成新对象
* 作为构造函数时，接受一个参数。参数为对象，返回该对象。参数为原始类型的值，但会值包装的对象
* Object\(\) 将任意值转为对象，如果是对象则返回原对象

```
var o1 = {a:1};
var o2 = new Object(o1);
o1 === o2 //true

 new Object(123) instanceof Number;//true
 new Object(123) instanceof Object;//true
```

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

* 将任意值转为对象，保证某值一定是对象
* > 判断变量是否为对象的一个js函数
  >
  > ```js
  > function isObject (val){
  >     retrun val === Object(val);
  > }
  > ```

#### 2.静态方法

* 部署在Object自身的方法
* **Object.keys\(\) ** **Object.getOwnPropertyNames\(\)**  遍历对象的属性，参数都是一个对象，返回一个数组（对象自身的所有属性名）。前者返回可枚举的属性，后者还返回不可枚举。返回直接定义在某个对象上面的全部属性的名称

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

//计算对象属性个数的方法
Object.keys(o).length
```

#### 3.实例方法

* **Object.prototype.valueOf\(\)  **返回一个对象的值

```js
//js自动类型转换时会默认调用改方法
var o = new Object();
1+o;//"1[object object]"
//定义valueOf，覆盖了Object.prototype.valueOf()
o.valueOf = function(){
    return 1;
}
1+o;//2
```

* **Object.prototype.toString\(\)  **返回对象的字符串形式，默认返回的类型为字符串

```js
//对象用于字符串加法时，会自动调用toString方法
var o = new Object();
o.toString = function(){
  return 'hello';
}
o+' '+'world';//'hello world'

//来判断类型，比typeof更准确，[object object],第二个表示改值的构造函数
Object.prototype.toString.call(2);//"[object Number]"
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
//更完善专门判断某种数据类型的方法
['Null',
 'Undefined',
 'Object',
 'Array',
 'String',
 'Number',
 'Boolean',
 'Function',
 'RegExp',
 'NaN',
 'Infinite'
].forEach(function (t) {
  type['is' + t] = function (o) {
    return type(o) === t.toLowerCase();
  };
});

type.isObject({}) // true
type.isNumber(NaN) // true
type.isRegExp(/abc/) // true
```



