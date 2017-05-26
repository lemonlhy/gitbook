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
//注意：export要引出去mutations
const state={
    count:1
}
const mutations={
    add(state){
        state.count++;   
    },
    reduce(state){
        state.count--;
    }
}
export default new Vuex.Store({
    state,
    mutations
})

//count.vue
//注意：commit方法放方法名要加上单引号
<template>
    <div>
        <h2>{{msg}}</h2>  
        <hr/>
        <div>{{$store.state.count}}</div> 
        <button @click="$store.commit('add')">+</button>
        <button @click="$store.commit('reduce')">-</button>     
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

### 2.state访问状态对象

#### 2.1 computed计算属性赋值

```js
computed:{
    count(){
        return this.$store.state.count;
    }
}
```

#### 2.2 通过mapState对象赋值

```js
//不太懂
import {mapState} from 'vuex';

computed:mapState({
    count:state=>stete.count
})
```

#### 2.3 通过mapState的数组来赋值

```js
computed:mapState(["count"])
```

### 3.Mutations修改状态





