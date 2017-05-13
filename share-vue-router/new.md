### 1.入门

#### 1.1安装

`$ npm install vue-router --save-dev`

#### 1.2router/index.js

```
export
default
new
Router
(
{

  routes
:
[
//配置路由，这里是个数组
{
//每一个链接都是一个对象

      path
:
'/'
,
//链接路径

      name
:
'Hello'
,
//路由名称，

      component
:
 Hello   
//对应的组件模板
}
]
}
)
```

#### 1.3router-link

* 相当于a标签

`<router-linkto="/">[显示字段]</router-link>`

to：填写router/index.js文件配置的path值

### 2.配置子路由

* App.vue

* components目录

* router/index.js

```
children
:
[
{
path
:
'/'
,
component
:
xxx
}
,
{
path
:
'xx'
,
component
:
xxx
}
,
]
//后面的子集不用加‘/’
```

### 3.传递参数

#### 3.1name

* 有子路由的name是没用的
* `<`
  `p`
  `>`
  `{{ $router.name}}`
  `<`
  `/p`
  `>`

#### 3.2:to

`<router-link:to="{name:xxx,params:{key:value}}">valueString</router-link>`

`{{$route.params.username}}`

### 4.单页面多路由区域

* 一个页面有2个以上的
* 非常适合左右分栏，左边操作右边

```
//App.vue
<
router
-
view 
>
<
/
router
-
view
>
<
router
-
view name
=
"left"
 style
=
"float:left;width:50%;background-color:#ccc;height:300px;"
>
<
/
router
-
view
>
<
router
-
view name
=
"right"
 style
=
"float:right;width:50%;background-color:#c0c;height:300px;"
>
<
/
router
-
view
>
//router/index.js
{

  path
:
'/'
,

  name
:
'Hello'
,

  components
:
{
default
:
Hello
,

    left
:
test01
,

    right
:
test02
  
}
}
```

### 5.利用url传递参数

* :号传递
* src/router/index.js 配置路由
* 传递的数值在
* 可以使用正则规定传递的数组 path:'/params/:showId\(\d+\)/:name'


