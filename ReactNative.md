# 环境搭建

```shell
1. 安装 Node.js
    "https://nodejs.org/en/"
2. 安装 JDK
	"https://www.oracle.com/java/technologies/downloads/"
3. 安装 Android Studio
	"https://developer.android.google.cn/studio/"
4. 安装 Android SDK (运行 Android Studio)
  	点击 "More Actions" -> "SDK Manager" -> "Android SDK" -> "Android 10.0(Q)" -> 下载 "Android SDK Platform 29" -> "Intel x86 Atom_64 System lmage"
5. 配置 ANDROID_HOME 环境变量
	"高级系统设置" -> "高级" -> "环境变量" -> "系统变量" -> "新建" -> "输入变量名和变量值"
		变量名："ANDROID_HOME"
		变量值："C:\Users\Administrator\AppData\Local\Android\Sdk"
6. 修改系统环境变量 Path
	"高级系统设置" -> "高级" -> "环境变量" -> "系统变量" -> "Path" -> "编辑"
		新建："%ANDROID_HOME%\platform-tools"
		新建："%ANDROID_HOME%\emulator"
		新建："%ANDROID_HOME%\tools"
		新建："%ANDROID_HOME%\tools\bin"
```

# 初始化项目和打包APP到手机

```shell
1. 通过数据线连接到电脑，设置启用 USB 调试
2. 打开手机 "设置" ，进入 "开发者选项" ，开启 "USB安装" 和 "USB调试(安全设置)" 选项
3. 电脑命令行输入 "adb devices" 检测是否连接成功
4. 电脑命令行输入 "npx react-native init 项目名" ，创建/运行 ReactNative 脚手架项目
5. 电脑命令行输入 "npx react-native run-android" ，将APP打包到手机上
```

# ReactNavigation

```react
# 安装依赖
yarn add @react-navigation/native
yarn add @react-navigation/stack
yarn add react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view

# App.js
import React, {Component} from 'react'
import {View} from 'react-native'
import Nav from './src/nav'
export default class App extends Component {
  render() {
    return (
	  <View>
        <Nav/>
      </View>
    )
  }
}

# Nav.js
import React, {Component} from 'react'
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
import Login from './pages/account/login';
const Stack = createStackNavigator();
export default class Nav extends Component {
  render() {
    return (
      <NavigationContainer>
        <Stack.Navigator initialRouteName="Login" headerMode="none">
          <Stack.Screen name="Login" component={Login} />
        </Stack.Navigator>
      </NavigationContainer>
    )
  }
}
```

# MobX

```react
# 安装依赖
yarn add mobx mobx-react @babel/plugin-proposal-decorators

# babel.config.js 添加以下配置
module.exports = {
  presets: ['module:metro-react-native-babel-preset'],
  plugins: [
    ['@babel/plugin-proposal-decorators', { 'legacy': true }]
  ]
}

# mobx-index.js
import {observable, action} from 'mobx'
class RootStore {
  @observable
  name = 'MobX'
    
  @action
  changName(name){
    this.name = name
  }
}

# App.js
import React, {Component} from 'react'
import {View} from 'react-native'
import {Provider} from 'mobx-react'
import RootStore from './mobx'
import Btn from './components/Btn'
export default class App extends Component {
  render() {
    return (
	  <View>
   	    <Provider RootStore={RootStore}>  // 通过 <Provider/> 把 RootStore 数据传递到 props
          <Btn/>    
        </Provider>
      </View>
    )
  }
}

# Btn.js
import React, {Component} from 'react'
import {View, Text} from 'react-native'
import {inject, observer} from 'mobx-react'	
@inject('RootStore')                    // 接收全局数据
@observer                               // 监视数据并渲染
class Index extends Component {
  handleChangName = ()=>{
    this.props.RootStore.changName('修改数据')
  }
  render() {
    return (
	  <View>
   	    <Text onPress={this.handleChangName}>MobX：{this.props.RootStore.name}</Text>
      </View>
    )
  }
}
```

