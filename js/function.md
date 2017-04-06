#### 基础点

* 函数名后紧跟一对圆括号，表示调用
* 第三种函数声明，构造函数

```js
var add = new Function(
  'x',
  'y',
  'return x + y'
);

// 等同于

function add(x, y) {
  return x + y;
}
```

* 采用function命令和赋值语句声明同一个变量，最后采用的总是赋值语句的定义

```js
var f = function() {
  console.log('1');
}

function f() {
  console.log('2');
}

f() // 1
```

* 不能再条件语句中声明函数
* toString\(\)返回函数的源码
* 0，空字符，null的布尔值为false
* 赋值传递不会改变值，传址传递会改变值

```js
var obj = {p: 1};

function f(o) {
  o.p = 2;
}
f(obj);

obj.p // 2
```

* arguments对象

> 函数运行时的所有参数  
> 数组专用的方法不能使用，用apply和call方法转为数组callee返回调用函数本身

* 闭包

> 能够读取其他函数内部变量的函数
>
> 定义在一个函数内部的函数

* 立即启动函数\(原因：js规定如果function出现在行首，一律解释成语句，语句不能以\(\)结尾\)



