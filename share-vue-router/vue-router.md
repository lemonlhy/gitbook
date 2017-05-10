### 1.入门

#### 1.1 安装

`$ npm install vue-router --save-dev`

#### 1.2 router/index.js

```js
export default new Router({
  routes: [              //配置路由，这里是个数组
    {                    //每一个链接都是一个对象
      path: '/',         //链接路径
      name: 'Hello',     //路由名称，
      component: Hello   //对应的组件模板
    }
  ]
})
```

#### 1.3 router-link

* 相当于a标签
* 


