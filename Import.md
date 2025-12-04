# CSS 导入

```html
<link rel="stylesheet" href="a.css"/>
<style lang="scss" scoped>
@import 'a.scss';
</style>
```

# JS 导入

```html
<script src="a.js"></script>
```

# 导出/导入模块

```js
# CommonJS 模块化（module.exports 和 exports 都是引用对象方式存储到堆内存中）
module.exports = value         > module.exports 暴露（只能暴露一次）
exports.xxx = value            > exports.xxx 暴露
const module = require('url')  > 引入语法

# ES6 模块化（语法像解构，实际不支持对象解构方式）
export value                            > 分别暴露（可以暴露多次）
export {value1, value2}                 > 统一暴露（可以暴露多次）
import {data} from './module'           > 引入 "分别暴露" or "统一暴露"
import {data as data2} from './module'  > 引入 "分别暴露" or "统一暴露" + 重命名
import * as module from './module'      > 引入 "分别暴露" or "统一暴露" + 打包成对象

export default 表达式                    > 默认暴露（只能暴露一次）
import xxx from './module'              > "默认暴露" 用此方式引入
```

