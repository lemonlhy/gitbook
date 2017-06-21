### 1.涵义

* this总是返回一个对象，属性或者方法当前所在的对象
* this是动态切换的

### 2.使用场合

* 全局-&gt;顶层对象window

```js
//指向window
this === window // true

function f() {
  console.log(this === window); // true
}
```

* 构造函数-&gt;实例对象
* 对象的方法，a对象赋值给b对象，a中的this就指向b,
* 解释：obj和obj.foo在不同的内存位置，只有是obj.foo\(\)这样调用是从obj开始的。所以this是指向obj，但直接使用obj.foo，没有从obj开始，则是指向了全局环境

```js
var obj={
    foo:function(){
        console.log(this);
    }
}
obj.foo() //obj
//其他的都指向代码块当前所在对象
(obj.foo = obj.foo)() //window
(false || obj.foo)() //window
(1,obj.foo)() //window
//等用于,解释：obj和obj.foo在不同的内存位置，
// 情况一
(obj.foo = function () {
  console.log(this);
})()

// 情况二
(false || function () {
  console.log(this);
})()

// 情况三
(1, function () {
  console.log(this);
})()
```

* Node中this分两种。全局指向global，模块指向module.exports

### 3.使用注意点

* 避免duo'ceng



