### 1.构造函数

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

### 2.Array.isArray\(\)

判断是否为数组，弥补typeof的不足

### 3.Array实例的方法

1. **valueOf\(\)** 返回数组本身
2. **toString\(\)** 返回数组的字符串形式
3. **push\(\)  **在数组末端添加一个或者多个元素，返回添加后的长度，还可以向对象添加元素，会多一个length属性。_改变原数组_
4. **pop\(\)** 删除最后一个，_改变原数组_
5. **join\(\) **参数为分隔符，生成字符串
6. **concat\(\)** 多个数组合并，变成新数组，_原数组不变_
7. **shift\(\)** 删除第一个，_改变原数组_
8. **unshift\(\)** 一个位置添加，_改变原数组_
9. **reverse\(\)** 颠倒，_改变原数组_
10. **slice\(\)** 提取原数组的一部分 slice\(start-index,upto-index\);
    Array.prototype.slice.call  将对象转为数组，_原数组不变_

11. **splice\(\)**  删除原数组一部分成员，并且可在删除的位置添加，返回值为删除的元素。_改变原数组，第一个参数是位置，从1开始_
12. sort\(\)  排序，_改变原数组_
13. map\(\)  映射。对数组所有成员依次调用一个函数，根据函数结果返回一个新数组,map方法会将其传入三个参数，分别是当前成员、当前位置和数组本身,第二个参数，表示回调函数执行时this所指向的对象。_原数组不变_
14. 


