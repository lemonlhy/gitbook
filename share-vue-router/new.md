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

`<router-link to="/">[显示字段]</router-link>`

to：填写router/index.js文件配置的path值

### 2.配置子路由

* App.vue

* components目录

* router/index.js

```js
children:[
{path:'/',component:xxx},
{path:'xx',component:xxx},
]
//后面的子集不用加‘/’
```

### 3.传递参数

#### 3.1 name

* 有子路由的name是没用的
* `<p>{{ $router.name}}</p>`

#### 3.2 :to

`<router-link:to="{name:xxx,params:{key:value}}">valueString</router-link>`

`{{$route.params.username}}`

### 4.单页面多路由区域

* 一个页面有2个以上的
* 非常适合左右分栏，左边操作右边

```js
//App.vue
 <router-view ></router-view>
 <router-view name="left" style="float:left;width:50%;background-color:#ccc;height:300px;"></router-view>
 <router-view name="right" style="float:right;width:50%;background-color:#c0c;height:300px;"></router-view>

//router/index.js
{
  path: '/',
  name: 'Hello',
  components: {
    default:Hello,
    left:test01,
    right:test02
  }
 }
```

### 5.利用url传递参数

* :号传递
* src/router/index.js 配置路由
* 传递的数值在
* 可以使用正则规定传递的数组 path:'/params/:showId\(\d+\)/:name'

### 6.重定向 -redirect

* 设置的路径不一致，但希望跳到同一个页面
* 直接改变路径值

```js
//src/router/index.js
{
    path: '/backhome',
    redirect:'/'
},
{
    path: '/goparmas/:showId(\\d+)/:name',
    redirect:'/params/:showId(\\d+)/:name'
},
```

### 7.alias别名的使用

* 路径名更改
* 根目录'/'更改是没用的

```js
//src/router/index.js
alias:'/test01alias'
```

#### 8.路由过度动画

* transition标签实现动画

```
<transition name="fade">
  <router-view ></router-view>
</transition>
```

* css过渡类名

> 1. fade-enter:进入过渡的开始状态，元素被插入时生效，只应用一帧后立刻删除。
> 2. fade-enter-active:进入过渡的结束状态，元素被插入时就生效，在过渡过程完成后移除。
> 3. fade-leave:离开过渡的开始状态，元素被删除时触发，只应用一帧后立刻删除。
> 4. fade-leave-active:离开过渡的结束状态，元素被删除时生效，离开过渡完成后被删除。

```css
//App.vue
<style>
.fade-enter {
  opacity:0;
}
.fade-leave{
  opacity:1;
}
.fade-enter-active{
  transition:opacity .5s;
}
.fade-leave-active{
  opacity:0;
  transition:opacity .5s;
}
</style>
```

* 过渡模式mode

> 1. in-out :新元素先进入，完成后当前元素离开过渡（默认）
> 2. out-in:当前元素先离开，离开完后新元素过渡进入

### 9.mode设置和404处理

* mode有两个值

> 1.histroy：url正常显示，没有\#号
>
> 2.hash：url有\#号键的hash值

* #### 404

```js
///src/router/index.js
{
   path:'*',//*代表404
   component:Error
}
```

### 10.路由中的钩子

* 进路由之前
* 离开路径之前
* 路由配置文件里  

```js
//src/router/index.js
{
    path: '/params/:showId(\\d+)/:name',
    component:params,
    beforeEnter:(to,from,next)=>{
      console.log(to);
      console.log(form);
      next();
    }
},

// to:路由将要跳转的路径信息
// form:跳转前的路径信息
// next:控制参数
```

* 模板中的钩子函数

```js
//test02.vue
 beforeRouteEnter: (to, from, next) => {
    console.log('准备进入路由模板');
    next();
  },
  beforeRouteLeave: (to, from, next) => {
    console.log('准备离开路由模板');
    next();    
  }
```

### 11.编程式导航

* this.$router.go\(-1\)

```js
  methods:{
    goBack(){
      this.$router.go(-1);
    },
    goInto(){
      this.$router.go(1);
    }
  }
```

* this.$router.push\(‘/xxx ‘\)

```js
 goHome(){
      this.$router.push('/');
    }
```



