# macOS 配置

```shell
# 允许任何来源
sudo spctl --global-disable

# 删除系统 ABC 输入法
sudo open ~/Library/Preferences  // 终端输入
com.apple.HIToolbox.plist       // plist 编辑器打开该文件
KeyboardLayout Name String ABC  // 删除 com.apple.HIToolbox.plist 文件中的这一行

# 开启/关闭 SIP
csrutil enable   // 开启
csrutil disable  // 关闭
```

# Windos 配置

```shell
# 优化右键菜单栏
reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
任务栏右键-点击【任务管理器】，在任务管理器中-应用-找到Windows资源管理器-右键后，点击：重新启动

# 关闭软件开启窗口
控制面板 -> 用户账户 -> 更改用户账户控制设置

# 关闭提高指针精确度
控制面板 -> 鼠标 -> 指针选项
```

# 开发配置

```shell
npm install -g cnpm --registry=https://registry.npm.taobao.org  > 安装 cnpm
npm install                                                     > 创建 node_modules
npm run start                                                   > 启动项目命令

# 安装 Python
官网 2.7.7 版本

# 安装 NodeJS
官网 14.21.3 版本

# 安装 Sass 注：需要和 NodeJS 版本匹配，否则抛错
npm install node-sass@4.14.1 --save-dev
npm install sass-loader@7.3.1 --save-dev

# 安装 TypeScript
npm install -g typescript

# 安装 postcss-px2rem插件
npm i postcss-px2rem --save -dev

# 安装 pdf 插件
npm install --save vue-pdf
```

# 静态服务器

```shell
npm install anywhere -g  > 安装静态服务器
anywhere                > 运行项目
```

# Shell

```shell
# 部署项目
1. 输入主机服务器地址
  54.79.227.246                  # 246环境
  13.210.179.247                 # 247环境
  54.66.161.26                   # staging环境
2. 输入用户名和密码
  用户名：ubuntu
  密码：密钥文件
3. 切换到服务器项目目录
  cd prod/zerocap-portal-admin/  # admin 端
  cd prod/zerocap-front-end/     # portal 端
  cd prod/zerocap-dma-ems/       # ems 端
4. 拉取最新代码
  git pull origin 分支名
5. 打包代码到服务器
  npm run build
  
# vim 修改服务器文件内容
vim 文件名  # 进入对应文件名的 vim 模式
i          # 进入光标模式
Esc        # 退出光标模式
:wq        # 强制保存退出

# 图片存放地址
https://img.defi.wiki/    # 测试环境
https://img.zerocap.com/  # 生产环境
```

