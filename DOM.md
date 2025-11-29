# 查找元素

```js
document.getElementById("id")                 > 查找对应 id 的一个元素
document.getElementsByTagName("div")          > 查找对应标签名的多个元素
document.getElementsByClassName("className")  > 查找对应类名的多个元素
document.getElementsByName("name")            > 查找对应 name 的多个元素
element.querySelectorAll("选择器")             > 查找对应选择器的所有子元素对象
element.querySelector("选择器")                > 查找对应选择器的一个子元素对象
element.parentElement                         > 查找元素对象的父元素
element.children                              > 查找元素对象的所有子元素
element.firstElementChild                     > 查找元素对象的第一个子元素
element.lastElementChild                      > 查找元素对象的最后一个子元素
element.previousElementSibling                > 查找元素对象的上一个兄弟元素
element.nextElementSibling                    > 查找元素对象的下一个兄弟元素
```

# 修改标签内容

```js
element.innerHTML    > 获取标签内容
element.textContent  > 获取文本内容
element.value        > 获取表单内容
```

# 操作属性

```js
element.getAttribute("属性名")          > 获取属性的值
element.setAttribute("属性名", "新值")  > 修改属性的值
element.removeAttribute("属性名")       > 移除此属性
element.hasAttribute("属性名")          > 判断是否包含此属性
element.style.css属性名                 > 获取内联样式属性值：属性名必须改为驼峰命名
element.style.css属性名="css值"         > 修改内联样式属性值：属性名必须改为驼峰命名
element.className                      > 获取 class 属性值
element.className="值"                 > 修改 class 属性值
```

# 自定义属性

```js
<input type="text" data-自定义属性名="值">   > 创建自定义属性
element.dataset.自定义属性名                 > 获取自定义属性名
element.dataset.自定义属性名="值"            > 修改自定义属性值
```

# 添加/删除/替换元素

```js
let divElement=document.createElement("div")       > 创建新的空元素
let divElements=document.createDocumentFragment()  > 创建文档片段对象
element.replaceChild(divElement, 新元素对象)        > 替换父元素中的一个旧元素
element.insertBefore(divElement, 新元素对象)        > 插入一个新元素在父元素开头
element.appendChild(divElement)                    > 插入一个新元素在父元素结尾
```

# form 元素

```js
let formElements=document.forms[index];                  > 获取 <form> 元素
let inputElements=formElements.elements[index/name/id];  > 获取 <form> 内的表单元素
```

# 跳转新链接窗口/url 历史记录栈

```js
location.reload()                     > 刷新当前页面
location.href="url"                   > 当前窗口打开新链接，支持后退
location.replace("url")               > 当前窗口打开新链接，禁止后退
<a href="url" target="_self">         > 当前窗口打开新链接，支持后退
window.open("url", "_self")           > 当前窗口打开新链接，支持后退
<a href="url" target="自定义窗口名">   > 新窗口打开新链接，仅打开一个
window.open("url", "自定义窗口名")     > 新窗口打开新链接，仅打开一个
<a href="url" target="_blank">        > 新窗口打开新链接，可打开多个
window.open("url", "_blank")          > 新窗口打开新链接，可打开多个
history.go(1)                         > 前进历史页面
history.go(0)                         > 刷新历史页面
history.go(-1)                        > 后退历史页面
```

# url 信息

```js
location.href            > 获取 url 路径
location.protocol        > 获取 url 协议
location.host            > 获取 url 主机名+端口号
location.hostname        > 获取 url 主机名
location.port            > 获取 url 端口号
location.pathname        > 获取 url 相对路径
location.search          > 获取 url ? 之后的查询字符串
location.hash            > 获取 url # 之后的锚点地址
```

# 游览器配置信息

```js
navigator.userAgent                       > 获得浏览器名称、内核、版本号相关信息
navigator.plugins                         > 获得浏览器中安装的插件信息列表
navigator.plugins["插件全名"]!==undefined  > 判断是否安装某个插件
```
