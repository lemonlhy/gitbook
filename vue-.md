# 插件

## 开发插件

插件的范围：

1. 添加全局方法或者属性，如: [vue-element](https://github.com/vuejs/vue-element)
2. 添加全局资源：指令/过滤器/过渡等，如 [vue-touch](https://github.com/vuejs/vue-touch)
3. 通过全局 mixin方法添加一些组件选项，如: [vuex](https://github.com/vuejs/vuex)
4. 添加 Vue 实例方法，通过把它们添加到 Vue.prototype 上实现。
5. 一个库，提供自己的 API，同时提供上面提到的一个或多个功能，如 [vue-router](https://github.com/vuejs/vue-router)

Vue.js 的插件有一个公开方法install。这个方法的第一个参数是Vue构造器 , 第二个参数是一个可选的选项对象:

```js
MyPlugin.install = function (Vue, options) {
  // 1. 添加全局方法或属性
  Vue.myGlobalMethod = function () {
    // 逻辑...
  }
  // 2. 添加全局资源
  Vue.directive('my-directive', {
    bind (el, binding, vnode, oldVnode) {
      // 逻辑...
    }
    ...
  })
  // 3. 注入组件
  Vue.mixin({
    created: function () {
      // 逻辑...
    }
    ...
  })
  // 4. 添加实例方法
  Vue.prototype.$myMethod = function (options) {
    // 逻辑...
  }
}
```

> [Vue.directive\(id,\[definition\]\)](http://cn.vuejs.org/v2/api/?#Vue-directive)
>
> 注册或获取全局指令

> [Vue.mixin\(mixin\)](http://cn.vuejs.org/v2/api/?#Vue-mixin)
>
> 全局注册一个混合，影响注册之后所有创建的每个 Vue 实例。插件作者可以使用混合，向组件注入自定义的行为。**不推荐在应用代码中使用**。

## 使用插件

通过全局方法 Vue.use\(\) 使用插件:

```js
// 调用 `MyPlugin.install(Vue)`
Vue.use(MyPlugin)

//也可以传入一个选项对象
Vue.use(MyPlugin, { someOption: true })

```



