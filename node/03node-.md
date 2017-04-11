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







