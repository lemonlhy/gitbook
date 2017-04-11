### 1.模块路径解析规则

* 内置模块，不做路径解析
* node\_modules目录用于存放模块
* NODE\_PATH环境变量

### 2.包

* 有些复杂的模块由多个子模块组成
* 需要主模块，采用index的命名
* 下面两句等价

```js
var cat = require('/home/user/lib/cat');
var cat = require('/home/user/lib/cat/index');
```

* 如果要自定义需要一个package.json文件

结构：

```
- /home/user/lib/
    - cat/
        + doc/
        - lib/
            head.js
            body.js
            main.js
        + tests/
        package.json
```

package.json

```json
{
    "name": "cat",
    "main": "./lib/main.js"
}
```

#### 4.命令行程序

* node编写东西，要么一个包，要么一个命令行程序
* 规划一个完整的工程目录，例：命令行程序

```
- /home/user/workspace/node-echo/   # 工程目录
    - bin/                          # 存放命令行相关代码
        node-echo
    + doc/                          # 存放文档
    - lib/                          # 存放API相关代码
        echo.js
    - node_modules/                 # 存放三方包
        + argv/
    + tests/                        # 存放测试用例
    package.json                    # 元数据文件
    README.md                       # 说明文件
```

```js
/* bin/node-echo */
var argv = require('argv'),
    echo = require('../lib/echo');
console.log(echo(argv.join(' ')));

/* lib/echo.js */
module.exports = function (message) {
    return message;
};

/* package.json */
{
    "name": "node-echo",
    "main": "./lib/echo.js"
}
```

### 5.版本号

* X.Y.Z 

> * 如果只是修复bug，需要更新Z位。
>
> * 如果是新增了功能，但是向下兼容，需要更新Y位。
>
> * 如果有大变动，向下不兼容，需要更新X位。

**想到了心仪的包名时请提前在NPM上抢注。**

