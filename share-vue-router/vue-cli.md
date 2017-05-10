### 1.开始吧

#### 1.1 安装

* 安装

`$ npm install vue-cli -g`

* 查看版本

`$ vue -V`

#### 1.2 初始化

`$ vuei init <template-name> <project-name>`

> &lt;template-name&gt;:
>
> * webpack:webpack+vue-loader 热加载，linting,检测，css扩展
> * webpack-simple:webpack+vue-loader
> * browserify:browsweify+vueify 热加载，linting,检测
> * browser-simple:browsweify+vueify

* Project name :项目名称 ，如果不需要更改直接回车就可以了。注意：这里不能使用大写，所以我把名称改成了vueclitest
* Project description:项目描述，默认为A Vue.js project,直接回车，不用编写。
* Author：作者，如果你有配置git的作者，他会读取。
* Use ESLint to lint your code? 是否用ESLint来限制你的代码错误和风格。我们这里不需要输入n，如果你是大型团队开发，最好是进行配置。
* setup unit tests with  Karma + Mocha? 是否需要安装单元测试工具Karma+Mocha，我们这里不需要，所以输入n。
* Setup e2e tests with Nightwatch?是否安装e2e来进行用户行为模拟测试，我们这里不需要，所以输入n。

### 2.目录结构

```
|-- build                            // 项目构建(webpack)相关代码
|   |-- build.js                     // 生产环境构建代码
|   |-- check-version.js             // 检查node、npm等版本
|   |-- dev-client.js                // 热重载相关
|   |-- dev-server.js                // 构建本地服务器
|   |-- utils.js                     // 构建工具相关
|   |-- webpack.base.conf.js         // webpack基础配置
|   |-- webpack.dev.conf.js          // webpack开发环境配置
|   |-- webpack.prod.conf.js         // webpack生产环境配置
|-- config                           // 项目开发环境配置
|   |-- dev.env.js                   // 开发环境变量
|   |-- index.js                     // 项目一些配置变量
|   |-- prod.env.js                  // 生产环境变量
|   |-- test.env.js                  // 测试环境变量
|-- src                              // 源码目录
|   |-- components                     // vue公共组件
|   |-- store                          // vuex的状态管理
|   |-- App.vue                        // 页面入口文件
|   |-- main.js                        // 程序入口文件，加载各种公共组件
|-- static                           // 静态文件，比如一些图片，json数据等
|   |-- data                           // 群聊分析得到的数据用于数据可视化
|-- .babelrc                         // ES6语法编译配置
|-- .editorconfig                    // 定义代码格式
|-- .gitignore                       // git上传需要忽略的文件格式
|-- README.md                        // 项目说明
|-- favicon.ico 
|-- index.html                       // 入口页面
|-- package.json                     // 项目基本信息
```

#### package.json

```
"scripts": {
    "dev": "node build/dev-server.js",
    "build": "node build/build.js",
    "test": ""
  },
  // node run dev 相当于执行了 node build/dev-server.js
  //dependencies字段指项目运行时所依赖的模块；
  //devDependencies字段指定了项目开发时所依赖的模块；
```

#### webpack

#### .babelrc

#### .editorconfig 编码规范

```
root = true

[*]    // 对所有文件应用下面的规则
charset = utf-8                    // 编码规则用utf-8
indent_style = space               // 缩进用空格
indent_size = 2                    // 缩进数量为2个空格
end_of_line = lf                   // 换行符格式
insert_final_newline = true        // 是否在文件的最后插入一个空行
trim_trailing_whitespace = true    // 是否删除行尾的空格
```

### 3.解读模板

#### 3.1 npm run bulid

* 执行完后生成了dist文件夹，里面就是要上传到服务器的文件

#### 3.2 main.js

* 入口文件

#### 3.3 app.vue

* 三部分 template script style
* &lt;style scoped&gt;只对当前页面



