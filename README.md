## 关于本项目
基于 createPortal 原生实现 KeepAlive 无需任何其他库或者其他插件

利用  react-routerV6 获取到路由信息 实现多页签<br/>

非 antd-pro umijs

## 工程
vite
## 语言
TypeScript

## 技术
- React > 16.8  支持18
- antd > 4
- react-router > 6

### 原理：

#### 核心API
1. react-routerV6 的 useRoutes。
2. React 的  createPortal。
    - 利用 useRoutes 动态匹配路由  存储每次匹配到的信息。
    - 利用 createPortal 将非当前渲染的路由 移动到一个 document.createElement('div') 当中

### 核心代码：
路由 渲染layout组件  在layout里面利用 useRoutes 匹配  路由信息跟vnode

然后传递给 `/components/KeepAlive` 组件

KeepAlive 自己缓存一个数组对象 `Array<{key：路由信息的pathname,value:vnode }>`

然后匹配当前路由的 pathname 渲染对应的 vnode

没匹配的就利用createPortal渲染到DIV里面

[预览](https://codesandbox.io/s/21972)
