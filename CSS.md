# 弹性布局

```css
display: flex/inline-flex/block/inline-block/inline/table/table-cell/none;  > 定义当前元素为：块级弹性容器/行块级弹性容器/块级元素/行内块元素/行内元素/表格元素/表格单元格元素/脱离文档流隐藏
flex-flow: row/row-reverse/column/column-reverse wrap/nowrap;    > 定义弹性容器的主轴方向(左右/右左/上下/下上)和所有项目的是否换行
flex: 1;                                                         > 定义当前项目的尺寸：项目原始尺寸+(主轴剩余空间/n)
gap: 20px;                                                       > 定义当前项目的间隔
justify-content: flex-start/center/flex-end/space-between/space-evenly/space-around;  > 定义弹性容器的所有项目的 X 轴方向对齐方式
align-items: flex-start/center/flex-end/stretch;                 > 定义弹性容器的单行项目的 Y 轴方向对齐方式
align-content: flex-start/center/flex-end/stretch;               > 定义弹性容器的多行项目的 Y 轴方向对齐方式
align-self: flex-stat/center/flex-end/stretch;                   > 定义当前项目的 Y 轴方向对齐方式

display: grid;
grid-template-columns: 40% 30% 30%;
grid-template-columns: repeat(2, 1fr);
grid-gap: 30px 10px;                                             > 定义子项目的纵向和横向间隔
grid-column: 1 / -1;
grid-row: 1 / -1;
```

- flex-stat：起点对齐
- center：居中对齐
- flex-end：终点对齐
- space-between：第一个元素紧靠起点，最后一个元素紧靠终点，余下所有元素平均分配间距
- space-evenly：所有元素平均分配间距
- space-around：左右间距相同
- stretch：如果项目在交叉轴方向上没有设置尺寸，让项目在交叉轴方向填满

# 动画

```css
@keyframes name { 0%{} 100%{} }                                            > 创建动画
animation: name duration delay timing-function iteration-count direction;  > 动画简写方式
animation-name: name;                                                      > 调用动画
animation-duration: 1s;                                                    > 定义动画执行时间
animation-delay: 1s;                                                       > 定义动画延迟时间
animation-timing-function: linear/ease/ease-in-out/ease-in/ease-out;       > 定义动画时间曲线函数
animation-iteration-count: n/infinite;                                     > 定义动画执行次数：infinite 无限
animation-direction: normal/reverse/alternate;                             > 定义动画执行顺序：0%-100%/100%-0%/0%-100%-0%-100%
animation-fill-mode: backwards/forwards/both;                              > 定义动画填充方式：填充第一帧/填充最后一帧/填充第一帧和最后一帧
```

- linear：匀速
- ease：慢速-加速-减速-慢速
- ease-in-out：慢速-疯狂加速-疯狂减速-慢速
- ease-in：慢速-一直加速
- ease-out：快速-一直减速

# 过度

```css
transition: property duration timing-function delay;                   > 过渡简写方式
transition-property: all/属性,属性, ...;                                > 定义参与过渡的属性
transition-duration: 1s;                                               > 定义过渡的时长
transition-timing-function: linear/ease/ease-in-out/ease-in/ease-out;  > 定义过渡的时间曲线函数
transition-delay: 1s;                                                  > 定义过渡的延迟时间
```

- linear：匀速
- ease：慢速-加速-减速-慢速
- ease-in-out：慢速-疯狂加速-疯狂减速-慢速
- ease-in：慢速-一直加速
- ease-out：快速-一直减速

# 背景/渐变

```css
background: color image repeat option / size;                           > 背景简写方式
background-color: transparent;                                          > 定义背景颜色
background-image: url('a.png');                                         > 定义背景图片
background-repeat: no-repeat/repeat/repeat-x/repeat-y;                  > 定义背景图片平铺方式
background-position-x/y: 0px;                                           > 定义背景图片定位
background-size: cover;                                                 > 定义背景图片大小
background-image: -前缀-linear-gradient(方向/角度, #000 0%, #000 100%);   > 定义背景线性渐变
background-image: radial-gradient(半径 at X轴 Y轴, #000 0%, #000 100%);  > 定义背景径向渐变
```

- -webkit-：代表 Chrome、Safari 游览器的私有属性
- -moz-：代表 Firefox 游览器的私有属性
- -o-：代表 Opera 游览器的私有属性
- -ms-：代表 IE 游览器的私有属性
- cover：自适应

# 旋转/缩放

```css
transform-origin: x y;                                      > 定义旋转中心点
transform: rotate(deg);                                     > 中心点选旋转
transform: rotate3d(x, y, z, deg);                          > 根据定义的旋转中心点 3D 旋转
transform: translate(x, y) scale(n) rotate(deg) skew(deg);  > 根据定义的旋转中心点 2D 转换：xy轴的偏移/缩放倍数/旋转度数/倾斜度数
transform: scale(n);                                        > 根据定义的旋转中心点缩放：占文档流，JS 获取元素的缩放后宽高
zoom: n;                                                    > 根据左上角缩放：不占文档流，JS 获取元素的缩放前宽高
```

# 文本

```css
text-shadow: 水平偏移距离/垂直偏移距离/扩散程度/颜色;     > 定义文本阴影
text-transform: capitalize                         > 定义文本首字母大写
text-overflow: ellipsis;                           > 定义文本溢出加省略号
text-decoration: overline/underline/line-through;  > 定义文本修饰：上划线/下划线/删除线
text-indent: 0px;                                  > 定义文本首行缩进
text-decoration: none;                             > 清除文本所有线条修饰
text-align: left/center/right/justify;             > 定义文本水平对齐方式：justify 两端对齐
line-height: 0;                                    > 定义文本行高
vertical-align: top/middle/bottom;                 > 定义 input/img/td 元素的文本垂直对齐方式
outline: none;                                     > 清除绘制于元素周围的一条线
word-break: break-word;                            > 允许在单词内换行
white-space: pre-wrap;                             > 字符串允许\n换行符
white-space: pre;                                  > 空白会被浏览器保留
```

# 字体

```css
font: style variant weight size family;                    > 字体简写方式
font-style: italic/normal;                                 > 定义字体斜体/清除斜体
font-variant: small-caps;                                  > 定义字体小型大写字母
font-weight: 100 ~ 1000;                                   > 定义字体加粗
font-size: 0%;                                             > 定义字体大小
font-family: "KaiTi";                                      > 定义字体系列
font-stretch: normal;                                      > 定义字体缩放比例：normal 代表标准
white-space: nowrap;                                       > 定义字体强制一行
word-break: break-all;                                     > 定义字体溢出换行
letter-spacing: 0px;                                       > 定义字体间距
color: rgba(#000, 1);                                      > 定义字体颜色
cursor: default/pointer/no-drop/wait/help/text/crosshair;  > 定义鼠标光标：箭头/小手/禁止/等待加载/帮助/文本输入/十字
outline: 0;                                                > 清除字体轮廓
@font-face {                                               > 导入字体系列：src/assets/font.css
  font-family: "TRENDS";
  src: url("TRENDS.ttf");
  font-weight: normal;
  font-style: normal;
}
```

# 盒子模型/元素阴影

```css
box-sizing: border-box/content-box;               > 定义盒子模型：包含内边距和边框/不包含内边距和边框
box-shadow: h-shadow v-shadow blur spread color;  > 定义元素阴影：水平偏移距离/垂直偏移距离/扩散程度/大小
```

# 边距/边框/圆角

```css
margin: 0px;                           > 定义外边距
padding: 0px;                          > 定义内边距
border: 1px solid/dashed/dotted #000;  > 定义边框：实线/虚线/点
border-radius: 0%;                     > 定义圆角
```

# 溢出

```css
overflow-x/y: visible/hidden/auto/scroll;  > 定义溢出处理方式：溢出显示/溢出不显示/溢出加滚动条/不管是否溢出都加滚动条
word-break: break-all;                     > 溢出换行

# 强制一行，溢出省略号
max-width: 0px;                > 固定宽度
overflow: hidden;              > 溢出隐藏
text-overflow: ellipsis;       > 溢出省略号
white-space: nowrap;           > 强制文本只显示一行

# 强制 n 行，溢出省略号
max-width: 0px;                > 固定宽度
overflow: hidden;              > 溢出隐藏
text-overflow: ellipsis;       > 溢出省略号
display: -webkit-box;          > 以下部分是强制文本只显示 n 行
-webkit-box-orient: vertical;
-webkit-line-clamp: 2;
```

# 显示/隐藏

```css
display: none;               > 定义元素脱离文档流显示/隐藏
visibility: visible/hidden;  > 定义元素不脱离文档流显示/隐藏
opacity: 0/1;                > 定义元素及子元素的透明度
```

# 定位

```css
position: static;    > 默认文档流
position: relative;  > 定义相对定位：默认文档流
position: absolute;  > 定义绝对定位：脱离文档流
position: fixed;     > 定义固定定位：脱离文档流
clear: both;         > 清除浮动
z-index: 0;          > 定义堆叠属性
```

# 表格

```css
caption-side: top/bottom;   > 定义表格标题位置
table-layout: auto/fixed;   > 定义表格自动布局/固定布局
border-collapse: collapse;  > 定义表格边框合并
border-spacing: 0px;        > 定义表格边框边距
grid-column:1 / -1;         > 定义 item 占据一列
```

# 列表

```css
list-style: type/image position;           > 列表简写方式
list-style-type: none/disc/circle/square;  > 定义列表项：清除/实心圆/空心圆/实心方块
list-style-image: url('a.png');            > 定义列表项自定义图片
list-style-position: inside/outside;       > 定义列表项位置：在li中/在ul左内边距中
```

# 居中

```css
display: flex;           > 弹性布局可以居中垂直处理
margin: 0 auto;          > 外边距居中
text-align: center;      > 定义当前元素内所有文本水平对齐
line-height: 0;          > 定义当前文本行高
vertical-align: middle;  > 定义当前 input/img/td 元素的文本垂直对齐方式
```

# 选择器

```css
# 伪类选择器
&:link{}                      > 匹配元素未被访问时的状态
&:visited{}                   > 匹配元素已被访问时的状态
&:hover{}                     > 匹配元素鼠标悬停时的状态
&:focus{}                     > 匹配元素获取焦点时的状态
&:active{}                    > 匹配元素被激活时的状态：左键点住不松手
&:checked{}                   > 匹配元素被选中时的状态：如 radio/checkbox
&:disabled{}                  > 匹配元素被禁用时的状态
&:target{}                    > 匹配元素被锚点激活时的状态
&:first-child{}               > 匹配其父元素下第一个元素
&:last-child{}                > 匹配其父元素下最后一个元素
&:nth-child(){}               > 匹配其父元素下第 n 个元素
&:nth-last-child(){}          > 匹配其父元素下倒数第 n 个元素
&:only-child{}                > 匹配其父元素的唯一子元素
&:not(){}                     > 匹配排除括号内的所有元素
&:empty{}                     > 匹配内部没有任何东西的所有元素：包括换行/空格

# 伪类元素选择器
&::before{ content: "\00a0"; } > 在当前元素下的第一位生成一个假子元素
&::after{ content: "\00a0"; }  > 在当前元素下的最后一位生成一个假子元素
&::placeholder{}               > 匹配包含 placeholder 属性的元素
&::-webkit-scrollbar-track{}   > 匹配滚动条轨道样式
&::-webkit-scrollbar,&::-webkit-scrollbar-thumb{}  > 匹配滚动条滑块样式

# 选择器结构
选择器选择器{}                 > 匹配当前元素其他选择器元素：当前元素其他选择器
选择器+选择器{}                > 匹配兄弟选择器元素：兄弟选择器
选择器,选择器{}                > 匹配多个元素：群组选择器
选择器>选择器{}                > 匹配子元素：子代选择器
选择器 选择器{}                > 匹配后代元素：后代选择器
[属性]...{}                   > 匹配所有元素对应单个/多个属性的元素：元素属性选择器
选择器[属性]...{}              > 匹配选择器元素对应单个/多个属性的元素：元素属性选择器
选择器[属性=值]...{}           > 匹配选择器元素对应单个/多个属性和值相符的元素，可以使用正则表达式模糊查询：元素属性选择器
```

# 响应式布局

```css
# 移动端适配
<meta name="viewport" content="width=device-width, initial-scale=1.0">

# 媒体查询
@media screen and (max-width:1199.99px){ 选择器 }  > 大屏：992px ~ 1199.99px
@media screen and (max-width:991.99px){ 选择器 }   > 中屏：768px ~  991.99px
@media screen and (max-width:767.99px){ 选择器 }   > 小屏：  0px ~  767.99px
```

# 特殊情况

```css
# 高度坍塌：父元素不设置高度，所有子元素浮动
&::after {
  content: "";
  display: block;
  clear: both;
}

# 父子元素外边距重叠：父元素没有上边框，子元素上沿与父元素上沿重叠
&::before {
  content: "";
  display: table;
}

# 设置文本域不能拖动
resize: none;

# 列表换行
.el-select-dropdown__list{
  .el-select-dropdown__item{
    height: auto;
    line-height: 22px;
    padding: 6px 20px;
    span{
      white-space: normal;
    }
  }
}
```
