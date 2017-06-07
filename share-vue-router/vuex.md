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

* $store.commit\(\)

```
<button @click="$store.commit('add')">+</button>
<button @click="$store.commit('reduce')">-</button>

const mutations={
    add(state){
        state.count++;
    },
    reduce(state){
        state.count--;
    }
}
```

* 传值

```
<button @click="$store.commit('add'，1)">+</button>

const mutations={
    add(state,n){
        state.count+=n;
    },
    reduce(state){
        state.count--;
    }
}
```

* 模板获取mutations方法

```
//引入mapMutations
import { mapState,mapMutations } from 'vuex';

//添加script
methods:mapMutations([
    'add','reduce'
])

//采用简便写法
<button @click="reduce">-</button>
```

### 4.getters

* 过滤计算

```js
const getters={
      count:state=>state.count+=10;
}
export default new Vuex.Store({
  state,
  mutations,
  getters
})

//computed只能有一个属性，多写只能最后一个能用，需要加上展开运算符‘...’
computed:{
  ...mapState(["count"]),
  count(){
    retutn this.$store.getters.count;
  }
}
//或者mapGetters简化模板
import { mapState,mapMutations,mapGetters } from 'vuex';
...mapGetters(["count"])
```

### 5.actions

* actions是异步，mutations是同步
* ~~几点疑惑：store到底代表什么。commit对象代表什么~~

```
//声明
const actions = {
  addAction(context){
    context.commit('add',10);    
  },
  reduceAction({commit}){
    commit('reduce');
  }
}
//使用
<p>
  <button @click="addAction">+</button>
  <button @click="reduceAction">-</button>
</p>
methods:{
    ...mapMutations([  
        'add','reduce'
    ]),
    ...mapActions(['addAction','reduceAction'])
}
//异步检验
setTimeOut(()=>{context.commit(reduce)},3000);
console.log('我比reduce提前执行');
```

### 6.module（项目不复杂不建议用）

```
const moduleA={
    state,mutations,getters,actions
}
export default new Vuex.Store({
    modules:{a:moduleA}
})



<h3>{{$store.state.a.count}}</h3>
//想以前的方式直接count
computed:{
    count(){
        return this.$store.state.a.count;
    }
},
```

### 7.vuex api

* state 驱动应用的数据源，单一状态树，每个应用仅包含一个store实例
* view 以声明方式将state映射到视图
* actions 响应view上用户输入导致的状态变化
* ![](/assets/vuex01.png)

* store 仓库，包含大部分状态state



