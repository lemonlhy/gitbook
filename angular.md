### 架构

用 Angular 扩展语法编写 HTML **模板**， 用**组件**类管理这些模板，用**服务**添加应用逻辑， 用**模块**打包发布组件与服务。![](/assets/application.png)八个主要构造块：

* 组件 \(component\)
* 模板 \(template\)
* 元数据 \(metadata\)
* 数据绑定 \(data binding\)
* 指令 \(directive\)
* 服务 \(service\)
* 依赖注入 \(dependency injection\)

### 1.模块

每个 Angular 应用至少有一个模块（[**根模块**](https://angular.cn/docs/ts/latest/guide/appmodule.html)），习惯上命名为AppModule。

Angular 模块（无论是**根模块**还是**特性模块**）都是一个带有@NgModule装饰器的类。

模块库：每个库都有@angular

