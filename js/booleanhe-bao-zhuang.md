### 1.包装对象的定义

* 包装对象：数值、字符串、布尔对应NUmber、String、Boolean三个原生对象
* 作为构造函数，带有new时，将原始类型转为对象。作为普通函数时，不带new。将任意类型的值转为原始类型

### 2.原始类型的自动转换

* 原始类型的值可以当作对象调用，自动包装，用完后立刻销毁
* 只读

### 3.自定义方法

* 在原型上添加方法和属性
* 无法用在原始类型上，因为会立马回销毁对象。String.prototype.name =function\(\){}

### 4.Boolean

```js
//所有对象对应的布尔值是true
if (new Boolean(false)) {
  console.log('true');
} // true

if (new Boolean(false).valueOf()) {
  console.log('true');
} // 无输出
```

* 将任意值转为布尔

```js
Boolean(undefined) // false 
Boolean(null) // false
Boolean(0) // false
Boolean('') // false
Boolean(NaN) // false

Boolean(1) // true
Boolean('false') // true
Boolean([]) // true
Boolean({}) // true
Boolean(function () {}) // true
Boolean(/foo/) // true
```

* 双重运算符！也可以将任意值转为布尔
* 有些特殊

```js
!!undefined // false
!!/foo/ // true

if (Boolean(false)) {
  console.log('true');
} // 无输出

if (new Boolean(false)) {
  console.log('true');
} // true

if (Boolean(null)) {
  console.log('true');
} // 无输出

if (new Boolean(null)) {
  console.log('true');
} // true
```



