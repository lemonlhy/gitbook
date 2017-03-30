## 1.安装注意

如果在一个模块化工程中使用它，必须要通过Vue.use\(\)明确安装路由

```js
import Vue from 'vue'
import VueRouter from 'vue-router'

Vue.use(VueRouter)
```

如果你想使用最新的开发版，就得从 GitHub 上直接 clone，然后自己 build 一个vue-router。

```
git clone https://github.com/vuejs/vue-router.git node_modules/vue-router
cd node_modules/vue-router
npm install
npm run build
```

## 2.基础

模块化配置

```js
// 1. 定义（路由）组件。
// 可以从其他文件 import 进来
const Foo = { template: '<div>foo</div>' }
const Bar = { template: '<div>bar</div>' }

// 2. 定义路由
// 每个路由应该映射一个组件。 其中"component" 可以是
// 通过 Vue.extend() 创建的组件构造器，
// 或者，只是一个组件配置对象。
const routes = [
  { path: '/foo', component: Foo },
  { path: '/bar', component: Bar }
]

// 3. 创建 router 实例，然后传 `routes` 配置
// 你还可以传别的配置参数, 不过先这么简单着吧。
const router = new VueRouter({
  routes // （缩写）相当于 routes: routes
})

// 4. 创建和挂载根实例。
// 记得要通过 router 配置参数注入路由，
// 从而让整个应用都有路由功能
const app = new Vue({
  router
}).$mount('#app')
```

> 注意：提醒一下，当使用路由参数时，例如从/user/foo导航到user/bar，**原来的组件实例会被复用**。因为两个路由都渲染同个组件，比起销毁再创建，复用则显得更加高效。**不过，这也意味着组件的生命周期钩子不会再被调用**

* router.push\(location\) 等同于 &lt;router-link :to="..."&gt;

* router.replace\(location\) 不会向history添加新纪录，替换当前history记录

* router.go\(n\) history向前或者后退

* 重定向：（别名用户访问/a 替换为/b）

* ```js
  const router = new VueRouter({
    routes: [
      { path: '/a', redirect: '/b' }
    ]
  })

  //别名
  const router = new VueRouter({
    routes: [
      { path: '/a', component: A, alias: '/b' }
    ]
  })
  ```

# 快速入门

[http://www.cnblogs.com/axl234/p/5899952.html](http://www.cnblogs.com/axl234/p/5899952.html)



