#### 1.构造函数

* Array是JavaScript的内置对象，也是一个构造函数
* 不建议使用它生成新数组，直接使用数组字面量

```js
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



