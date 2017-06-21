### 1.new Date\(\)

* new Date\(milliseconds\) Unix\*1000

```js
// 1970年1月2日的零时
var Jan02_1970 = new Date(3600 * 24 * 1000);
// Fri Jan 02 1970 08:00:00 GMT+0800 (CST)

// 1969年12月31日的零时
var Dec31_1969 = new Date(-3600 * 24 * 1000);
// Wed Dec 31 1969 08:00:00 GMT+0800 (CST)
```

* new Date\(datastring\)

```js
new Date('January 6, 2013');
// Sun Jan 06 2013 00:00:00 GMT+0800 (CST)
new Date('2013-2-15')
// Fri Feb 15 2013 00:00:00 GMT+0800 (CST)
```

* new Date\(year,month\[,day,hours,minutes,seconds,ms\]\)

### 2.日期的运算

* 减法为两个时间差
* 加法为字符串相加

### 3.静态方法

* **Date.now\(\)** 距离那个时间的毫秒数
* **window.performance.now\(\)** 页面加载到命令运行已经过去的时间
* **Date.parse\(\)** 解析日期字符串，返回毫秒数
* **Date.UTC\(\)** 看看就行

### 4.实例方法

* to类

  * **Date.prototype.toString\(\) **返回一个完整的日期字符串，默认会调用

  * **Date.prototype.toUTCString\(\)** 返回对应UTC时间，比北京时间晚8个小时

  * **Date.prototype.toISOString\(\)** 对应时间的ISO8601写法，返回的UTC时区

  * **Date.prototype.toJSON\(\)** 符合json格式的iso日期字符串与上一个结果完全相同，那为何要整两个方法出来，不懂

  * **Date.prototype.toDateString\(\)** 日期字符串

  * **Date.prototype.toTimeString\(\)** 时间字符串

  * **Date.prototype.toLocaleDateString\(\)** 日期的当地写法

  * **Date.prototype.toLocaleTimeString\(\)**  时间的当地写法

* get类

  * **getTime\(\)**：返回距离1970年1月1日00:00:00的毫秒数，等同于valueOf方法

  * **getDate\(\)**：返回实例对象对应每个月的几号（从1开始）

  * **getDay\(\)**：返回星期几，星期日为0，星期一为1
  * **getYear\(\)**：返回距离1900的年数。
  * **getFullYear\(\)**：返回四位的年份。
  * **getMonth\(\)**：返回月份（0表示1月，11表示12月）。
  * **getHours\(\)**：返回小时（0-23）。
  * **getMilliseconds\(\)**：返回毫秒（0-999）。
  * **getMinutes\(\)**：返回分钟（0-59）。

  * **getSeconds\(\)**：返回秒（0-59）

  * **getTimezoneOffset\(\)**：返回当前时间与UTC的时区差异，以分钟表示，返回结果考虑到了夏令时因素。

* set类

  * **setDate\(date\)**：设置实例对象对应的每个月的几号（1-31），返回改变后毫秒时间戳。
  * **setYear\(year\)**: 设置距离1900年的年数。
  * **setFullYear\(year \[, month, date\]\)**：设置四位年份。
  * **setHours\(hour \[, min, sec, ms\]\)**：设置小时（0-23）。
  * **setMilliseconds\(\)**：设置毫秒（0-999）。
  * **setMinutes\(min \[, sec, ms\]\)**：设置分钟（0-59）。
  * **setMonth\(month \[, date\]\)**：设置月份（0-11）。
  * **setSeconds\(sec \[, ms\]\)**：设置秒（0-59）。
  * **setTime\(milliseconds\)**：设置毫秒时间戳。



