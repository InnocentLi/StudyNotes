# **Vue 语法初探**

## 初探

### 编写 HelloWorld 和 Counter

```js
Vue.createApp({
        data() {
            return {
                content:'hello world2'
            }
        },
        template:
        '<div>{{content}}</div>'
}).mount('#root');
```

此时，一个简单的hello world 就会被打印成功

```js
    Vue.createApp({
        data() {
            return {
                content:1
            }
        },
        mounted(){
            setInterval(()=>{
                this.content += 1 ;
             //相当于   this.$data.content += 1; 
            },100)
        },
        template:
        '<div>{{content}}</div>'
    }).mount('#root');
```

此时每100毫秒会对content+1，此时一个简单的vue的demo小程序就编写成功了。

### 编写字符串反转和内容隐藏小功能

反转

```js
 Vue.createApp({
        data() {
            return {
                content:'hello world'
            }
        },
        methods: {
            handleButtonClick(){
                const newContent = this.content.split('').reverse().join('');
                this.content = newContent;
            }
        },
        template:
        `
        <div>{{content}}</div>
        <button v-on:click="handleButtonClick">反转</button>
        `
    }).mount('#root');
```

隐藏?

```js
Vue.createApp({
        data() {
            return {
                content:'hello world'
            }
        },
        methods: {
            handleButtonClick(){
                const newContent = this.content.split('').reverse().join('');
                this.content = newContent;
            }
        },
        template:
        `
        <div>{{content}}</div>
        <button v-on:click="handleButtonClick">反转</button>
        `
    }).mount('#root');
```

### 编写TodoList 小功能，了解循环和双向绑定

循环测试：

```vue
Vue.createApp({
        data() {
            return {
                list:['hello','world','haha','lala']
            }
        },
        template:`
					<ul>
            <li v-for="item of list">{{item}} test</li>
					</ul>
        `
    }).mount('#root');
```

显示效果 hello world haha lala 每行展示并且输出test

todolist

```vue
Vue.createApp({
        data() {
            return {
								inputValue:"",
                list:[],
            }
        },
				method:{
						handleAddItem(){
						this.list.push(this.inputValue);
						this.inputValue = "";
				}
				}
        template:`
				<div>
          <input v-model="inputValue"/>	
					<button v-on:click="handleAddItem">增加	</button>
					<ul>
            <li v-for="item of list">{{item}} test</li>
					</ul>
        </div>
        `
    }).mount('#root');
```

## 组件概念初探，对 TodoList 进行组件代码拆分



# **Vue 基础语法**

## Vue 中应用和组件的基础概念



## 理解 Vue 中的生命周期函数

## 生命周期函数的深度分析

Vue生命周期总共可以分为8个阶段：创建前后, 载入前后,更新前后,销毁前销毁后，以及一些特殊场景的生命周期

| 生命周期      | 描述                               |
| ------------- | ---------------------------------- |
| beforeCreate  | 组件实例被创建之初                 |
| created       | 组件实例已经完全创建               |
| beforeMount   | 组件挂载之前                       |
| mounted       | 组件挂载到实例上去之后             |
| beforeUpdate  | 组件数据发生变化，更新之前         |
| updated       | 数据数据更新之后                   |
| beforeDestroy | 组件实例销毁之前                   |
| destroyed     | 组件实例销毁之后                   |
| activated     | keep-alive 缓存的组件激活时        |
| deactivated   | keep-alive 缓存的组件停用时调用    |
| errorCaptured | 捕获一个来自子孙组件的错误时被调用 |

![](/Users/innocent/Desktop/学习笔记/生命周期.png)

### 具体分析

**beforeCreate -> created**

- 初始化`vue`实例，进行数据观测

**created**

- 完成数据观测，属性与方法的运算，`watch`、`event`事件回调的配置
- 可调用`methods`中的方法，访问和修改data数据触发响应式渲染`dom`，可通过`computed`和`watch`完成数据计算
- 此时`vm.$el` 并没有被创建

**created -> beforeMount**

- 判断是否存在`el`选项，若不存在则停止编译，直到调用`vm.$mount(el)`才会继续编译
- 优先级：`render` > `template` > `outerHTML`
- `vm.el`获取到的是挂载`DOM`的

**beforeMount**

- 在此阶段可获取到`vm.el`
- 此阶段`vm.el`虽已完成DOM初始化，但并未挂载在`el`选项上

**beforeMount -> mounted**

- 此阶段`vm.el`完成挂载，`vm.$el`生成的`DOM`替换了`el`选项所对应的`DOM`

**mounted**

- `vm.el`已完成`DOM`的挂载与渲染，此刻打印`vm.$el`，发现之前的挂载点及内容已被替换成新的DOM

**beforeUpdate**

- 更新的数据必须是被渲染在模板上的（`el`、`template`、`rende`r之一）
- 此时`view`层还未更新
- 若在`beforeUpdate`中再次修改数据，不会再次触发更新方法

**updated**

- 完成`view`层的更新
- 若在`updated`中再次修改数据，会再次触发更新方法（`beforeUpdate`、`updated`）

**beforeDestroy**

- 实例被销毁前调用，此时实例属性与方法仍可访问

**destroyed**

- 完全销毁一个实例。可清理它与其它实例的连接，解绑它的全部指令及事件监听器
- 并不能清除DOM，仅仅销毁实例

### **使用场景分析**

| 生命周期      | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| beforeCreate  | 执行时组件实例还未创建，通常用于插件开发中执行一些初始化任务 |
| created       | 组件初始化完毕，各种数据可以使用，常用于异步数据获取         |
| beforeMount   | 未执行渲染、更新，dom未创建                                  |
| mounted       | 初始化结束，dom已创建，可用于获取访问数据和dom元素           |
| beforeUpdate  | 更新前，可用于获取更新前各种状态                             |
| updated       | 更新后，所有状态已是最新                                     |
| beforeDestroy | 销毁前，可用于一些定时器或订阅的取消                         |
| destroyed     | 组件已销毁，作用同上                                         |

### 数据请求在created和mouted的区别

`created`是在组件实例一旦创建完成的时候立刻调用，这时候页面`dom`节点并未生成`mounted`是在页面`dom`节点渲染完毕之后就立刻执行的触发时机上`created`是比`mounted`要更早的两者相同点：都能拿到实例对象的属性和方法讨论这个问题本质就是触发的时机，放在`mounted`请求有可能导致页面闪动（页面`dom`结构已经生成），但如果在页面加载前完成则不会出现此情况建议：放在`create`生命周期当中

## 常用模版语法讲解



## 数据，方法，计算属性和侦听器

## 样式绑定语法

## 条件渲染

## 列表循环渲染

## 事件绑定

## 表单中双向绑定指令的使用

# **探索组件的理念**

## 组件的定义及复用性，局部组件和全局组件

## 组件究竟是什么？

### 组件是什么？

组件就是把图形、非图形的各种逻辑均抽象为一个统一的概念（组件）来实现开发的模式，在`Vue`中每一个`.vue`文件都可以视为一个组件

组件的优势

- **降低整个系统的耦合度**，在保持接口不变的情况下，我们可以替换不同的组件快速完成需求，例如输入框，可以替换为日历、时间、范围等组件作具体的实现

- **调试方便**，由于整个系统是通过组件组合起来的，在出现问题的时候，可以用排除法直接移除组件，或者根据报错的组件快速定位问题，之所以能够快速定位，是因为每个组件之间低耦合，职责单一，所以逻辑会比分析整个系统要简单

- 提高可维护性，由于每个组件的职责单一，并且组件在系统中是被复用的，所以对代码进行优化可获得系统的整体升级

### 插件是什么？

插件通常用来为 `Vue` 添加全局功能。插件的功能范围没有严格的限制——一般有下面几种：

- 添加全局方法或者属性。如: `vue-custom-element`
- 添加全局资源：指令/过滤器/过渡等。如 `vue-touch`
- 通过全局混入来添加一些组件选项。如` vue-router`
- 添加 `Vue` 实例方法，通过把它们添加到 `Vue.prototype` 上实现。
- 一个库，提供自己的 `API`，同时提供上面提到的一个或多个功能。如` vue-router`

## 组件间传值及传值校验



## 单向数据流的理解

## Non-Props 属性是什么

## 父子组件间如何通过事件进行通信

## 组件间双向绑定高级内容（选学）

## 使用插槽和具名插槽解决组件内容传递问题

## 作用域插槽

## 动态组件和异步组件

## 基础语法知识点查缺补漏

# **Vue 中的动画**

## 使用 Vue 实现基础的 CSS 过渡与动画效果

## 使用 transition 标签实现单元素组件的过渡和动画效果

## 组件和元素切换动画的实现

## 【讨论题】前端动画是如何实现的？

## 列表动画

## 状态动画

# **Vue 中的高级语法**

## Mixin 混入的基础语法

## 开发实现 Vue 中的自定义指令

自定义指令

```jsx
//自定义指令
const app = Vue.createApp({
  mounted(){
    this.$ref.input.focus();
  },
  template:
  	<div>
      <input ref="input"/>
      <input v-focus/>
  	</div>
  
app.directive('focus',{
		mounted(el){
			this.$ref.input.focus();
			el.focus();			
		}
}
});	

	
```



## Teleport 传送门功能

## 更加底层的 render 函数

## 插件的定义和使用

## 【讨论题】为什么插件机制相对于Mixin是更优雅的代码扩展

## 数据校验插件开发实例

# **Composition API**



## Setup 函数的使用

## ref，reactive 响应式引用的用法和原理

## toRef 以及 context 参数

## 使用 Composition API 开发TodoList

## computed方法生成计算属性

## watch 和 watchEffect 的使用和差异性

## 生命周期函数的新写法

## Provide,Inject,模版 Ref 的用法

## 【讨论题】Composition API 的产生背景是什么

# **Vue 项目开发配套工具讲解**

## VueCLI 的使用和单文件组件

## 使用单文件组件编写 TodoList

## 【讨论题】单文件组件这种语法设计，背后实现的原理是什么

## Vue-Router 路由的理解和使用

## 【讨论题】对前端路由，你有怎样的理解？

## VueX 的语法详解

## CompositionAPI 中如何使用 VueX

## 【讨论题】对前端数据管理框架，你有怎样的理解？

## 使用 axios 发送ajax 请求

