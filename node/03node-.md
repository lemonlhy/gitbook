### 1.例子

* 小文件拷贝

```js
var fs = require('fs');

function copy(src, dst) {
    fs.writeFileSync(dst, fs.readFileSync(src));
}

function main(argv) {
    copy(argv[0], argv[1]);
}

main(process.argv.slice(2));
```

fs.readFileSync从源路径读取文件，使用fs.wariteFileSync将文件写入目标路径

> process全局变量，process.argv获得命令行参数。
>
> argv\[0\]：node执行程序的绝对路径
>
> argv\[1\]：主模块的绝对路径
>
> argv\[2\]：第一个命令开始的位置

* 大文件

采用fs.createReadStream（a水桶）,fs.createWriteStream（b水桶）创建流，并用pipe（水管）连起来

### 2.API

#### 2.1 Buffer

* 二进制
* 字符串修改是生成新的字符串
* buffer修改是修改的原数据，采用的是指针
* 将JS的数据处理能力从字符串扩展到了任意二进制数据

#### 2.2 Stream

* 数据流的搬运，这样写类似于pipe来做

```js
var rs = fs.createReadStream(src);
var ws = fs.createWriteStream(dst);

rs.on('data', function (chunk) {
    if (ws.write(chunk) === false) {
        rs.pause();
    }
});

rs.on('end', function () {
    ws.end();
});

ws.on('drain', function () {
    rs.resume();
});
```

#### 2.3 File

* 文件属性读写 **fs.stat  fs.chmod  fs.chown**
* 文件内容读写 **fs.readFile  fs.readdir fs.writeFile  fs.mkdir**
* 底层文件操作  **fs.open  fs.read  fs.write  fs.close**
* fs模块所有异步API都有对应的同步版本

#### 2.4 Path

* **path.normalize  **将传入的路径转换为标准路径
* **path.jion  **将传入的多个路径拼接为标准路径

### 3.遍历目录

* 递归
* 遍历（深度遍历和先序遍历）
* 分为同步和异步。（异步看不懂）

### 





