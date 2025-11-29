# 标签

```html
# 块级元素
<hr>                                  > 水平分割线
<div></div>                           > 块级元素
<p></p>                               > 段落
<h1></h1>                             > 标题
<pre><pre>                            > 预格式化（保留标签内所有空格和回车并显示）
<ul>                                  > 无序列表
  <li></li>
</ul>
<ol>                                  > 有序列表
  <li></li>
</ol>
<dl>                                  > 定义列表
  <dt></dt>
  <dd></dd>
</dl>
<fieldset>                            > 控件分组
  <legend>组名</legend>
</fieldset>
<table cellpadding="边框与内容的距离">  > 表格
  <tr rowspan="行合并">
    <td colspan="列合并"></td>
  </tr>
</table>

# 行内元素
<br>                                                 > 换行
<span></span>                                        > 行内元素
<label for="id"></label>                             > 表单关联（for 关联 input 的 id）
<strong></strong>                                    > 加粗
<em></em>                                            > 斜体
<u></u>                                              > 下划线
<del></del>                                          > 删除线
<sup></sup>                                          > 上标
<sub></sub>                                          > 下标
<transition></transition>                            > Vue 专门写动画的标签
<img src="url" alt="图片加载失败时显示的文本">          > 图片
<a href="#锚点名称/url" harget="__self/__blank"></a>  > 超链接
<router-link to="url"></router-link>                 > 路由跳转

# 行内块元素
<input type="text" placeholder="" autofocus>                  > 文本框
<input type="password" placeholder="">                        > 密码框
<input type="hidden" value="">                                > 隐藏域
<input type="file" enctype="multipart/form-data" multiple>    > 文件选择框
<input type="number" step="" max="" min="">                   > 数字框
<input type="radio" name="sex" value="" checked>              > 单选按钮
<input type="checkbox" name="sex" value="" multiple checked>  > 复选按钮
<input type="reset" value="">                                 > 重置按钮
<button onclick="fun()"></button>                             > 提交按钮
<select name="" size="" multiple>                             > 下拉列表
  <option value="" slected></option>
</select>
```

- maxlength：最大输入长度
- minlength：最小输入长度
- autofocus：自动获取焦点
- disabled：只看不改，无法提交
- readonly：只看不改，可以提交
- multiple：多选
- checked：默认选中

# WebStorage

```js
# cookie：存储数据在游览器，前后端都能进行操作
npm install vue-js-cookie             > 安装 cookie
import Cookies from 'js-cookie'       > 导入 cookie

Cookies.set('name','Young')           > 存储
Cookies.get('name')                   > 获取
Cookies.remove('name')                > 删除
Cookies..clear()                      > 删除所有


# localStorage：存储数据只在当前标签页有效
localStorage.setItem('name','Young')  > 存储键名和值
localStorage.getItem('name')          > 获取键名对应的值
localStorage.removeItem('name')       > 清除指定的键名和值
localStorage.clear()                  > 清除所有的键名和值
localStorage.lenght                   > 获取键值对的数量

# sessionStorage：存储数据永远有效
sessionStorage.setItem(key,value)     > 存储键名和值
sessionStorage.getItem(key)           > 获取键名对应的值
sessionStorage.removeItem(key,value)  > 清除指定的键名和值
sessionStorage.clear()                > 清除所有的键名和值
sessionStorage.lenght                 > 获取键值对的数量
```

# 视频

```html
# 简写
<video src="./static/video.mp4">
  视频格式不支持时的提示信息
</video>

# 标准
<video>
  <source src="./static/video.mp4" type="video/mp4"/>
  <source src="./static/video.webm" type="video/webm"/>
  <source src="./static/video.ogg" type="video/ogg"/>
  视频格式不支持时的提示信息
</video>
```

- poster="./static/img/01.jpg"：设置视频海报帧
- preload="none/auto/metadata"：auto/尽可能的下载视频文件 metadata/只加载视频的总时长、宽度、高度等源数据 none/不缓存视频
- controls：是否显示视频播放控件
- autoplay：是否自动播放视频
- muted：是否静音
- loop：是否循环播放

# 音频

```html
# 简写
<audio src="./static/audio/mp3" controls>
  音频格式不支持时的提示信息
</audio>

# 标准
<audio controls>
  <source src="./static/audio.mp3" type="audio/mp3"/>
  <source src="./static/audio.wav" type="audio/wav"/>
  <source src="./static/audio.ogg" type="audio/ogg"/>
  视频格式不支持时的提示信息
</audio>
```

- preload="none/auto/metadata"：auto/尽可能的下载音频文件 metadata/只加载音频的源数据(总时长、宽度、高度等) none/不缓存音频
- controls：是否显示音频播放控件
- autoplay：是否自动播放音频
- muted：是否静音
- loop：是否循环播放

# 媒体命令

```js
# 事件
@loadedmetadata                    > 媒体的源数据（总时长、宽度、高度等）加载完毕后自动触发
@loadedata                         > 媒体的第一帧数据加载完毕后自动触发
@timeupdate                        > 媒体对象的 currentTime 属性发生变化时自动触发（每秒触发 4~66 次）
@play                              > 媒体播放时自动触发
@pause                             > 媒体暂停时自动触发
@ended                             > 媒体播放结束时自动触发

# 方法
element.play()                     > 播放媒体
element.pause()                    > 暂停媒体
element.currentTime                > 获取/设置媒体的当前播放时间：单位/秒
element.volume                     > 获取/设置媒体的音量：0~1
element.playbackRate               > 获取/设置媒体的播放速率
element.paused                     > 获取媒体是否正在暂停
element.ended                      > 获取媒体是否已经播放完毕
element.duration                   > 获取媒体的总时长：单位/秒
element.requestFullscreen()        > W3C 进入全屏
element.exitFullscreen()           > W3C 退出全屏
element.fullscreenElement()        > W3C 获取全屏状态的 Element 对象
element.webkitRequestFullscreen()  > Chrome 进入全屏
element.webkitExitFullscreen()     > Chrome 退出全屏
element.webkitFullscreenElement()  > Chrome 获取全屏状态的 Element 对象
element.MOZRequestFullscreen()     > 火狐进入全屏
element.MOZExitFullscreen()        > 火狐退出全屏
element.MOZFullscreenElement()     > 火狐获取全屏状态的 Element 对象
```

# 地图

```js
<script src="https://api.map.baidu.com/api?密钥"></script>       > 引入地图
let geoElement = window.navigator.geolocation                   > 1.获取 Geolocation 对象
geoElement.getCurrentPosition(                                  > 获取设备的当前位置
  (position)=>{  // 获取位置成功时自动触发
    # 引入地图
    let divElement = document.getElementsByClassName("div")[0]  > 2.获得元素对象
    let longitude = position.coords.longitude                   > 3.获取经度
    let latitude = position.coords.latitude                     > 4.获取纬度
    let map = new BMap.Map(divEle)                              > 5.创建地图对象
    let point = new BMap.Point(longitude, latitude)             > 6.创建坐标对象（经纬度）
    map.centerAndZoom(point, 15)                                > 7.设置地图中心点和展示层级（最高到 19 级）
    # 功能类
    map.enableDragging()                                        > 功能：启用地图拖拽，默认启用
    map.disableDragging()                                       > 功能：禁用地图拖拽
    map.enableScrollWheelZoom()                                 > 功能：启用滚轮放大缩小，默认禁用
    map.disableScrollWheelZoom()                                > 功能：禁用滚轮放大缩小
    map.enableDoubleClickZoom()                                 > 功能：启用双击放大，默认启用
    map.disableDoubleClickZoom()                                > 功能：禁用双击放大
    # NavigationControl 对象
    let navElement = new BMap.NavigationControl()               > 创建 NavigationControl 对象
    map.addControl(navElement)                                  > 控件：地图平移/缩放
    # LocalCity 对象
    let cityElement = new BMap.LocalCity()                      > 创建 LocalCity 对象
    cityElement.get((res)=>{})                                  > 获取本地城市位置
    # Geolocation 对象
    let locationElement = new BMap.Geolocation()                > 创建 Geolocation 对象
    locationElement.getCurrentPosition((res)=>{})               > 获取当前用户的位置
  },
	# 获取位置失败时自动触发
  (err)=>{},
	# 相关配置
  {
    Geolocation.watchPosition((res)=>{},(err)=>{})              > 开启监听：设备地理位置发生变化时自动触发
    Geolocation.clearWatch()                                    > 结束监听
    timeout                                                     > 设备必须在多少时间内返回一个位置，如果超时则返回错误信息（建议：5000 毫秒）
  }
)
let nav = window.navigator.useragent                            > 获取用户浏览器的相关信息
```

# 拖拽元素

```js
# 拖拽属性
<div draggable="true">文本</div>        > 设置鼠标可以直接用拖拽元素

# 拖拽事件
element.ondragstart=funtcion(event){}  > 元素被拖拽开始时自动触发
element.ondrag=funtcion(event){}       > 元素被拖拽过程中自动触发多次
element.ondragenter=funtcion(event){}  > 元素被拖拽进目标区域时自动触发
element.ondragover=funtcion(event){}   > 元素被拖拽进目标区域悬停时自动触发多次
element.ondrop=funtcion(event){}       > 元素被拖拽目标区域内释放自动触发
element.ondragleave=funtcion(event){}  > 元素被拖拽目标区域外释放自动触发
element.ondragend=funtcion(event){}    > 元素被释放时自动触发
event.stopPropagation()                > 防止自动触发后，浏览器自动打开新标签页
event.preventDefault()                 > 防止自动触发后，浏览器把本标签页删除

# DataTransfer 对象
let dataElement=event.dataTransfer     > 获取 DataTransfer 对象
dataElement.setData("name", "Zeek")    > 设置数据：如果数据类型不存在会自动添加到末尾，如果存在则覆盖
dataElement.getData("name")            > 获取设置的数据
dataElement.clearData("name")          > 删除设置的数据

# FileList 对象
let filesElement=dataEle.files         > 获取 FileList 对象：存储 <input type="file"> 数据和拖放的文件数据
filesElement.length                    > 获取查看 FileList 对象一共存储了多少个文件
filesElement.[index]                   > 获取指定下标的文件
filesElement.name                      > 获取 FileList  对象的名称
filesElement.size                      > 获取 FileList  对象的字节数
filesElement.type                      > 获取 FileList  对象的 MIME 类型
filesElement.lastModified              > 获取 FileList  对象最后修改日期的时间戳

# FormData 对象
let formElement=new FormData()         > 获取 FormData 对象
formElement.append("name", "Zeek")     > 添加键值对
formElement.originalname               > 上传文件的原始名称
formElement.filename                   > 文件上传后的名称
formElement.destination                > 文件上传后，存储的目录名称
```

# WebWorker

```vue
# compute.js
<script>
  this.onmessage=funtion(event){                     > 监听主线程发送的消息（event 返回 MessageEvent 对象）
    let data=parseInt(event.data)                    > 返回发送的消息内容
    let sum=0
    for(let n=0;n<data;n++){
      sum+=n
    }
    this.postMessage(sum)                            > 发送消息给主线程
  }
</script>

# .html
<body>
  <div class="app">
    <p>请输入要计算的数字：<input type="text"></p>
    <p><button onclick="compute()">计算</button></p>
    <p id="sum"></p>sa
  </div>
</body>
<script>
  function compute(){
    let value=document.getElementById("number").value
    var workerEle=new Worker("./script/compute.js")  > 创建 Worker 线程对象
    workerEle.postMessage(value)                     > 发送消息给 Worker 线程
    workerEle.onmessage=function(event){
      let sumEle=document.getElementById("sum")
      sumEle.innerText=evemt.data                    > 把接收的结果显示到 <p>
    }
  }
</script>
```

- 什么是 WebWorker：为 JavaScript 创建多线程环境，主线程创建 Worker 线程后，可以将繁琐的计算工作交由 Worker 线程异步完成
- 限制：
-   同源策略：必须保证主线程和 Worker 线程同源
-   DOM 限制：在 Worker 线程中不允许任何 DOM 操作，但可以访问 BOM 对象
-   通信限制：主线程与 Worker 线程不能直接通信，只能通过消息完成
-   文件限制：Worker 线程无法读取本地脚本文件，只能来源于网络
-   脚本限制：Woeker 线程可以使用 XMLHttpRequest 对象发送 AJAX 请求

# SVG

```vue
<body>
  <svg id="svg" version="1.1" xmlns="http://www.w3.org/2000/svg"></svg>                                                         > 默认尺寸：300 * 150
    <line x1="起点x坐标" y1="起点y坐标" x2="终点x坐标" y2="终点y坐标" stroke="描边颜色"></line>  <!-- 绘制线条 -->
    <rect x="起点x坐标" y="起点y坐标" width="100" height="100" stroke="描边颜色" fill="填充颜色" rx="长轴半径" ry="短轴半径"></rect>  > 绘制矩形
    <circle cx="圆心x轴" cy="圆心y轴" r="半径" fill="填充颜色"></circle>                                                           > 绘制圆形
    <ellipse cx="圆心x轴" cy="圆心y轴" rx="水平半径" ry="垂直半径" fill="填充颜色"></ellipse>                                        > 绘制椭圆
  </svg>
</body>

# SVG 绘制示例
<body>
  <svg id="svg" version="1.1" xmlns="http://www.w3.org/2000/svg"></svg>
  <div>
    <button onclick="draw()">绘制圆</button>
  </div>
</body>
<script>
  function draw(){
    let svgEle=document.getElementById("svg")                                     > 获得 svg 对象
    let circlEle=document.createElementNS("http://www.w3.org/2000/svg","circle")  > 在对应的 svg 中创建 circle 对象
    circlEle.setAttribute("cx", 300)                                              > 设置元素圆心x轴的属性值
    circlEle.setAttribute("cy", 100)                                              > 设置元素圆心y轴的属性值
    circlEle.setAttribute("r", 30)                                                > 设置元素圆心半径的属性值
    circlEle.setAttribute("fill", "#f00")
    svgEle.appendChild(circEle)                                                   > 把 circle 对象添加到 svg 对象中
  }
</script>
```

