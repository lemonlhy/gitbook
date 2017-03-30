

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

