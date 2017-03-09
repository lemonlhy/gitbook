## 概述

* 构造函数

```js
var Vehicle = function () {
  this.price = 1000;
};
```

> 首字母大写
>
> 内部使用this关键字，所要生成的对象实例
>
> 生成需要用new命令

* new原理

> 创建一个空对象，作为要返回实例
>
> 将空对象的原型，指向构造函数的prototype
>
> 空对象赋值给函数的this

```js
var Vehicle = function () {
  this.price = 1000;
  return 1000;
};

(new Vehicle()) === 1000
// false

var Vehicle = function (){
  this.price = 1000;
  return { price: 2000 };
};

(new Vehicle()).price
// 2000

```

## this关键字





