# 安装

```shell
# 安装 Webpack
npm i --save-dev css-loader
npm i --save-dev file-loader
```

# 打包

1. packge.json

```json
{
  "scripts": {
    "build": "node ./node_modules/webpack/bin/webpack.js",  > 生成打包命令
    "start": "node ./main.js"
  },
}
```

2. webpack.config.js

```js
module.exports = {                                      > Webpack 运行时自动读取的配置文件
  mode: "development（开发模式）/production（产品模式）",  > 1.打包模式
  entry: "./public/src/js/index.js",                    > 2.打包入口
  output: {                                             > 3. 打包结果的输出文件
    path: __dirname + "/public/build",                  > 打包到此路径
    filename: "app.js",                                 > 打包生成的文件名
  },
  module: {                                             > 4. 第三方加载器
    rules: [
      {
        test: /\.css$/,                                 > 打包所有 .css 文件
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.(png|jpg|gif)/,                        > 打包所有 .png|.jpg|.gif 文件
        use: ["url-loader"],
      },
      ...                                               > 打包其它文件需要持续添加对象
    ],
  },
  plugins: [                                            > 5. 打包扩展插件
    ...
  ],
};
```

3. src -> js -> index.js

```js
import getCompanyName from "./util.js";  > 导入其它 JS 模块
import "../css/index.css";               > 导入其它 CSS 模块：CSS 文件无需导出，也无需为导入的文件取变量名，直接导入即可
import "../css/base.css";
import pic20 from "../img/20.jpg";       > 导入其它图片模块
import pic40 from "../img/40.jpg";

function createDiv() {
  var div = document.createElement("div");
  div.classList.add("box");
  div.innerHTML = "版权所有：" + getCompanyName();
  let img20 = new Image();               > 在 <div> 中添加两个图片元素
  let img40 = new Image();
  img20.src = pic20;
  img40.src = pic40;
  div.appendChild(img20);
  div.appendChild(img40);
  return div;
}
document.body.appendChild(createDiv());
```

4. packge.json

```shell
npm run build  > 执行打包命令
```

5. public -> index.html

```html
<script src="./build/app.js"></script>  > 让页面渲染已打包完成的 app.js 文件
```

