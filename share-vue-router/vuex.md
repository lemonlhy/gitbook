### 1.简介

* 数据仓库，状态管理器
* 状态：共用的属性或者数据，每打开一个页面就要向服务器请求状态
* 引入vuex

```
$ npm install vuex --save

//store.js
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
```

* 小demo

```js
//store.js
const state={
    count:1
}
export default new Vuex.Store({
    state
})

//count.vue
<template>
    <div>
        <h2>{{msg}}</h2>  
        <hr/>
        <div>{{$store.state.count}}</div>      
    </div>
</template>
<script>
    import store from '@/store';
    export default{
        data(){
            return{
                msg:'Hello Vuex',
 
            }
        },
        store
        
    }
</script>

```



