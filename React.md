# React 安装

```react
# 安装
npm install -g yarn              > 安装 yarn
npm install -g create-react-app  > 安装 React
create-react-app 项目名           > 创建 React 项目
yarn start                       > 启动 React 项目
```

# 路由器

```react
yarn add react-router-dom        > 安装路由器

import {BrowserRouter， HashRouter, Redirect, Route, Link, NavLink, Switch, withRouter} from 'react-router-dom'

class Header extends Component{}   > 一般组件
export default withRouter(Header)  > 把一般组件加工成路由组件

ReactDOM.render(
  <BrowserRouter>
    <App/>
  <BrowserRouter/>,
document.getElementById('id'))

<Switch>                                                           > 匹配到对应的路由则停止匹配
  <Route path="/test" component={Test} exact={true} />             > 查找 /test 路由并显示 Test 组件(exact 精准匹配属性)
  <Redirect to="/test"/>                                           > 重定向
</Switch>
<Link to="/test"></Link>                                           > 标签跳转到 /test 路由
<NavLink to="/test" activeClassName="demo" replace={true}></Link>  > 标签跳转到 /test 路由，可指定高亮的 class 样式(replace 跳转后不留当前页面的历史痕迹)
this.props.history.push('/test')                                   > 编程式跳转，保存当前页面历史痕迹
this.props.history.replace('/test')                                > 编程式跳转，不保存当前页面历史痕迹
this.props.history.go(n)                                           > 前进 n 级历史记录
this.props.history.goBack()                                        > 前进下一级历史记录
this.props.history.goForward()                                     > 回退上一级历史记录
        
# 路由传参
<Link to={`/test/${id}/${title}`}></Link>                          > 跳转路由时携带 params 参数
<Route path="/test/:id/:title" component={Test} />                 > 注册路由时声明接收 params 参数
const {id, title} = this.props.match.params                        > 获取传递过来的 params 参数

import qs from 'querystring'
<Link to={`/test?id=${id}&title=${title}`}></Link>                 > 跳转路由时携带 search 参数
<Route path="/test" component={Test} />                            > 注册路由时，如果携带 search 参数，无需声明接收
const {id, title} = qs.parse(this.props.location.search.slice(1))  > 获取传递过来的请求字符串 search 参数，并转换为对象
        
<Link to={{pathname:'/test', state: {id, title}}}></Link>          > 跳转路由时携带 state 参数
<Route path="/test" component={Test} />                            > 注册路由时，如果携带 state 参数，无需声明接收
const {id, title} = this.props.location.state                      > 获取传递过来的 state 参数
```

# nanoid

```shell
# 安装
yarn add nanoid

# 使用
import {nanoid} from 'nanoid'

nanoid()
```

# axios

```react
# 安装
yarn add axios
```

# 属性/方法

```react
setState()                                                      // 更新状态
forceUpdate()                                                   // 强制更新(不需要更新状态)
ReactDOM.unmountComponentAtNode(document.getElementById('id'))  // 销毁组件
```

# 类式组件

```react
import React, {Component} from 'react'
import './index.css'

// 1. 定义组件
export default class MyComponent extends React.Component{
  // 构造器
  constructor(props){
    super(props)
  }

  // 限制props类型
  static propTypes = {
    name: PropTypes.string.isRequired  // isRequired必须的
  }

  // 设置props默认值
  static defaultProps = {
    name: '中国'
  }
  
  // 使用createRef，创建一个存储节点的容器
  container = React.createRef()
  
  // 设置state属性
  state = {name: '类式组件'}
    
  // 函数
  demo = ()=>{}

  // 生命周期
  static getDerivedStateFromProps(props, state){}      // 几乎不用
  componentDidMount(){}                                // 挂载后
  shouldComponentUpdate(){return ture/false}           // 更新阀门
  getSnapshotBeforeUpdate(){return value}              // 更新前（返回的值会传到preBefore参数）
  componentDidUpdate(preProps, preState, preBefore){}  // 更新后
  componentWillUnmount(){}                             // 销毁
  render(){                                            // 初次渲染+更新
    const {name} = this.props
    return <h1 ref={this.container} onClick={this.demo}>{name}</h1>
  }
}

// 以下代码在 App 组件中渲染即可
const props = {name: '类式组件'}

// 2. 渲染组件到页面
ReactDOM.render(<MyComponent {...props}/>, document.getElementById('root'))
```

# React-Redux

```react
# 安装
yarn add react-redux
yarn add redux-devtools-extension  // 安装 Redux 开发者工具的插件

# index.js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'
import {Provider} from 'react-redux'
import store from './redux/store'
ReactDOM.render(
  <Provider store={
    <App/>
  </Provider>,
document.getElementById('root'))

# App.jsx
import React, { Component } from 'react'
import Count from './containers/Count'
export default class App extends Component {
  render() {
	return (
	  <div>	
	    <Count/>
	  </div>
	)
  }
}

# redux-constant.js  // 常量模块
export const INCREMENT = 'increment'
export const DECREMENT = 'decrement'

# redux-action.js
import {INCREMENT,DECREMENT} from './constant'
export const createIncrementAction = number => ({type:INCREMENT, data:number})
export const createDecrementAction = number => ({type:DECREMENT, data:number})

# redux-reducer.js
import {INCREMENT,DECREMENT} from './constant'
export default function countReducer(preState=0, action){
  const {type,data} = action
  switch (type) {
	case INCREMENT:
	  return preState + data
	case DECREMENT:
	  return preState - data
	default:
	  return preState
  }
}
        
# redux-store.js
import {createStore} from 'redux'
import reducer from './reducer'
export default createStore(reducer)

# containers-Count  容器组件
import React, { Component } from 'react'
import {connect} from 'react-redux'
import {createIncrementAction} from '../../redux/action'
class Count extends Component {  // UI组件
  increment = () => {
    const {value} = this.checkNumber
    this.props.jia(value*1)
  }
  render() {
	// console.log('Count的UI组件收到的props是',this.props);
	return (
	  <div>
		<h2>当前求和为：{this.props.sum}</h2>
		<select ref={c => this.checkNumber = c}>
		  <option value="1">1</option>
		  <option value="2">2</option>
		  <option value="3">3</option>
		</select>&nbsp;
		<button onClick={this.increment}>+</button>
	  </div>
	)
  }
}
export default connect(  // 容器组件
  state => ({sum: state}),      > 映射状态
  {jia: createIncrementAction}  > 映射操作状态的方法
)(Count)
```

