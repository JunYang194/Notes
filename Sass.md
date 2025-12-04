# 配置

```js
# build -> webpack.base.conf.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.sass$/,
        loaders: ['style','css','scss']
      }
    ]
  }
}
```

# 转换

```shell
sass style.scss:style.css --style expanded            > 转换文件
sass --watch style.scss:style.css                     > 监听文件
sass --watch src/sass:src/css                         > 监听目录
```

# 命令

```css
$变量: 0px;                      > 声明变量
@extend .a;                     > 继承 .a{} 选择器的共有样式
@mixin fun(){}                  > 封装混合器
@include fun()                  > 调用混合器
@function fun($a){@return $a;}  > 封装自定义函数
width: fun(100)+px;             > 调用自定义函数
@if(){}                         > 指令
@else if(){}
@else(){}
content: "#{}";                 > 插值运算
width: round(4.2px);            > 四舍五入
width: ceil(4.1px);             > 向上取整
width: floor(-3.5px);           > 向下取整
width: min($v1, $v2, ...);      > 取最小值
width: max($v1, $v2, ...);      > 取最大值
width: random();                > 随机数
content: unquote("abc");        > 去除双引号
content: quote("abc");          > 添加双引号
```

