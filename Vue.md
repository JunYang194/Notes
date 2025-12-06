# Vue

```vue
# 防连点
v-no-more-click

# 安装
npm install -g vue                        > 安装 Vue
npm istall -g @vue/cli                    > 安装 Vue 脚手架
vue create 项目名                          > 创建 Vue 项目
npm istall                                > 创建 node_modules 包
npm run start                             > 启动 Vue 项目

# 脚手架选项
1. > Manually select features             > 手工选择功能
2. (*) Babel                              > 不要 Babel 将新的语法翻译为ES5的语法，让大多数浏览器都能支持
   (*) Router                             > 单页面应用的核心组件
   (*) Vuex                               > 选用 Vuex 核心插件
3. > N                                    > 是否使用history模式作为路由器的导航方式
4. > In package.json                      > 放在一个package.json文件中
5. > N                                    > 是否将当前选择作为将来项目的默认配置

# src -> main.js
import Header from "@/components/Header"  > 导入页头组件
Vue.component("my-header", Header);       > 把导入的页头组件转为全局组件

# new Vue()
<script>
export default {
  name: "",                               > 定义当前组件的名称
  mixins: [],                             > 导入mixin
  components: {},                         > 导入子组件
  props: {},                              > 接收其它页面组件的传参
  filters: {},                            > 过滤器
  computed: {},                           > 计算变量（支持缓存，不支持异步）
  watch: {},                              > 监视变量（不支持缓存，支持异步）
  data(){ return {} },                    > 保存界面中的变量
  methods: {}                             > 保存界面中的函数
  beforeCreate(){},                       > 组件实例化对象前
  created(){},                            > 组件实例化对象后
  beforeMount(){},                        > 组件初始化渲染前
  mounted(){},                            > 组件初始化渲染后
  beforeUpdate(){},                       > 组件重新渲染前
  updated(){},                            > 组件重新渲染后
  beforeDestroy(){},                      > 组件实例化对象销毁前
  destroyed(){},                          > 组件实例化对象销毁后
  activated(){},                          > 缓存组件并初始显示后激活时调用
  deactivated(){}                         > 缓存组件并初始显示后失活时调用
}
</script>
```

# Vuex

```vue
# 安装
npm istall --save vuex                # 安装 Vuex 核心插件
npm install --save vuex-persist  # 安装 Vuex-persist 持久化存储

<!-- Vuex 示例（main.js ） -->
<script>
new Vue({
  el: '#app',
  router,
  //使用vuex
  store: store,
  render: h => h(App),
});
</script>

<!-- Vuex 示例（store -> index.js ） -->
<script>
  import Vue from 'vue';
  import Vuex from 'vuex';
  import VuexPersistence from 'vuex-persist'
  
  Vue.use(Vuex);  // Vuex 注册成为 Vue 的插件
  
  const vuexLocal = new VuexPersistence({  // 配置 vuex-persist
    storage: window.localStorage
  })
  
  const vuexSession = new VuexPersistence({  // 配置 vuex-persist
    storage: window.sessionStorage
  })

  const store = new Vuex.Store({  // 通过构造函数来创建Vuex的Store(仓库)
    state:{  // 状态,在各个组件中共享的数据
      storage: ''
    },
    mutations:{  // 用于操作 state 中的数据
      type(state[,payload]){
        // state 代表是当前store内的状态,会自动注入到 mutations 中
        // payload，称为载荷，是用户调用 mutaions 时传递的额外参数
      }
      this.$store.commit('type'[,payload])  // 提交 Mututations
    },
    actions:{  // 用于发送异步请求
      type(context[,payload]){
        // context参数代表是当前store内的state、getters、mutations等
        // 该参数将自动注入到actions的内部
      }
      this.$store.dispatch('type'[,payload])  // 分发 actions
    },
    getters:{
      type(state){}  // 可以被认为是 store 的计算属性，其返回值会缓存起来，只有依赖值发生变化时，才会重新计算
    }
    plugins: [vuexLocal.plugin, vuexSession.plugin]  // 配置 vuex-persist
  })
  export default store;
</script>

<!-- 其它页面组件访问 Vuex state 中的数据 -->
<script>
import { mapState, mapGetters, mapMutations } from 'vuex'
export default {
  computed: {
    ...mapState(["变量名"]),  // mapState用来提取数据
    ...mapGetters(["函数名"]),
  }
  methods: {
    ...mapMutations(["函数名"]),  // mapMutations用来存储数据
  }
}
</script>
```

# vuex-persist

```js
# 安装
npm install --save vuex-persist

# store -> user.js
import VuexPersistence from 'vuex-persist'
const vuexSession = new VuexPersistence({ storage: window.sessionStorage })
const store = new Vuex.Store({
  state: {},
  mutations: {},
  plugins: [ vuexSession.plugin ]
})
```

# axios

```js
# 安装
npm install --save axios

# src -> main.js
import axios from 'axios'
axios.defaults.baseURL='/api'
Vue.prototype.$axios=axios

# vue.config.js
module.exports={                                           // vue.config.js
  proxy: {
    '/api': {                                              // 服务器端地址
      target:'http://192.168.112.252:60060',               // 服务器端接口地址
      changeOrigin: true,                                  // 开启跨域
      pathRewrite: { '^/api': '' }                         // 把请求中的 /api 替换为空字符
    }
  }
}

# src -> utils -> request.js
let request={}
request.get=function (url, params={}){                     // get/delete/patch 发送请求
  return new Promise((resolve, reject)=>{
      axios.get(url, { params })                           // {params:{"username": "Young","password": 123456}}
      .then(response=>{ resolve(response) })
      .catch(error=>{ reject(error) })
  })
}
request.post=function (url, data={}){                      // post/put 发送请求
  return new Promise((resolve, reject)=>{
    axios.post(url, data)                                  // data={"username": "Young","password": 123456}
    .then(response=>{ resolve(response) })
    .catch(error=>{ reject(error) })
  })
}
export default request;

# src -> api -> user.js
import request from '@/utils/request'
export const loginAPI=(data)=>request.post(url.userUrl+'/api/ua/user/login', data)

# 发送请求
try{
  const result = await axios.get(url)
  console.log(result)
}catch(error){
  console.log(error)
}
```

# QS

```js
# 安装
npm istall --save qs

# src -> main.js
import qs from 'qs'
Vue.prototype.qs = qs

# 方法
qs.stringify()  > 将对象转换成请求字符串
qs.parse()      > 将请求字符串转换成对象
```

# 指令

```html
<html v-text="'用户名：'+name"/>             > 解决网速慢，用户可能短暂看到 {{}} 语法
<html v-html="变量名"/>                      > 绑定 HTML 内容
<html v-show="true/false"/>                 > 切换元素的 display 属性
<html v-if/v-else-if/v-else="判断条件"/>     > 根据条件保留DOM元素
<html v-for="(v, i) of Array" :key="k"/>    > 循环创建元素：v-for 的优先级比 v-if 高
<html v-on:click="fun($event, ...)"/>       > 事件绑定（函数传参）
<html v-on:click="fun" data-name="value"/>  > 事件绑定（自定义属性传参）
<html v-bind:属性名="uname"/>                > 绑定属性值的变量或 JS 表达式
<html v-model="变量名"/>                     > 双向绑定（限制元素：input/select/textarea）
<html v-pre/>                               > 保护元素内容中的 {{}} 不被 Vue 编译
<html v-once/>                              > 首次加载时修改元素内容，此元素不会加入到虚拟 DOM 树
<html v-lazy/>                              > 懒加载
```

# 自定义指令

```js
Vue.directive("focus",{      // 添加自定义 focus 指令
  inserted(domElem){         // 插入自定义指令，调用时会执行此函数
    domElem.focus()          // 当带有这个指令的元素被插入到页面后自动执行
  }
})
```

# 自定义过滤器

```js
Vue.filter("dataFilter",(val, n=0)=>{       // oldVal：为固定形参，等于变量值
  let data=String(val);
    for(let i=3;i<data.length-n;i++){
      if(i%3==0){
        data=data.slice(0,data.length-i-n)+','+data.slice(data.length-i-n);
        n++;
      }
    }
    return data;                          // 判断原始数据，返回新值
});
export default {
  data(){
    dateVal: 1000
  }
}
```

# 懒加载

```js
# 根目录 -> vue.config.js
module.exports={
  chainWebpack:config=>{               // 取消异步懒加载执行，实现纯粹的懒加载
    config.plugins.delete("prefetch")  // 删除 index.html 中 prefetch 属性的 link，取消异步下载不使用的页面组件文件
  }
}

# 根目录 -> index.js
{
  path: "/index/:id",                                                            // 页面跳转路径
  name: "Index",
  component: () => import(/* webpackChunkName: "index" */ "../views/Index.vue")  // 异步懒加载页面组件对象
}
```

# 拦截器

```js
// 添加请求拦截器
axios.interceptors.request.use(function (config) {  //发送请求之前做一些事情
  return config;
}, function (error) {  //捕捉错，对错误进行处理
  return Promise.reject(error);
});

// 添加响应拦截器
axios.interceptors.response.use(function (response) {  //对响应结果做一些处理
  /*  
  if(data.code===200){
　  return data.data
　}else{
　  return response　
　}
　*/
  return response;
}, function (error) {
  return Promise.reject(error);
});
```

# 防抖

```vue
<template>
  <div class="app">
    <input type="text" v-model="keyword" @keywup.13="search">
    <button @click="search">百度一下</button>
  </div>
</template>
<script>
export default {
  data(){
    return {
      keyword: "",                 // 用户输入的值
      timer: null                  // 定时器状态
    }
  },
  methods:{
    search(){
      if(this.timer!=null){        // 用户在 1s 内再次触发事件函数则清除上一个定时器
        clearTimeout(this.timer);
      }
      this.tiemr=setTimeout(()=>{  // 定义新的定时器
        if(this.keyword.trim()){   // 去除值左右的空格，并不能为空
          console.log(`查找${this.keyword.trim()}相关的内容...`);
        }
      },1000)
    }
  }
}
</script>
```

# 路由

```vue
# 路由传参
<!-- router -> index.js -->
import Vue from 'vue'
import VueRouter from 'vue-router'
Vue.use(VueRouter)
const routes = [
  {
    path: "/details/:uid",
    component: Details,
    props: true
  }
]

<!-- views -> details.vue -->
<template>
  <div class="details">
    <h1>显示{{uid}}号商品</h1>
  </div>
</template>
<script>
export default {
  props: ["uid"]
}
</script>

# 父组件向子组件传参
<!-- 父组件 -->
<template>
  <div class="login">
    <header :dataList="dataList">子组件</header>  <!-- 父组件向子组件传递数据 dataList -->
  </div>
</template>
<script>
import Header from "@/components/Header"          // 导入组件
export default {
  name: "Header",                                 // 导入的组件命名
  components: { Header },                         // 把导入的组件转为子组件
  data(){
    return {
      dataList: {                                 // 定义数据
        "username": "Young",
        "password": 123456
      }
    }
  }
}
</script>

<!-- 子组件 -->
<template>
  <div class="header">
    <h1>{{"账号:"+dataList.username}}</h1>         <!-- 父组件向子组件传递数据 dataList -->
    <h1>{{"密码:"+dataList.username}}</h1>
  </div>
</template>
<script>
export default {
  props: ["dataList"]  // 子组件接收父组件传来的参数
}
</script>

# 路由跳转
<router-link :to="'/details/'+uid"></router-link>  <!-- HTML 路由跳转 -->
<script>
  this.$router.go(-1/0/1)                          // JS 后退历史记录/更新当前页面/前进历史记录
  this.$router.push("/details/"+uid)               // JS 路由跳转
  this.$route.query.uid                            // JS 接收 get 参数
  this.$route.params.uid                           // JS 接收 post 参数
</script>

# 全局路由守卫
<script>
  router.beforeEach((to, from, next) => {})     // 全局前置守卫(from:路由发起信息对象 / to:路由跳转信息对象 / next():放行函数)
  router.beforeResolve((to, from, next) => {})  // 全局后置守卫
  router.afterEach((to, from) => {})            // 全局解析钩子
</script>

# 组件内守卫
<script>
  beforeRouteEnter((to, from, next) => {})      // 当前路由渲染该组件时调用
  beforeRouteUpdate((to, from, next) => {})     // 当前路由改变时调用
  beforeRouteLeave((to, from, next) => {})      // 当前路由离开时调用
</script>

# 路由懒加载
const Home = ()=> import('../pages/Home/Home.vue')  // 动态引入，提高首屏渲染效率

# 性能优化
  1. 路由懒加载
  2. 打包时可以通过关闭 Map 映射文件来性能优化
  3. keep-alive 缓存组件

# 滚动插件
better-scroll
```

# I18n

```vue
# 安装
npm install vue-i18n

# main.js
import VueI18n from 'vue-i18n'

const i18n = new VueI18n({
  locale: 'en',  > 语言标识
  messages: {
		cn: { ... cn },
		en: { ... en }
	}
})
Vue.use(VueI18n)

new Vue({
  router,
  store,
  i18n,          > 挂载
  render: h => h(App)
}).$mount('#app')
```

# 具名作用域插槽

```vue
# 父组件
<父组件>
  <template #插槽名="{item}">
    <div>
      {{ item }}  // 父组件的scope.prop 等于 子组件的item
    </div>
  </template>
</父组件>

# 子组件
<子组件>
  <slot :name="插槽名" :item="item"></slot>
</子组件>

```

