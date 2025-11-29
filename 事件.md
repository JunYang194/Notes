# 事件

```js
blur            > 失去焦点
change          > 下拉列表选中项改变
click           > 单击
dblclick        > 双击
focus           > 获得焦点
input           > 用户输入时触发
keydown         > 键盘按键按下
keyup.13        > 键盘按键抬起：.13 是回车键
keyup.enter.native  > 回车事件
load            > 加载完成
mousedown       > 鼠标按键按下
mousemove       > 鼠标移动
mouseenter      > 鼠标移入
mouseleave      > 鼠标移出
mouseup         > 鼠标按键抬起
resize          > 窗口大小改变
scroll          > 网页滚动
error           > 捕获错误

element.addEventListener("事件名", 函数名)     > 添加事件
element.removeEventListener("事件名", 函数名)  > 移除事件
```

# 事件修饰符

```js
事件.native     > 将 vue 组件转化为一个普通的 HTML 标签
事件.capture    > 捕获事件冒泡
事件.once       > 定义为一次性事件
事件.prevent    > 阻止事件默认行为
事件.self       > 限制自身才能触发此事件
事件.stop       > 阻止事件冒泡
```

# 事件对象

```js
event.target                      > 激活事件的对象
event.target.nodeName             > 获取事件对象的元素标签名
event.target.id                   > 获取事件对象的元素 id
event.target.className            > 获取事件对象的元素 class
event.target.innerHTML            > 获取事件对象的元素内容
event.target.dataset.自定义属性名   > 获取自定义属性的值
event.srcElement                  > 获取 img 的事件对象
event.keyCode                     > 获取按键
event.screenX/Y                   > 获取鼠标相对于屏幕左上角的 x/y 坐标
event.clientX/Y                   > 获取鼠标相对于文档显示区左上角的 x/y 坐标
event.offsetX/Y                   > 获取鼠标相对于事件所在元素左上角的 x/y 坐标
event.stopPropagation()           > 阻止事件冒泡
event.preventDefault()            > 阻止事件默认行为
```

## 事件车

```
@/util/bus.js
import Vue from 'vue';
export var bus = new Vue();

@/main.js
import { bus } from '@/util/bus';
Vue.prototype.bus = bus;
```

