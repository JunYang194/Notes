# 方法

```js
# 属性
const                                         > 常量
var                                           > 全局变量
let                                           > 局部变量
debugger                                      > 断点
continue                                      > 跳过当前循环，继续下次循环
break                                         > 结束循环
return                                        > 返回值
throw                                         > 返回错误值
__dirname                                     > 当前模块的绝对路径
__filename                                    > 当前模块的绝对路径以及文件名称
obj.__proto__                                 > 子对象的原型对象
constructor.prototype                         > 构造函数的原型对象
constructor.prototype.属性名 = ""              > 设置/重写原型对象的共有属性
constructor.prototype.方法名 = function(){}    > 设置/重写原型对象的共有方法
constructor.prototype = obj                   > 设置所有子对象的新原型对象，一定要在创建子对象前修改：自定义继承
window.location.href = url                    > 当前页面打开 url 页面
window.open(url)                              > 新页面打开 url 页面
window.scrollTo(0, 0)                         > $router.push 跳转后页面默认位置
typeof a                                      > 检测a的数据类型
a instanceof b                                > 检测a是否为b的实例
$refs.ref.hide()                              > 关闭 el-dropdown 菜单
$router.back()                                > 实参为空是返回上个页面，为0是刷新，为1是前进

# 方法
Object.assign(this.$data, this.$options.data.call(this));  > 初始化 data
$nextTick()                                   > 渲染完再执行函数
$refs.属性名                                   > 获取对应 ref 属性的DOM
$set(target, key, value)                      > 添加响应式属性
$forceUpdate()                                > 强制渲染
$emit('fun', 参数, ...)                        > 子组件调用父组件的方法
$emit('update:属性名', 值)                     > 子组件更新父组件的属性
JSON.parse()                                  > 字符串转为对象
JSON.stringify()                              > 对象转为字符串
fun.call(obj2, ...)                           > 改变 fun 的 this 指向 obj2，后面可放 fun 的其他参数（返回函数并执行）
fun.apply(obj2, [...])                        > 改变 fun 的 this 指向 obj2，后面数组中可放 fun 的其他参数（返回函数并执行）
fun.bind(obj2, ...)()                         > 改变 fun 的 this 指向 obj2，后面可放 fun 的其他参数（返回函数）
eval()                                        > 执行字符串中的表达式
input.focus()                                 > 文本框自动获取焦点
encodeURIComponent()                          > 字符串转义
$store.state.属性名 
$store.commit()
$store.dispatch()

# 注释规范
/**
 * @author 作者信息 [附属信息：如邮箱、日期]
 * @for 所属类名
 * @method 方法名
 * @description 函数说明
 * @param {参数类型} 参数名 参数说明
 * @return {返回值类型} 返回值说明
 * @throw 异常说明
 * @example 示例代码
 */
```

# Set 容器

```js
new Set([iterable])      > 无序不可重复的多个Value的集合体
Set.prototype.keys()     > 返回键名的遍历器
Set.prototype.values()   > 返回键值的遍历器
Set.prototype.entries()  > 返回键值对的遍历器
```

# Map 容器

```js
new Map(array)          > 无序的key不重复的多个key-value的集合体
Map.prototype.set()     > 返回键名的遍历器
Map.prototype.get()     > 返回键值的遍历器
Map.prototype.delete()  > 返回键值对的遍历器
Map.prototype.has()     > 返回键值对的遍历器
Map.prototype.size()    > 返回键值对的遍历器
```

# Number

```js
Number.prototype.toFixed(count)  > 保留小数点后 n 位

# ES6
Number.prototype.isFinite(n)     > 判断是否是有限大的数
Number.prototype.isNaN(n)        > 判断是否是 NaN
Number.prototype.isInteger(n)    > 判断是否是整数
Number.prototype.parseInt(str)   > 将字符串转换为对应的数值
Number.prototype.parseFloat()    > 强制转化为浮点型，会从数据的开头寻找浮点数，如果找不到则返回 NaN
```

# Math

```js
Math.random()                    > 随机获取 0 ~ 1 之间的数
Math.PI()                        > 圆周率
Math.abs()                       > 取绝对值
Math.max()                       > 取最大值
Math.min()                       > 取最小值
Math.floor()                     > 向上取整
Math.ceil()                      > 向下取整
Math.round()                     > 四舍五入取整
Math.pow(x, y)                   > 计算 x 的 y 次方

# ES6
Math.trunc(n)                    > 直接去除小数部分
```

# Array

```js
Array.isArray(arr)                                > 判断 arr 是否为数组
Array.prototype.length                            > 获取数组长度
Array.prototype.join(str)                         > 合并数组中的所有元素，按分隔符合并为字符串
Array.prototype.concat(arr2, ...)                 > 拼接数组
Array.prototype.unshift(value, ...)               > 添加元素至数组开头：返回数组的长度
Array.prototype.push(value, ...)                  > 添加元素至数组结尾：返回数组的长度
Array.prototype.remove(value/index)               > 删除数组中指定的元素/指定下标的元素
Array.prototype.slice(start, end)                 > 截取数组中元素
Array.prototype.splice(start, count, value, ...)  > 删除数组中元素：value 是删除后替换的元素
Array.prototype.shift()                           > 删除数组中开头的元素：返回删除的元素
Array.prototype.pop()                             > 删除数组中末尾的元素：返回删除的元素
Array.prototype.reverse()                         > 翻转数组中的元素：返回翻转后的数组
Array.prototype.sort((a, b)=>a-b)                 > 排序数组中的元素
Array.prototype.every((value, index, arrs)=>{})   > 遍历数组，所有值为 true 则返回 true；否则返回 false
Array.prototype.some((value, index, arrs)=>{})    > 遍历数组，所有值为 false 则返回 false；否则返回 true
Array.prototype.reduce((sum, item, index, arr)=>{}, initial) > total：第一次是initial/第一个元素值，后续是回调的返回值

# ES5
Array.prototype.indexOf(value)                    > 得到数组中某个数据的第一个下标
Array.prototype.lastIndexOf(value)                > 得到数组中某个数据的最后一个下标
Array.prototype.forEach((item, index)=>{})        > 遍历数组
Array.prototype.map((item, index)=>{})            > 遍历数组，返回新数组
Array.prototype.filter((item, index)=>{})         > 遍历数组，返回过滤后的数组

# ES6
Array.from({length: n}, (value, index)=>{})       > 将对象转成数组，该对象必须要有length属性，对象的属性名必须是数字
Array.of(value1, value2, value3)                  > 将一些列数值转换为数组
Array.prototype.find((value)=>{})                 > 找出第一个满足条件的元素
Array.prototype.findIndex((value)=>{})            > 找出第一个满足条件的元素的下标
Array.prototype.flat()                            > 将多维数组转为一维数组(也称为: 数组扁平化)

# ES7
Array.prototype.includes()                        > 判断一个数组是否包含一个指定的值，包含就返回 true , 否则返回false
```

# Object

```js
Object.prototype.toString.call(data) === '[object Object]'  > 判断数据类型
Object.prototype.hasOwnProperty(key)            > 检测键名是否存在
Object.setPrototypeOf(子对象, 新原型对象)          > 设置一个子对象的新原型对象(自定义继承)
Object.keys(obj)                                > 获取该对象的键，以数组形式返回

# ES5
Object.create(prototype, [descriptors])         > 创建对象并继承
Object.defineProperties(object, [descriptors])  > 为指定对象扩展多个属性

# ES6
Object.is(value1, value2)                       > 比较两个值是否为同一个值
Object.assign(target, obj1, obj2)               > 将其它对象的属性复制到目标对象上

# ES8
Object.values(obj)                              > 获取对象中所有的属性的值 
Object.entries(obj)                             > 把对象转数组
```

# String

```js
String.prototype.charCodeAt()                        > 查看字符的 Unicode 码
String.prototype.charAt(index)                       > 获取指定下标的字符
String.prototype.indexOf(str)                        > 获取首个字符的下标：返回首个字符的下标/-1
String.prototype.lastIndexOf(str)                    > 获取末尾字符的下标，返回末尾字符的下标/-1
String.prototype.slice(start, end)                   > 截取字符：start 开始，end 结束
String.prototype.substr(start, count)                > 截取字符：start 开始，count 长度
String.prototype.split(str)                          > 按分隔符切割为数组
String.prototype.toUpperCase()                       > 所有英文字母转大写
String.prototype.toLowerCase()                       > 所有英文字母转小写
String.prototype.localeCompare(str)                  > 对比字符串
String.prototype.search(/str/gi)                      > 查找对应字符串，返回下标/-1
String.prototype.match(/str/gi)                       > 查找对应字符串，返回数组
String.prototype.replace(/str/gi, ($0, $1, $2, ...))  > 查找并替换字符串，返回替换后的字符串，$0是所有规则，$1规则1，$2规则2等
String.prototype.trim()                              > 去除字符串两边空格

# ES6
String.prototype.includes(str)                       > 判断是否包含指定的字符串
String.prototype.startsWith(str)                     > 判断是否以指定字符串开头
String.prototype.endsWith(str)                       > 判断是否以指定字符串结尾
String.prototype.repeat(count)                       > 重复指定的次数
```

# Date

```js
Date.now()                                  > 获取本地时间的时间戳
Date.prototype.getTime()                    > 获取距离计算机元年的毫秒数
Date.prototype.getFullYear()                > 获取年
Date.prototype.getMonth()                   > 获取月：范围：0 ~ 11
Date.prototype.getDate()                    > 获取日
Date.prototype.getDay()                     > 获取星期：范围：0 ~ 6
Date.prototype.getHours()                   > 获取时
Date.prototype.getMinutes()                 > 获取分
Date.prototype.getSeconds()                 > 获取秒
Date.prototype.getMilliseconds()            > 获取毫秒
Date.prototype.setTime(value)               > 设置距离计算机元年的毫秒数
Date.prototype.setFullYear(value)           > 设置年
Date.prototype.setMonth(value)              > 设置月
Date.prototype.setDate(value)               > 设置日
Date.prototype.setHours(value)              > 设置时
Date.prototype.setMinutes(value)            > 设置分
Date.prototype.setSeconds(value)            > 设置秒
Date.prototype.setMilliseconds(value)       > 设置毫秒
Date.prototype.toLocaleString('zh-CN')      > 日期时间转为本地字符串：0000-00-00 00:00:00
Date.prototype.toLocaleDateString('zh-CN')  > 日期转为本地字符串：0000/00/00
Date.prototype.toLocaleTimeString('zh-CN')  > 时间转为本地字符串：00:00:00
new Date(Date.UTC(year, month, day, hours, minutes, seconds))  > 转换为UTC时间的实例对象
```

# Process

```js
process.arch      > 查看当前 CPU 架构
process.platform  > 查看当前操作系统
process.version   > 查看当前 Nodejs 版本号
process.pid       > 查看当前的进程编号
process.kill(id)  > 结束指定编号的进程
```

# JSX

```js
# 安装
npm install @vue/babel-preset-jsx @vue/babel-helper-vue-jsx-merge-props

# 根目录 -> .babelrc
{
  "plugins": ["transform-runtime", "transform-vue-jsx"]
}
```

## 语法

```jsx
const myId = 'h1'
const myData = '前端JS框架列表'
const arr = [
  {id: 1, name: 'Angular'},
  {id: 1, name: 'React'},
  {id: 1, name: 'Vue'}
]

# 1. 创建虚拟DOM
const VDOM = (
  <div id={myId}
       className="class"
       style={{backgroundColor:'red', ...}}>
    <h1>{myData}</h1>
    <ul>
      {arr.map(item=><li key={item.id}>{item.name}</li>)}
    </ul>
  </div>
)
# 2. 使用React语法将VDOM转为真实DOM并插入页面
ReactDOM.render(VDOM, document.getElementById('id'))
```

# 事件车

```vue
# 建立公共的事件车，主要用来传递信息
Vue.prototype.$bus = new Vue();


this.$bus.$on(自定义函数名, 函数本体)  // 定义事件
this.$bus.$emit(自定义函数名)  		// 调用事件
```

# PubSub

```js
# 安装(消息订阅与发布)
yarn add pubsub-js

import PubSub from 'pubsub-js'

this.token = Pubsub.subscribe('updataState', (msg, stateObj)=>{  // 订阅消息
  this.setState(stateObj)
})
Pubsub.publish('updataState', stateObj)                          // 发布消息
Pubsub.unsubscribe(this.token)                                   // 取消订阅
```

# JavaScript高级

## 面向对象

> 什么是面向对象：面向对象是用一个对象保存属性和方法，然后再按需访问对象中保存的属性和方法
>
> 面向对象三大特点：
>
>   封装：封装是把自己的数据和方法隐藏起来，只让可信的类或者对象操作
>
>   继承：继承是可以让某个类型的对象获得另一个类型的对象的属性的方法
>
>   多态：多态是同一个函数在不同情况下表现出不同的状态（重载、重写）
>
>   （重载：重载是函数名相同，参数不同；在JS中，名字相同的函数会相互覆盖，可以利用arguments参数的长度从而达到重载的目的）
>
>   （重写：重写是覆盖，一般用于子类覆盖父类的方法）

## 作用域/作用域链

> 什么是作用域：作用域是一个变量的可用范围，专门保存变量的对象；包含全局作用域和函数作用域
>
> 什么是作用域链：作用域链是由多级作用域串联形成的链式结构

## 闭包

> 什么是闭包：闭包是一个函数和函数内部能访问到的变量的总和

## this

> 什么是this：this是一个可以自动获得正在调用当前函数 . 前对象的关键词

## 构造函数

> 什么事构造函数：构造函数是用new关键字来调用的函数
>
> （window有11种内置对象：Array/Boolean/Date/Error/Function/global(window 代替)/Math(不能 new)/Number/Object/RegExp/String）

## 原型对象

> 什么事原型对象：每当定义一个对象时，对象中都会包含一些预定义的属性。其中每个函数对象都有一个prototype属性，这个属性指向函数的原型对象

## 原型链

> 什么是原型链：原型链是多级父对象逐级继承，形成的链式结构，保存着一个对象可用的所有属性和方法

# ES5 新特性

> Object.create(prototype, [descriptors])           > 创建对象并继承
>
> Object.defineProperties(object, [descriptors])  > 为指定对象扩展多个属性
>
> Array.prototype.indexOf(value)                     > 得到数组中某个数据的第一个下标
>
> Array.prototype.lastIndexOf(value)                > 得到数组中某个数据的最后一个下标
>
> Array.prototype.forEach((item, index)=>{})     > 遍历数组
>
> Array.prototype.map((item, index)=>{})         > 遍历数组，返回新数组
>
> Array.prototype.filter((item, index)=>{})         > 遍历数组，返回过滤后的数组

# ES6 新特性

> const 与 let（1. 有块作用域  2. 没有变量提升  3. 不会添加到window上  4. 不能重复声明）
>
> 字符串模板
>
> for of
>
> 箭头函数
>
> 拓展运算符（打包/拆包）
>
> 形参默认值
>
> 解构赋值
>
> Rest/剩余参数
>
> 类语法
>
> - class
> - extends
> - constructor
> - super() / super.xxx()
> - static
>
> 模块化语法
>
> - export  
> - export default  value
> - import: 静态导入, 合并一起打包
> - import(): 动态导入, 拆分打包, 用于懒加载      const Home = () => import('./views/Home.vue')
>   import('./views/Home.vue').then((module) => {
>   	// 使用module块
>   	module.default
>   	module.xxx
>   })
>
> 异步语法
> - Promise
> - async 函数
> - await 表达式
>
> 新容器语法
> - Map
> - Set
>
> 代理(Proxy)与反射(Reflect)语法
> - Proxy
> - Reflect
>
> Symbol（给该变量唯一标识）
>
> Iterator（是一种接口机制,为各种不同的数据结构提供统一的访问机制）
>
> Generator（ES6 提供的解决异步编程的方案之一）
>
> Async 函数是 Generator 函数的语法糖
>
> // String 扩展
>
> includes(str)  > 判断是否包含指定的字符串
>
> startsWith(str)  > 判断是否以指定字符串开头
>
> endsWith(str)  > 判断是否以指定字符串结尾
>
> repeat(count)  >重复指定的次数
>
> // Number 扩展
>
> Number.isFinite(n)  > 判断是否是有限大的数
>
> Number.isNaN(n)  > 判断是否是 NaN
>
> Number.isInteger(n)  > 判断是否是整数
>
> Number.parseInt(str)  > 将字符串转换为对应的数值
>
> Number.parseFloat()  > 强制转化为浮点型，会从数据的开头寻找浮点数，如果找不到则返回 NaN
>
> Math.trunc(n)  > 直接去除小数部分
>
> // Array 扩展
>
> Array.from({length: n}, (value, index)=>{})  > 伪数组转真数组
> Array.of(value1, value2, value3)  > 将一些列数值转换为数组
> Array.prototype.find((value)=>{})  > 找出第一个满足条件的元素
> Array.prototype.findIndex((value)=>{})  > 找出第一个满足条件的元素的下标
>
> // Object 扩展
>
> Object.is(value1, value2)  > 比较两个值是否为同一个值
>
> Object.assign(target, obj1, obj2)  > 将其它对象的属性复制到目标对象上
>
> // Set 容器（无序不可重复的多个值的集合体）
>
> Set()
>
> Set(array)
>
> add(value)
>
> delete(value)
>
> has(value)
>
> clear()
>
> size
>
> // Map容器（无序的key不重复的多个key-value的集合体）
>
> Map()
>
> Map(array)
>
> set(key,value) 添加
>
> get(key)
>
> delete(key)
>
> has(key)
>
> clear()
>
> size

# ES7 新特性

> Array.prototype.includes()  > 判断一个数组是否包含一个指定的值，包含就返回 true , 否则返回false

# ES8 新特性

> Object.values(obj)  > 获取对象中所有的属性的值 
> Object.entries(obj)  > 把对象转数组

# ES9 新特性

> Promise.finally()  > 成功失败都会执行