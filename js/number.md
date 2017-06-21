### 1.属性

```js
Number.POSITIVE_INFINITY // Infinity
Number.NEGATIVE_INFINITY // -Infinity
Number.NaN // NaN

Number.MAX_VALUE
// 1.7976931348623157e+308
Number.MAX_VALUE < Infinity
// true

Number.MIN_VALUE
// 5e-324
Number.MIN_VALUE > 0
// true

Number.MAX_SAFE_INTEGER // 9007199254740991
Number.MIN_SAFE_INTEGER // -9007199254740991
```

### 2.方法

* Number.prototype.toString\(\)

```js
(10).toString(); //"10"
(10).toString(2); //"1010"
//以下写法都可以，只要不让js解析为小数点
10..toString();
10 .toString();
10.0.toString();
10['toString']();

```

* Number.prototype.toFixed\(\)

```js
//转为指定位数的小数，返回小数对应的字符串,0-20
(10).toFixed(2);//"10.00"
```

* Number.prototype.toExponential\(\)

```js
//转为科学计数法,0-20
(10).toExponential();//"1e+1"
```

* Number.peototype.toPrecision\(\)

```js
//转为指定位数的有效数字,1-21,用于四舍五入不太靠谱
(12.34).toPrecision(1) // "1e+1"
(12.34).toPrecision(2) // "12"
(12.34).toPrecision(3) // "12.3"
(12.34).toPrecision(4) // "12.34"
```

### 3.自定义方法

* 在Number.prototype后面定义





