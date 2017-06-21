### 1.构造函数

* Array是JavaScript的内置对象，也是一个构造函数
* 不建议使用它生成新数组，直接使用数组字面量

```js
var arr = new Array(2);
//等同于
var arr = Array(2);
//Array对于参数不一致就会产生不一样的效果，所以建议不适用他生成新数组
// bad
var arr = new Array(1, 2);

// good
var arr = [1, 2];
```

* 构造一个数组，读到undefined，但没有值，有length长，但取不到健名

```js
var arr = new Array(3);
arr.length // 3

arr[0] // undefined
arr[1] // undefined
arr[2] // undefined

0 in arr // false
1 in arr // false
2 in arr // false
```

### 2.Array.isArray\(\)

判断是否为数组，弥补typeof的不足

### 3.Array实例的方法

* **valueOf\(\)** 返回数组本身
* **toString\(\)** 返回数组的字符串形式
* **push\(\)  **在数组末端添加一个或者多个元素，返回添加后的长度，还可以向对象添加元素，会多一个length属性。_**改变原数组 **_

```js
//合并两个数组
var a = [1,2];
var b = [4,5];
Array.prototype.push.apply(a,b);
//或者
a.push.apply(a,b)
```

* **pop\(\)** 删除最后一个，_**改变原数组**_
* **join\(\) **参数为分隔符，生成字符串，默认逗号

```js
//这里必须要length
var obj = { 0: 'a', 1: 'b', length: 2 };
Array.prototype.join.call(obj, '-')
```

* **concat\(\)** 多个数组合并，变成新数组，如无参数，则返回当前数组的一个浅拷贝，不管有没有参数，都是返回该数组的引用。_**原数组不变**_

```js
var obj = { a:1 };
var oldArray = [obj];

var newArray = oldArray.concat();

obj.a = 2;
newArray[0].a // 2
//将对象合并为数组
[].concat.call({a: 1}, {b: 2})
// [{ a: 1 }, { b: 2 }]

[].concat.call({a: 1}, [2])
// [{a: 1}, 2]

[2].concat({a: 1})
// [2, {a: 1}]
```

* **shift\(\)** 删除第一个，_**改变原数组**_
* **unshift\(\)** 第一个位置添加，可多个。返回数组长度。_**改变原数组**_
* **reverse\(\)** 颠倒，_**改变原数组**_
* **slice\(\)** 提取原数组的一部分，包括第一个不包括第二个。slice\(start\__index,upto_\_index\); Array.prototype.slice.call  将类似数组的对象转为数组，_**原数组不变**_
* **splice\(\)**  删除原数组一部分成员，并且可在删除的位置添加，返回值为删除的元素。_第一个参数是位置，第二个是被删除的元素个数。splice\(index,count\_to\_remove,addElement1,addElement2\)**改变原数组**_
* **sort\(\)  **默认按字典顺序排序。函数参数，&gt;0第一个在第二个元素后面，_**改变原数组**_
* **map\(\) ** 映射,遍历数组成员。对数组所有成员依次调用一个函数，根据函数结果返回一个新数组,map方法_第一个参数_可以是函数，函数会将其传入三个参数，分别是当前成员、当前位置和数组本身,第_二个参数，_表示回调函数执行时this所指向的对象。map还可以用于字符串，用call间接使用。~~this绑定。~~_**原数组不变**_

* **split\(\) **字符串分割成字符串数组

* **forEach\(\) **遍历数组成员，一般不返回值，其他和map一样，注意循环没法中断。~~this绑定~~

* **filter\(\) **参数是一个函数，返回结果为true组成一个数组。~~this绑定。~~_**原数组不变**_

* **some\(\),every\(\) **判断数组成员是否符合某种条件。参数为函数，返回一个布尔。some只要有返回为true则为true，every要都是true。空数组，some返回false，every返回true，回调函数不执行

* **reduce\(\),reduceRight\(\) **依次处理，最终累计为一个值。函数，四个参数，1.累积变量，必须，默认第一个。2.当前变量，必须，默认第二个。3.当前位置。4.原数组。

* **indexOf\(\),lastIndexOf\(\) **前者：返回给顶元素在数组第一次出现的位置，没有返回-1.第二个参数表示搜索的开始位置。后者：最后一次出现

> 改变原数组：push\(\)、pop\(\)、concat\(\)、shift\(\)、unshift\(\)、reverse\(\)、splice\(\)、sort\(\)、filter\(\)、
>
> 不改变原数组：concat\(\)、slice\(\)、map\(\)、forEach\(\)、
>
> 浅拷贝：
>
> 深拷贝：

#### 4. 类似数组的对象

典型的是函数的arguments对象，以及大多数dom元素，还有字符串

```js
// arguments对象
function args() { return arguments }
var arrayLike = args('a', 'b');

arrayLike[0] // 'a'
arrayLike.length // 2
arrayLike instanceof Array // false

// DOM元素集
var elts = document.getElementsByTagName('h3');
elts.length // 3
elts instanceof Array // false

// 字符串
'abc'[1] // 'b'
'abc'.length // 3
'abc' instanceof Array // false
```

#### 5.in

检查某个键名是否存在

```js
var arr = [ 'a', 'b', 'c' ];
2 in arr  // true
'2' in arr // true
4 in arr // false

var arr = [];
arr[100] = 'a';

100 in arr // true
1 in arr // false
```

不推荐用for..in遍历数组

length属性不过滤空位

空位就是数组没有这个元素，所以不会被遍历到，而undefined则表示数组有这个元素，值是undefined，所以遍历不会跳过

