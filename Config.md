# macOS 配置

```shell
# 允许任何来源
sudo spctl --global-disable

# 删除系统 ABC 输入法
PLIST Editor                                                // App Store 商店下载软件
sudo open ~/Library/Preferences/com.apple.HIToolbox.plist   // 终端输入
AppleEnabledInputSources -> KeyboardLayout Name String ABC  // 删除 com.apple.HIToolbox.plist 文件中的这一行
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

# NVIDIA 控制面板
通过预览调整图像设置：质量
调整桌面尺寸和位置：全屏/GPU
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

